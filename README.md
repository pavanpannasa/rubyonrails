# rubyonrails code
#!/usr/bin/ruby


class Screen
  
 def cls
   puts ("\n" * 30)
   puts "\a"
 end
 
 def pause
    STDIN.gets
 end
 
end
 
class Game
    game_counter = 0
    avg_guess = 0
    def display_greeting
        Console_Screen.cls
        print "\t\t Welcome to the Ruby Number Guessing Game!" +
        "\n\n\n\n\n\n\n\n\n\n\n\n\ Press Enter to " + 
        "continue."
 
        Console_Screen.pause
    end
 
    def display_instruction
        Console_Screen.cls
        puts "Instruction:\n\n"
 
        puts "This game randomly generates a number from 1 to 100 and "
        puts "challaenges you to identify it in as few guesses and possible "
    end
 
    def generate_number
        return randomNo = 1 + rand(100)
    end
    
    def play_game
        number = generate_number
        game_counter += 1 
        attempts = 0
        game_number = 0
        loop do
            Console_Screen.cls
            print "\nEnter your guess and press the enter key: "
 
            reply = STDIN.gets
            reply.chop!
            reply = reply.to_i
 
            if reply < 1 or reply > 1000 then
                redo # redo the ciurrent iteration of the loop
                attempts += 1
                game_number +=1
            end
            if attempts > 10 then
               print "Excceded the no. of attempts(10)...GAME_OVER"
               Console_Screen.cls
               break
            guess1 = 0
            guess2 = 0
            guess3 = 0
            if reply == number then
                guess1 += 1 
                print "game_number"
                Console_Screen.cls
                print "You have guessed the number! Press Enter to continue."
                Console_Screen.pause
                break
            elsif reply < number then
                guess2 += 1 
                print "game_number"
                Console_Screen.cls
                print "Your guess is too low! Please enter number from 1 to 1000  Press enter to continue."
                Console_Screen.pause
            elsif reply > number then
                guess3 += 1 
                print "game_number"
                Console_Screen.cls
                print "Your guess is too high! Please enter number from 1 to 1000 Press enter to continue."
                Console_Screen.pause
            end
 
        end
        avg_guess = (guess1 +guess2 + guess3) / 3     
    end
    
    def display_credits
        Console_Screen.cls
        puts "\t\t\Thanks you for playing the number game!!"
        puts "\t\tNo. of games played" +   game_counter
        puts "\t\tAverage no. of games played" +   avg_guess
    end
 
    $noRight = 0
 
    Console_Screen = Screen.new
 
    SQ = Game.new
 
    SQ.display_greeting
 
    answer = ""
 
    loop do
        Console_Screen.cls
 
        print "Are you ready to play the Ruby Number Guessing Game? (y/n): "
 
        answer = STDIN.gets
 
        answer.chop!
 
        break if answer == "y" || answer == "n"
    end
 
    if answer == "n"
 
        Console_Screen.cls
 
        puts "Perhaps anoher time.\n\n"
 
    else
        SQ.display_instruction
 
        loop do
            SQ.play_game
 
            Console_Screen.cls
 
            print "Would you like to play again? (y/n): "
 
            playAgain = STDIN.gets
            playAgain.chop!
 
            break if playAgain == "n"
        end
 
        SQ.display_credits
 
    end
 
end
