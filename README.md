# hangman
print( '''_                                             
| |                                            
| |__   __ _ _ __   __ _ _ __ ___   __ _ _ __  
| '_ \ / _' | '_ \ / _' | '_ ' _ \ / _' | '_ \ 
| | | | (_| | | | | (_| | | | | | | (_| | | | |
|_| |_|\__,_|_| |_|\__, |_| |_| |_|\__,_|_| |_|
                    __/ |                      
                   |___/''')
stages = [''' 
  +---+ 
  |   | 
  O   | 
 //|\\  | 
 // \\  | 
      | 
=========''', ''' 
  +---+ 
  |   | 
  O   | 
 //|\\  | 
 /    | 
      | 
=========''', ''' 
  +---+ 
  |   | 
  O   | 
 //|\\  | 
      | 
      | 
=========''',''' 
  +---+ 
  |   | 
  O   | 
 //|   | 
      | 
      | 
=========''', ''' 
  +---+ 
  |   | 
  O   | 
  |   | 
      | 
      | 
=========''', ''' 
  +---+ 
  |   | 
  O   | 
      | 
      | 
      | 
=========''',  ''' 
  +---+ 
  |   | 
      | 
      | 
      | 
      | 
=========''' ]
word_list= ["hello", "solar", "sun", "great", "beach", "papers", "honest", "baboon","jaguar", "watermelon", "jackfruit",
            "sunflower", "dhyanalinga", "devi", "smart", "battery", "charger", "picture", "mountain", "waterfall",
            "peacock", "lion", "cute", "phone"]
import random
chosen_word=random.choice(word_list)
print(chosen_word)

#guess_letter=input("Guess a letter\n").lower()
#print(guess_letter)
#for letter in chosen_word:
#    if guess_letter==letter:
 #       print("right")
  #  else:
   #     print("wrong")

word_length=len(chosen_word)
placeholder=""

for letter in range(word_length):
    placeholder+= "_"
print("word to guess: " + placeholder)

game_over=False
correct_letter=[]
lives = 6
while not game_over:
    display = ""
    guess_letter=input("guess a letter: \n").lower()

    for letter in chosen_word:
        if letter==guess_letter:
            display += letter
            correct_letter.append(letter)
        elif letter in correct_letter:
            display += letter
        else:
            display+="_"
    if guess_letter in correct_letter:
        print("you've already guessed this letter dumbass")
    print("guessed letter: " + display)

    if guess_letter not in chosen_word:
        print("wrong guess! loser !! you lost a life :(")

        lives-=1
        print(f"you have lives {lives} /6 lives remaining")
        if lives == 0:
            game_over= True
            print(f"***************** YOU LOSE! it was {chosen_word}*************************")

    if "_" not in display:
        game_over=True
        print("********************* YOU WIN *************************")

    print(stages[lives])

