---
title: "I've messed up my firefox"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by whitetrashprincess on 2007-04-22
I'm a newbie and I think I've done something really dumb -- I was going to install the newest version of Firefox from the net (I'm using xubuntu).  I got into root login and double-clicked and it put the folder on my desktop - now when I click on firefox launcher it thinksthinksthinks and then does nothing.  I know it is not my internet connection because I can get mail and get on chat.
What did I do?
What can I do?
I did a search on forums, and got something about a manual install but it goes to a link about where the terminal is and doesn't say what to type.
I'd appreciate any help anyone could offer - I'm even willing to reinstall xubuntu but I can't figure out how to do that either!
(Sorry for the double-post I don't know how to move a thread)

---

### Post by aysiu on 2007-04-22
First, type this command in [the terminal](http://www.psychocats.net/ubuntu/terminal) (substituting in your username instead of *whitetrashprincess*): ```
sudo chown -R whitetrashprincess:whitetrashprincess /home/whitetrashprincess
``` This will make sure you have ownership of everything in your home directory, including your Firefox profile folder.

Next, type ```
firefox
``` in the terminal. If you get any error messages, copy and paste them back into this thread.

---

### Post by whitetrashprincess on 2007-04-22
it says
Segmentation fault (core dumped)

---

### Post by aysiu on 2007-04-22
I'd try [getting a fresh profile](http://ubuntuforums.org/showthread.php?t=103930&highlight=firefox+corrupt)

And then [reinstalling Firefox with this script](http://www.psychocats.net/ubuntu/firefox)

---

### Post by whitetrashprincess on 2007-04-22
FOr the new profile I got an error box that says:
The command "firefox -safe-mode" failed to run:  Failed to execute child process "firefox" (No such file or directory)

I forgot - I deleted the install box and the new folder that it created from my desktop -- is firefox just GONE now????

For the install:  Can I download the script and email it to myself?

Is there a way to reinstall it from the xubuntu cd?

I really appreciate all your help - now I understand how my mother feels when she screws up Windows!

---

### Post by jiminycricket on 2007-04-22
Yes, it's stil in the repositories and on the cd.  You can reinstall the version you had before with 'sudo aptitude install firefox'.

What version of Xubuntu are you running?  What version of Firefox did you have before and what are you trying to install now?  Firefox 2 should be in Feisty Fawn repositories

You can download Ubuntu packages here, just make sure you choose the right version: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by whitetrashprincess on 2007-04-22
I tried the 
sudo aptitude install firefox 
and it says E: Type '"deb' is not known on line 40 in source list /etc/apt/sources.list

I am running xubuntu 6.10

---

