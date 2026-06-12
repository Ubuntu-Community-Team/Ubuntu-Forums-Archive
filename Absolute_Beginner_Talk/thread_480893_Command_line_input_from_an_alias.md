---
title: "Command line input from an alias"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by mirrorhall on 2007-06-21
#-o just can't do this - anyone able to help?

**[COLOR="Red"]EDIT[/COLOR]**:Just found "Forcefield"an experimental GUI  [http://ubuntuforums.org/showthread.php?t=364415]("http://ubuntuforums.org/showthread.php?t=364415") (will try it out and report back) [COLOR="Green"]*Good try, but unstable and unable to remember mount points.*[/COLOR]

**This question isn't really about truecrypt, but about how to pipe data from a terminal [ run a bash script to perform an action and pipe/redirect required input to a terminal window]** [COLOR="Sienna"]Any good bash gurus out there?[/COLOR]

I used truecrypt to encrypt my 4GB pqi usb stick. Everything works fine, but i can only mount the disk if I open a terminal and issue the commands needed - why? because in the terminal truecrypt asks for a password (naturally). If I make an alias or try to make a bash script to do the same thing it never works because I can't input the password! I'm stuck ](*,) 

For security purposes i don't want to include the password in the script - I want to be prompted to enter the password as I think this is the only real way to keep the data safe.

There is no GUI for** truecrypt** in Linux as far as i know, so what i would like to be able to do is create a bash script which allows me to mount the drive with the requisite commands but opens a window (terminal or otherwise) which allows me to input the password.

Here's a summary of what I would like to be able to do:

1. Plug in my usb stick
[COLOR="DarkRed"]2. Either automatically, or manually mount the device via a script
3. Input the password (via a window, terminal ...)[/COLOR]
4. Use the device
5. Close the encrypted partition 
6. remove the usb stick.

NOTE: *Closin&#609; the encrypted partition from a script is easy because no password input is required.*

---

### Post by pmg on 2007-06-21
I'm not sure if this will help, but it might... You can open a terminal window and within it run a command with **xterm -e somecommand** and when *somecommand* is done the xterm window will go away.

---

### Post by mirrorhall on 2007-06-22
> **pmg said:**
> I'm not sure if this will help, but it might... You can open a terminal window and within it run a command with **xterm -e somecommand** and when *somecommand* is done the xterm window will go away.

Thanks.

Here's what i did 

1. create a script

> #!/bin/bash

gnome-terminal -e 'sudo truecrypt /media/ANBC/.anbc.tc /media/anbc-tc -M uid=anbc,gid=users'


2. enter the password

3.Terminal fades away - leaving me with a mounted drive - just what i wanted.

---

### Post by knightnet on 2007-06-22
I had the same problem.

The answer though is nice and simple: use KDialog :)

See The KDE user guide ([http://docs.kde.org/stable/en/kdebase/userguide/userguide.pdf](http://docs.kde.org/stable/en/kdebase/userguide/userguide.pdf)) for all the options.

Enjoy.

---

