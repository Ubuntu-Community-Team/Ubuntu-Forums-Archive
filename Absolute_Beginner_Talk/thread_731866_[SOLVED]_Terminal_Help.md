---
title: "[SOLVED] Terminal Help"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by T2manner on 2008-03-22
okay.

as i'm fairly new to ubuntu. i've got no idea how to work the terminal.

i heard it was similar to windows command prompt, but the commands are different.

can somebody help me get familiar with it?

---

### Post by (((X))) on 2008-03-22
Here is a nice guide teaches basic shell commands and describes how shell works in general.
[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)

---

### Post by marco123 on 2008-03-22
There's a good guide here: [http://ubuntuforums.org/showthread.php?p=990636](http://ubuntuforums.org/showthread.php?p=990636)

The way I learned though was just to jump in and start using LInux, you'll pick it up pretty fast.

I'd say the most important commands are:

top  -  Will give you a list of all running proccesses. (Q to quit) 
sudo apt-get <insert application name>  e.g  sudo apt-get firefox  -  Will install any program in the repositories.

There are loads more here: [http://www.oreillynet.com/linux/cmd/](http://www.oreillynet.com/linux/cmd/)

Cheers, Marco.

---

### Post by wesley_of_course on 2008-03-22
And yet another right here from the forums ;[http://ubuntuforums.org/showthread.php?p=990636](http://ubuntuforums.org/showthread.php?p=990636)    these start from the beginning and go to advanced . 

     As does this one ;  [http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)

             I've found both very useful in my own learning curve and theres another on Psychocats  but don't have the url at the moment .  Have fun and don't be intimidated , it's actually fun !

---

### Post by T2manner on 2008-03-22
wow thanks guys

btw
what are repositories

---

### Post by (((X))) on 2008-03-22
> 
top - Will give you a list of all running proccesses. (Q to quit)
sudo apt-get <insert application name> e.g sudo apt-get firefox - Will install any program in the repositories.

k is to kill process, enter process id to kill
q is to quit top

It's sudo apt-get install firefox

the option firefox will not be understood by apt-get, so nothing will be installed.

---

### Post by marco123 on 2008-03-22
The repositories are huge collections of safe software that you can install easily.

Go to Applications>Add/Remove  or   System>Administration>Synaptic Package Manager

There are literally thousands of free programs that you can install just by checking the box next to them. (Or sudo apt-get on the command line if you know the apps name.)  

Enjoy.:) Cheers, Marco.

---

### Post by marco123 on 2008-03-22
> **(((X))) said:**
> k is to kill process, enter process id to kill
q is to quit top

It's sudo apt-get install firefox

the option firefox will not be understood by apt-get, so nothing will be installed.

Oops, sorry, my bad.  Long night last night. lol

---

