---
title: "custom terminal welcome"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by chris200x9 on 2007-12-19
Hi, I'm trying to figure out how to get a custom terminal welcome I've been trying with life hackers tips:


[code] 

#------WELCOME MESSAGE---------------------
# customize this first message with a message of your choice.
# this will display the username, date, time, a calendar, the amount of users, and the up time.
clear
echo -e "Lifehacker, the Productivity and Software Guide"
echo -e ""
echo -ne "Today is "; date
echo -e ""; cal ;
echo -ne "Up time:";uptime | awk /'up/
{print $3,$4}'
echo "";

[\code]


and I get them all to show but everytime I exit out of terminal and come back it doesn't stay as my welcome message each time.

---

### Post by Lord_Dicranius on 2007-12-19
In one of the menus there should be a "save profile" option.  Give that a try and see if it saves it.

---

### Post by chris200x9 on 2007-12-19
I put in the code in a thing about my profile and hit execute instead of shell or something now when i hit terminal nothing happens it won't open :confused:

---

### Post by Dr Small on 2007-12-19
Greetings,
Please read this:
[http://php.8ez.com/drsmall/blog/?p=164](http://php.8ez.com/drsmall/blog/?p=164)

Try adding that code to the end of your .bashrc file.

---

### Post by chris200x9 on 2007-12-19
edit it does open and just closes witin like a second

---

### Post by bodhi.zazen on 2007-12-19
> **chris200x9 said:**
> Hi, I'm trying to figure out how to get a custom terminal welcome I've been trying with life hackers tips:


[code] 

#------WELCOME MESSAGE---------------------
# customize this first message with a message of your choice.
# this will display the username, date, time, a calendar, the amount of users, and the up time.
clear
echo -e "Lifehacker, the Productivity and Software Guide"
echo -e ""
echo -ne "Today is "; date
echo -e ""; cal ;
echo -ne "Up time:";uptime | awk /'up/
{print $3,$4}'
echo "";

[\code]


and I get them all to show but everytime I exit out of terminal and come back it doesn't stay as my welcome message each time.

Put that code either in /etc/issue or in ~/.bashrc

---

### Post by chris200x9 on 2007-12-19
is there some way to reset my terminal?

---

### Post by bodhi.zazen on 2007-12-19
Since you were modifying .bashrc I suggest you go to the console (Ctrl-Alt-F1 or F2), log in if needed.

mv .bashrc .bashrc now working

go back to GUI (Ctrl-Alt-F7)

Re-try opening a terminal.

After you modigy .bashrc, open a new terminal b4 you close the new one ....

---

### Post by chris200x9 on 2007-12-19
> **bodhi.zazen said:**
> Since you were modifying .bashrc I suggest you go to the console (Ctrl-Alt-F1 or F2), log in if needed.

mv .bashrc .bashrc now working

go back to GUI (Ctrl-Alt-F7)

Re-try opening a terminal.

After you modigy .bashrc, open a new terminal b4 you close the new one ....

it's the same file?

---

### Post by bodhi.zazen on 2007-12-20
sorry

mv .bashrc .bashrc_not_working

---

### Post by chris200x9 on 2007-12-20
it says .bashrc no file or directory

is there any way to completly reset terminal like I did when I messed up my xorg I did a dpkg-reconfigure -phigh xserver-xorg

---

### Post by azurepalm on 2007-12-20
> **chris200x9 said:**
> is there some way to reset my terminal?

i have it setup so that "<Ctrl><Alt>T" brings up Terminal. It's useful enough to warrant a system wide keyboard shortcut.

so if i want to reset Terminal quickly.:
1. <Ctrl>D    // exit terminal shortcut, default
2. <Ctrl><Alt>T   // open new terminal shortcut, custom

---

