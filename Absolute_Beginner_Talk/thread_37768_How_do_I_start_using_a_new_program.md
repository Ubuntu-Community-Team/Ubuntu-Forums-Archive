---
title: "How do I start using a new program?"
date: 2005-05-28
forum: Absolute Beginner Talk
---

### Post by acostanza on 2005-05-28
Yes, I'm brand new off the Microsoft Boat!  Installed Ubunto no problem, but I don't know how to use a new program I got with synaptic.  It's a backup utility, backula, and I see that there is an associated backula folder in the etc folder, but I can't find anything installed in the "applications" dropdown menu and clicking on files in the backula folder does nothing.  How do start this new software package, or any for that matter, once installed?

Thanks for helping the new guy! 
-Adam

---

### Post by clb137 on 2005-05-28
[QUOTE=acostanza]Yes, I'm brand new off he Microsoft Boat!  Installed Ubunto no problem, but I don't know how to use a new program I got with synaptic.  It's a backup utility, backula, and I see that there is an associated backula folder in the etc folder, but I can't find anything installed in the "applications" dropdown menu and clicking on files in the backula folder does nothing.  How do start this new software package, or any for that matter, once installed?

Thanks for helping the new guy! 
-Adam[/QUOTE]


Hi there

which window manager are u using Gnome/KDE/XFCE4?  If the program has placed itself in your menu (yet) then you can open a terminal and type ./xxxxxxxx  the file name or look in your menus for 'run program' and type in the program name

good luck

clinton

---

### Post by Error_Msg on 2005-05-28
======
WARNING
======
I'm just as much of a newbie (I hate that word!) as you are, but have you tried open a terminal and typing backula?

E_M

---

### Post by Kyral on 2005-05-28
Well, first off let me say welcome to the Wonderful World of Linux (TM:razz:)

Most programs will insert an entry into the Applications menu, but some won't. In that case open up a terminal and start typing the first few letters of the program, then hit TAB and see what happens (TAB is autocomplete in the terminal :D)

---

### Post by clb137 on 2005-05-28
[QUOTE=Error_Msg]======
WARNING
======
I'm just as much of a newbie (I hate that word!) as you are, but have you tried open a terminal and typing backula?

E_M[/QUOTE]

did you place ./ before typing???

---

### Post by acostanza on 2005-05-28
[QUOTE=clb137]Hi there

which window manager are u using Gnome/KDE/XFCE4?  If the program has placed itself in your menu (yet) then you can open a terminal and type ./xxxxxxxx  the file name or look in your menus for 'run program' and type in the program name

good luck

clinton[/QUOTE]

Window manager is Gnome for the record.  I went back after reading these hints and installed Thunderbird - I love it over Outlook!  Anyway, that went right into the applications menu.  I assume because it is fully supported by Ubuntu.

I tried opening up a terminal window, tuped bac (tab) and it filled in "bacula-" hitting enter gave an error message "command not found" however.  Maybe I should start out more slowly on a more friendly piece of software... 

Thanks for the quick responses!  I'll keep at it!
-Adam

---

### Post by acostanza on 2005-05-28
[QUOTE=Kyral]Well, first off let me say welcome to the Wonderful World of Linux (TM:razz:)

Most programs will insert an entry into the Applications menu, but some won't. In that case open up a terminal and start typing the first few letters of the program, then hit TAB and see what happens (TAB is autocomplete in the terminal :D)[/QUOTE]
 That is great!  Thanks for the tip!

---

### Post by acostanza on 2005-05-28
Tried that too, no luck though.  What does /. mean anyway?  I vaguely remember from DOS moving up a folder in heirarchy.  Is that right?

Thanks,
-Adam

---

### Post by clb137 on 2005-05-28
[QUOTE=acostanza]Tried that too, no luck though.  What does /. mean anyway?  I vaguely remember from DOS moving up a folder in heirarchy.  Is that right?

Thanks,
-Adam[/QUOTE]

Adam

It is telling linux to execute a program, if it does not work then it is not installed
can you post your 'sources.list' file it is in /etc/apt   thanks 

Open a terminal window  and type ./   not /.     so try ./bacula      

ley me know if it works

clinton

---

### Post by acostanza on 2005-05-28
[QUOTE=clb137]Adam

It is telling linux to execute a program, if it does not work then it is not installed
can you post your 'sources.list' file it is in /etc/apt   thanks 

Open a terminal window  and type ./   not /.     so try ./bacula      

ley me know if it works

clinton[/QUOTE]
 Right, ./  Tried that, here are my errors from the terminal:

adam@server:~$ ./bacula
bash: ./bacula: No such file or directory
adam@server:~$ ./bacula-
bash: ./bacula-: No such file or directory
adam@server:~$

Found the sources.list file you are referring to, but I don't see anything but comments.  Here it is:

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe main restricted multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

---

### Post by Mez on 2005-05-28
try the following command

sudo bconsole

That should start the bacula console :D

Also

[http://www.bacula.org/rel-manual/Brief_Tutorial.html#SECTION000121000000000000000](http://www.bacula.org/rel-manual/Brief_Tutorial.html#SECTION000121000000000000000)

Is a good uide to starting to use bacula

---

### Post by clb137 on 2005-05-28
[QUOTE=acostanza]Right, ./  Tried that, here are my errors from the terminal:

adam@server:~$ ./bacula
bash: ./bacula: No such file or directory
adam@server:~$ ./bacula-
bash: ./bacula-: No such file or directory
adam@server:~$

Found the sources.list file you are referring to, but I don't see anything but comments.  Here it is:

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe main restricted multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe[/QUOTE]


have a look at this 1st 

[http://www.bacula.org/rel-manual/Brief_Tutorial.html#SECTION000121000000000000000](http://www.bacula.org/rel-manual/Brief_Tutorial.html#SECTION000121000000000000000)

---

### Post by clb137 on 2005-05-28
[QUOTE=Mez]try the following command

sudo bconsole

That should start the bacula console :D

Also

[http://www.bacula.org/rel-manual/Brief_Tutorial.html#SECTION000121000000000000000](http://www.bacula.org/rel-manual/Brief_Tutorial.html#SECTION000121000000000000000)

Is a good uide to starting to use bacula[/QUOTE]

It will not work f it is not installed

---

### Post by clb137 on 2005-05-28
Hello,

have u tried the following?

[http://www.bacula.org/dev-manual/Testing_Your_Tape_Drive.html#_ChapterStart27](http://www.bacula.org/dev-manual/Testing_Your_Tape_Drive.html#_ChapterStart27)


clinton

---

### Post by clb137 on 2005-05-28
[QUOTE=clb137]Hello,

have u tried the following?

[http://www.bacula.org/dev-manual/Testing_Your_Tape_Drive.html#_ChapterStart27](http://www.bacula.org/dev-manual/Testing_Your_Tape_Drive.html#_ChapterStart27)


clinton[/QUOTE]


if this does not get u working i wil dig deeper


clinton

---

### Post by acostanza on 2005-05-28
[QUOTE=clb137]if this does not get u working i wil dig deeper


clinton[/QUOTE]
 Clinton,

Thanks so much!  It's working now.  I've got a lot to learn I see.  I'll be sure to check for the manuals next time. 

This is a great resource for us beginners!

-Adam

---

### Post by DanP on 2005-05-29
Hi Acostanza,

As a Fluxbox desktop user I find that many of the programs I
install don't put a listing into the menu. What I do is to open
a terminal and type **sudo update-menus** you will then be asked
for your user password (not the root password).  This will update
your menu lists(imagine that)and may also work for you to get backula
installed into your menus.

Be warned that the backup program that I use,Backup2L, and many others are
not graphic programs, but are meant to be run either from a terminal by typing
in the name of the program, or through cron which is a program which runs
periodic commands such as backup programs without user intervention-- 
perhaps at 3:00am while you're sleeping.

I have never used backula and don't use KDE or Gnome so this info may or
may not be useful to you.  You can also try typing **man backula**
into a terminal window to find out exactly what information the program
needs to run properly.  Remember that the **man** program will show you the
instructions for the programs installed onto your computer-- **man** is your friend.
 
Let us know what happened, if it works or not, and be sure to include any error
messages displayed when you try to run the program.

Good luck,

DanP

edit: Sorry,  a little slow on this post.

---

### Post by jobezone on 2005-05-29
[QUOTE=DanP]Hi Acostanza,

As a Fluxbox desktop user I find that many of the programs I
install don't put a listing into the menu. What I do is to open
a terminal and type **sudo update-menus** you will then be asked
for your user password (not the root password).  This will update
your menu lists(imagine that)and may also work for you to get backula
installed into your menus.

Be warned that the backup program that I use,Backup2L, and many others are
not graphic programs, but are meant to be run either from a terminal by typing
in the name of the program, or through cron which is a program which runs
periodic commands such as backup programs without user intervention-- 
perhaps at 3:00am while you're sleeping.

I have never used backula and don't use KDE or Gnome so this info may or
may not be useful to you.  You can also try typing **man backula**
into a terminal window to find out exactly what information the program
needs to run properly.  Remember that the **man** program will show you the
instructions for the programs installed onto your computer-- **man** is your friend.
 
Let us know what happened, if it works or not, and be sure to include any error
messages displayed when you try to run the program.

Good luck,

DanP

edit: Sorry,  a little slow on this post.[/QUOTE]
 DanP: You had to first install the package "menu" right?:)
I posted a HOWTO about this in the Hoary Tips&Tricks sub-forum.

A also good friend to us all is the /usr/share/doc/ directory. I bow down to this directory:)
This is where package's and programs you install with synaptic place their documentation. So, for backula, its documentation would probably be in
/usr/share/doc/backula  (or similar name instead of backula) .

---

