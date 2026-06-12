---
title: "help needed"
date: 2005-06-10
forum: Absolute Beginner Talk
---

### Post by hypnotoad8 on 2005-06-10
](*,) 
that's how i'm feeling right now. i'm new to computers, and i received a live cd of ubuntu from my boyfriend. just one question - how do i use it? i'm really anxious to learn!
 :)

---

### Post by s0lid on 2005-06-10
first try to boot the live cd so if somethings go wrong you wont screw your files

---

### Post by az on 2005-06-10
[QUOTE=hypnotoad8]](*,) 
that's how i'm feeling right now. i'm new to computers, and i received a live cd of ubuntu from my boyfriend. just one question - how do i use it? i'm really anxious to learn!
 :)[/QUOTE]


When you turn on your computer, it follows a list of devices from which to boot.  It may be set to look to see if it can boot from the cdrom driver before looking for a harddrive.  It may be set to boot from floppy first, or it just may be set to boot from the hard drive and ignore the cdrom.


If this is the case, you have to change the setting in your bios.

When you boot, it should be displayed for a second or two, what key to press to enter the bios setup.  In my case, it is DEL.  In other cases, it may be F1, or another key.  Find the boot order setting and tell it to look at the cdrom before the hard drive.  Save and exit.

Put in the cd and boot the computer.  The live cd should boot.  Follow the prompts and do not worry about it messing up your system.   A live cd does ont do anything to your hard drive.

---

### Post by hypnotoad8 on 2005-06-10
ah, perhaps i should clarify  ;-)  i know how to boot the cd and get it started on the computer. i can open a terminal window and then.........i just sit there because i don't know what to do. i often watch my boyfriend type all these lines of code and whatnot into the terminal and do all sorts of things. 
so i guess i am looking for help with the commands (ie, openning a file) in the terminal, so i'm not lamely double clicking to open things.
 :grin:

---

### Post by bored2k on 2005-06-10
[QUOTE=hypnotoad8]ah, perhaps i should clarify  ;-)  i know how to boot the cd and get it started on the computer. i can open a terminal window and then.........i just sit there because i don't know what to do. i often watch my boyfriend type all these lines of code and whatnot into the terminal and do all sorts of things. 
so i guess i am looking for help with the commands (ie, openning a file) in the terminal, so i'm not lamely double clicking to open things.
 :grin:[/QUOTE]
 Well, what do you want to do with it ? There are thousands of commands.

---

### Post by az on 2005-06-10
What file do you want to open?  A text file?  Use a text editor.  vi, nano, emacs...

nano (filename)

---

### Post by N'Jal on 2005-06-10
NEVER type sudo rm -rf /* :P It'll screw your system up, always handy to know what NOT to type as well as what TO type

Ok to get system updates try this

sudo apt-get update
sudo apt-get upgrade

My VERY first command was 

ping [http://www.google.com](http://www.google.com)

it was the only thing i knew how to do, so don't wory it just takes a little practice, i used to fear the command line, now although i might not know what i am doing im happy doing it in the terminal

---

### Post by poofyhairguy on 2005-06-10
[QUOTE=hypnotoad8]ah, perhaps i should clarify  ;-)  i know how to boot the cd and get it started on the computer. i can open a terminal window and then.........i just sit there because i don't know what to do.[/QUOTE]

You can not use the terminal if you want. I prefer GUIs if I can get them.

---

