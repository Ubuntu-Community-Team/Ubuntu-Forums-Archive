---
title: "No Screen found?"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by cameron1 on 2007-08-03
I was installing it, and got errors saying NO screen found.

I'm on Vista right now, this is my first time to boot from Ubuntu.

Thanks for any advice.

---

### Post by spur on 2007-08-03
What kind of video card do you have and does the live cd run?

---

### Post by cameron1 on 2007-08-03
> **spur said:**
> What kind of video card do you have and does the live cd run?

It will boot, and it does alot fo stuff like I click install and it starts I get no errors.

Then I get the server error I click the info so I try to trouble shoot it, then it says Screen not found

I have this 
[IMG]http://img367.imageshack.us/img367/9739/saveaw9.png[/IMG]

heres a pic of my display settings

---

### Post by leo_rockway on 2007-08-03
x1400 won't let you boot the live cd... (i have one)

this is what i did (idk if you are familiar at all w/ linux so i'll try to make this as simple as possible)

after you get the error you get back into CLI (command line interface) and it may look scary but it is in fact a great tool.

you need to type this in:

> sudo nano /etc/X11/xorg.conf

note that it is X11 and not x11 (linux is case sensitive)

this will take you to a terminal text editor (there are many out there i just used nano because i like it).

You need to add this to the file

> Section "Extensions"
Option "Composite" "Disable"
EndSection

Section "ServerFlags"
Option "AIGLX" "off"
EndSection

then you hit control+o to save and control+x to exit.

now you type in:

> sudo apt-get install xorg-driver-fglrx

then

> sudo aticonfig --initial

and

> sudo aticonfig --overlay-type=Xv

after that you will be ready to start X by typing

> startx

if you decide to install ubuntu then you probably will have to do all that again after the installation.

lemme know if it worked for you.

---

### Post by cameron1 on 2007-08-03
> **leo_rockway said:**
> x1400 won't let you boot the live cd... (i have one)

this is what i did (idk if you are familiar at all w/ linux so i'll try to make this as simple as possible)

after you get the error you get back into CLI (command line interface) and it may look scary but it is in fact a great tool.

you need to type this in:



note that it is X11 and not x11 (linux is case sensitive)

this will take you to a terminal text editor (there are many out there i just used nano because i like it).

You need to add this to the file



then you hit control+o to save and control+x to exit.

now you type in:



then



and



after that you will be ready to start X by typing



if you decide to install ubuntu then you probably will have to do all that again after the installation.

lemme know if it worked for you.

I'll try this thanks.

brb 0:

---

### Post by cameron1 on 2007-08-03
It's saying "Option" uisnt a valid command on line 3. 

Something like that.

---

### Post by cameron1 on 2007-08-03
Okay that worked after messing with for a while.

I'm wondering umm

What do I do now, I see a orange background...

Thanks

---

### Post by cameron1 on 2007-08-03
I got it all installed, thanks for everyone's help.

Your really great people.

Take care.

---

### Post by leo_rockway on 2007-08-05
np... you should mark this as solved

---

