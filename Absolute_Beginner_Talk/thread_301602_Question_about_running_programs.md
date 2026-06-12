---
title: "Question about running programs"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by r0ckl0bster on 2006-11-17
Hey everyone I'm completely new to Linux, and so far I am absolutely loving Ubuntu I've had it for a few days
I have bee having a problem finding where programs are after i install them using apt-get and running them, is there an easy way/something I've missed in how to do this.  Thanks fo rany help you can give sorry if this is a repeat i searched and couldnt find anything to easily answer my question.

---

### Post by Bachstelze on 2006-11-17
Hi and welcome to Ubuntu :)

Usually, to run a program when it doesn't have a shortcut in the menus, you just type its name in a terminal and press Enter. But sometimes it's a bit more tricky so if you tell us which program you try to run, it'll be easier for us to help you out.

---

### Post by earobinson on 2006-11-17
also if you know the name of the program you can type which <program name> in the terminal to give you the location of the binary

type man which for more information on which

---

### Post by r0ckl0bster on 2006-11-17
awesome that seems to be working...except for beagle, but that is possibly because i think i may have already started the daemon and just can't see it anywhere but i was trying to get checkgmail up and running and it worked for that as well as a few other programs...i love the terminal and linux in general so much better than windows

---

### Post by mark_g on 2006-11-17
The system-essential programs are installed in /bin, the rest is in /usr/bin or (more seldom) in /usr/local/bin.

But you'll never have to go to that directory to start them. If it's a program with a graphical interface, it can most likely be started from one of the categories of the main menu.
The other programs can be started from a terminal or with the 'Alt-F2' shortcut and then typing the name of the program.
An even easier option is to make a 'Launcher' on your desktop (right-click on an empty space and select "Create Launcher".

Hope this helps.

---

### Post by r0ckl0bster on 2006-11-17
thanks for all the help, i still cant seem to get beagle and deskbar applet working i launch the beagle daemon, but i dont see anything, and nothing seems to be working with deskbar applet either

---

### Post by r0ckl0bster on 2006-11-17
figured it out

---

### Post by earobinson on 2006-11-17
cair to tell us what you did,

also do us a favor and edit the original post, click advanced, and mark the thread as resolved!

---

