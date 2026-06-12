---
title: "need help with script"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by honor01 on 2007-11-01
hey guys, i'm new to the whole ubuntu thing, just transferred to it 2 days ago. but, i love it, especially the freedom.

anyways, i've been spending some time learning how to use the terminal and write scripts. i found a ton of tutorials, so i don't need that. 

i wrote this relatively simple(to you guys) script. i'm just trying to test using the case/if commands. the problem is, it's giving me this "syntax error: unexpected end of file" message. i can't figure out what i did wrong. here's the script:
<hr>


#!/bin/bash

	#case_test - a script to test the case operation

### functions

function question
{
echo -n "Type a digit or a letter.-->"
read character
case $character in
	#check for letters
	[a-z] | [A-Z] ) echo "you typed a letter, that being, $character."
	;;
	#check for digits
	[0-9] ) echo "you typed a number, that being $character."
	;;
	#check for everything else
	* ) echo "what the hell?"
esac
$(try_again)
}

function try_again
{
echo -n "would you like to try again?[y/n]"
	read answer
		if [ "$answer" = "y" "Y" ]
			then
				$(question)
			else
				if [ "$answer" = "n" "N" ]
					then
						echo "goodbye"
						exit 0
				fi
		fi

#### main

cat <<- _EOF_
	$(question)
	_EOF_

---

### Post by damotor on 2007-11-01
You need to close > } the try_again function, otherwise it won't be able to determine where does the function finish and where does the main start

---

### Post by honor01 on 2007-11-02
thankyou. can't believe i missed that. lol.

---

