---
title: "bash script woes"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by Kolfinna on 2007-10-10
Good evening;

I'm creating a bash script and I've run into some problems... 
I'd like it to give a greeting based on what time of day it is (morning, afternoon, or evening), identify the user, and state the date. 
I've got the user part down (I think), but the greeting and date's throwing me for a real loop.

Here's an excerpt of what I've got so far:
[INDENT]#!/bin/bash
while : 
do
DATE= date
HOUR= date +%H%M

clear
if [ $HOUR -lt 2359 ]
then
echo "Good evening, $USER. It is $DATE. Where would you like to go?"
elif [ $HOUR -lt 1800 ]
then
echo "Good afternoon, $USER. It is $DATE. Where would you like to go?"
else
echo "Good morning, $USER. It is $DATE. Where would you like to go?"
fi[/INDENT]

From here it opens into the main menu (adds a couple options if user is root), which has submenus, opens games... should have error statements if the user inputs something wrong. 
I have a lot of work to do yet, but I'm just not getting this bit... I've yet to research the games bit and the like.

Where have I gone wrong with this? Do you all have any other suggestions?

Thanks!

~K

---

### Post by ryanVickers on 2007-10-10
I'll report back ASAP ;)

Edit: the while loop has to have  a"done", like if has to have "fi" ;)

---

### Post by kevdog on 2007-10-10
The conditions you have set up are not mutually exclusive.  You have to set ranges on your if statements with lt gt statements, not just lt statements since some conditions will meet all 3 if statements

---

### Post by Kolfinna on 2007-10-11
ryanVickers--
It is just the excerpt; the whole script is rather long an incomplete. But there is a done at the end. ^_^

kevdog--
....ooh. Layman's terms, please... I'm still pretty new to this.

---

### Post by Kolfinna on 2007-10-11
Okay-- I think I understand what you mean, but I've still got a bit of a problem with it-- it keeps saying "./script: line 8: [: -gt: unary operator expected
./script: line 11: [: -gt: unary operator expected". 
What does this mean?

Also, how can I get it to escape out of a case statement but not the entire script? 

Thanks...

~K

Here's the entire script:

[INDENT]#!/bin/bash
while : 
do
DATE= date
HOUR= date +%H%M

clear
if [ $HOUR -gt 1800 ] && [ $HOUR -lt 0000 ]
then
echo "Good evening, $USER. It is $DATE. Where would you like to go today?"
elif [ $HOUR -gt 1200 ] && [ $HOUR -lt 1800 ]
then
echo "Good afternoon, $USER. It is $DATE. Where would you like to go?"
else
echo "Good morning, $USER. It is $DATE. Where would you like to go?"
fi
echo "[1] File Operations"
echo "[2] User Operations"
echo "[3] Games"
echo "[4] Exit"
echo "[5] Shut Down Computer"

read ans

case $ans in
1 )
echo 
echo "1. File Operations Submenu"
echo "--------------------------"
echo "[1] Create a file"
echo "[2] Change ownership of a file"
echo "[3] Change permissions of a file"
echo "[4] Create a symbolic link"
echo "[5] Modify a text file"
echo "[6] Cancel"
read select
	case $select in 
	1 )
	echo 
	echo "What is the name of the file?"
	read file
	echo "And where would you like to put it?"
	echo "Full file path, please."
	read addy
	touch $file $addy
	;;

	2 )
	echo
	echo "Which file would you like to change ownership of?"
	read cho
	echo "Who do you want to own it?"
	read wn
	chown $cho $wn
	;;

	3 )
	echo
	echo "Which file would you like to change permissions of?"
	read mod
	echo "Great."
	echo "To change permissions use values between 0 and 7."
	echo "The format is rwx-rwx-rwx -- the first for root "
	echo "priveledges, the middle for group settings, and "
	echo "the third for everyone else's settings."
	echo "r is worth 4, w is worth 2, and x is worth 1."
	echo "So-- what permission level would you like to give"
	echo "This file?"
	read ch
	chmod $ch $mod
	;;

	4 )
	echo
	echo "4. Create a Symbolic Link"
	echo "-------------------------"
	echo "A symbolic link is essentially the same thing as"
	echo "a shortcut in Windows. This druid will help you"
	echo "sort out the differences."
	echo "What is the file to be linked? Full address, please."
	read filename
	echo "And the file path and name of the link?"
	echo "(format should be /filepath/linkname)"
	read linkname
	ln -s $linkname $filename
	;;

	5 )
	echo
	echo "Modify a Text File"
	echo "------------------"
	echo "Which file would you like to edit?"
	echo "Full file path, please."
	read iv
	vi $iv
	;;

	6 )
	echo "Are you sure? (y/n)"
	read yn
	if [ $yn = n ]
	then
	echo "Right. Press Enter to continue."
	read
	else
	exit 
	fi
	;;

	esac
;;

2 )
echo "User Operations Menu"
echo "--------------------"
echo "[1] Create a user"
echo "[2] Create a group"
echo "[3] Add a user to a group"
echo "[4] Describe a user"
echo "[5] Cancel"
read user
	case $user in
	1 )
	echo
	echo "What is the new user's name?"
	read usr
	echo "Okay. Would you like to add a password?"
	read y
	if [ $y = y -o Y]
	then
	passwd $usr
	fi 
	echo "Press Enter to continue..."
	read
	;;

	2 )
	echo
	echo "Create a Group"
	echo "--------------"
	echo "What is the name of the group you wish to add?"
	read groupname
	groupadd $groupname
	;;
	
	3 ) 
	echo 
	echo "Add a User to a Group"
	echo "---------------------"
	echo "Which user would you like to add?"
	read us
	echo "All right, and which group would you like to add"
	echo "him or her to?"
	read grp
	;;

	4 )
	echo
	echo "Describe a User"
	echo "---------------"
	echo "Which user would you like to describe?"
	read use
	echo "And how would you describe this user?"
	read desc
	;;

	5 )
	echo "Are you sure? (y/n)"
	read yn
	if [ $yn = n ]
	then
	echo "Right. Press Enter to continue."
	read
	else
	exit 0
	fi
	;;

	esac
;;

3 )
echo
echo "Games Menu"
echo "----------"
echo "Welcome! Time to get your game on..."
echo "[1] TinTin++"
echo "[2] Overkill"
echo "[3] Cancel"
read sel
	case $sel in
	
	1 )
	tt++
	;;

	2 )
	Overkill
	;;

	3 ) 
	echo "Are you sure? (y/n)"
	read yn
	if [ $yn = n ]
	then
	echo "Right. Press Enter to continue."
	read
	else
	exit 0
	fi
	;;
	esac
;;


4 )
echo "Are you sure? (y/n)"
read yn
if [ $yn = n ]
then
echo "Right. Press Enter to continue."
read
else
exit
fi
;;

5 )
echo "Are you sure? (y/n)"
read yep
if [ $yep = n ]
then
echo "Just kidding, weren't you? Press Enter to continue."
read
else
shutdown -h now
;;

esac

done[/INDENT]

---

### Post by kevdog on 2007-10-11
For lines like this:

if [ $HOUR -gt 1800 ] && [ $HOUR -lt 0000 ]

What if you try:
if [ $HOUR -gt 1800 -a $HOUR -lt 0000 ]

or try this 

if [ "$HOUR" -gt 1800 ] && [ "$HOUR" -lt 0 ]    <------ I know what you want to do hear but this statment makes no sense.  How can you be greater than 1800 (numerically) but less than 0?  Wouldn't you want -le 2359??

---

### Post by Kolfinna on 2007-10-11
I wondered about the possibility of 0000 not being a legitimate number for time... Initially, I did have it as 2359 but wanted to test to see if it would count time differently than other numbers.

No worries. ^_^ 

If I do the following:
if [ $HOUR -gt 1800 -a $HOUR -lt 2359 ]
I get a new error:
./script: line 7: [: too many arguments

If I do this:
if [ "$HOUR" -gt 1800 ] && [ "$HOUR" -lt 2359 ]
I get:
./script: line 7: [: : integer expression expected
./script: line 11: [: : integer expression expected

However, I did this:
if [ $HOUR > 1800 ] && [ $HOUR < 2359 ]
And got:
./script: line 7: 1800: Permission denied
./script: line 11: 1200: Permission denied

Finally, I tried this:
if [ $HOUR > 1800 ] && [ $HOUR -lt 2359 ]
And still permission is denied.

Probably because > is being used as a redirect, versus a mathematical symbol. 

I'm doing this part of it in user mode rather than root to ensure that this works entirely for both. 

Thoughts?

Thanks!

~K

---

### Post by Martje_001 on 2007-10-11
> **Kolfinna said:**
> #!/bin/bash
while :

while [ 1 = 1 ]

For if:

```
if [[ $numberl -ge 0 && $number -le 100 ]]; then 
```
see it?

---

### Post by Kolfinna on 2007-10-11
martje:

Tried it, but nothing seems to be working...

I've recently tried this:

[INDENT]hour= date +%H

if [[ "${hour}" -ge "00" && "${hour}" -lt "12" ]]
then
echo "Good morning, $USER. It is:" 
date
elif [[ ${hour} -ge 12 && ${hour} -lt 18 ]]
then
echo "Good afternoon, $USER. It is:" 
date
else
echo "Good evening, $USER. It is:" 
date
fi[/INDENT]

--but it keeps displaying my variable at the very top, and seems not to be utilizing the variable in the actual if statement.

I tried it with quotes and without; I got the same results. 

~K

---

### Post by Martje_001 on 2007-10-12
I'll work at it when I'm home, I think I see the problem!

---

### Post by Old *ix Geek on 2007-10-12
Something jumped out at me straight off:
```
DATE=[color=red]** date**[/color]
HOUR= [color=red]**date +%H%M**[/color]
```You're setting your date and hour variables to TEXT, not times.

Do this at a prompt so you can easily see the results:
```
$ DATE=date
$ echo $DATE
date   <---------- that's the text value you assigned to DATE

$ HOUR=date +%H%M
bash: +%H%M: command not found   <--------- as above, but the space is causing problems here

$ HOUR=date+%H%M  <--------- after removing the space
$ echo $HOUR
date+%H%M  <--------- here's the string you assigned to HOUR
```

Now try these:
```
$ DATE=`date`
$ echo $DATE
Thu Oct 11 23:17:40 PDT 2007  <------ now you're getting the output from the "date" command

$ HOUR=`date +%H%M`
$ echo $HOUR
2318  <-------- as above

```
Until you fix those, the rest of it won't work. :shock:

---

