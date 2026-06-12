---
title: "Installing programs not listed in synaptic"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by dolecannery on 2007-12-02
I would like to sync my calendar with google calendar (and everything else) and have seen GCALdaemon as a possible program to help.   I can not find the program via synaptic or the add programs functions. I can see the program on its website but do not know how to install it (What software uncompresses this software and how, how do I move the uncompressed software to the right location, how do I run the installation software, how do I make the interface point to it, I can read the directions on how to configure GCALdaemon but installing as opposed to configuring the actual software is greek to me.

---

### Post by Paqman on 2007-12-02
[Seen this?](http://monkeyblog.org/ubuntu/installing/)

Short version:
Easiest = Synaptic/apt-get
Easy = .deb
Not so easy = compiling tarballs

---

### Post by dolecannery on 2007-12-03
Thank you for taking the time to reply.  Unfortunately, the response assumes I already know what you are talking about i.e., know line commands, their parameters, directory manipulation, etc in linux.  For instance, it took me more than an hour to find the directory path of the storage directory where I put the zip file using the GUI.  When I go to directory to use the unzip command Unzip command is not found when executed from the directory I unzipped the file to, etc, etc.  This is the rule not the exception for trying to make anything work in Ubuntu. The same is true for the web site provided.  If you do not already know what it says, it is worse than meaningless as it takes hours and hours of frustrating work to accomplish very little.  I say all this after spending scads of hours trying to simply unzip a file to a directory and install it.  Nothing provided explains how to.  Thanks anyway, I appreciate the consideration and effort of all who are dedicated to move away from windows.  Someday.

---

### Post by philinux on 2007-12-03
Have a read through this,

[http://ubuntuforums.org/showthread.php?t=540330](http://ubuntuforums.org/showthread.php?t=540330)

---

### Post by Gary Nored on 2007-12-03
I'm an ignorant newby myself, but I've done this and here's what I've found to work. Unfortunately, I don't know how this can be done from the gui. but I can give you the commands and you can read up on them. You'll have to do all this as root, or use the "sudo" prefix for each step. 

1. Move the downloaded file to /usr/share/applications. 

2. Unzip and/or unarchive it. Since I have a mind like a sieve, I use a cheat sheet I got at FOSSwire.com for unix/linux commands. The last 2 or three characters behind the period will tell you what command to use. 

3. Try running it from there. If it won't work, it may not have permission to execute, so you'll have to change its permissions before it will run. Try chmod 704 filename first and see if it will run with you as a user. 

4. If that doesn't work, I  
   a. sudo chmod 777 filename (dangerous, I know but it worked for me once).
   b. now try chmod 704 filename. That sets it up so that you have permission to run it.

You should now be able to run your program from the command line at least. How you associate a program with an icon and item on the menu is still one of the mysteries of the dark world for me ....

It's never a good idea to leave a file's permissions set to 777 for long (if ever) but that's what I figured out, and it worked. 

Since I am so ignorant, you may want to wait for other suggestions before trying these. Doubtless there are more elegant ways, but this is how I struggled to success with Gramophile (if I remember correctly). From there on, just typing "gramophile" from the command line brought it up. 

Regards,
Gary

---

### Post by Sims2789 on 2007-12-03
You could just use GDebi and install things graphically, like in Windows or PC-BSD. Some people have command line fetishes. If you're not one of them remember that, like other modern, user-oriented desktop operating systems, Ubuntu rarely requires the command line.

---

### Post by Paqman on 2007-12-03
> **dolecannery said:**
> Unfortunately, the response assumes I already know what you are talking about 

To be fair, you're trying to accomplish something fairly fiddly here. I've just had a look at the [Linux install](http://gcaldaemon.sourceforge.net/usage11.html#p1) instructions on the GCALDaemon site, and it's pretty unfriendly. Granted you could simply cut'n'paste those commands blindly, but you're not really likely to understand them, so if they don't work first time, you're toast.

For what it's worth, those commands basically set up the permissions on the files after you unzip them. Maybe go and read up on the chmod command and the concept of file permissions if you're interested.

---

### Post by dolecannery on 2007-12-03
Thank you for your help.  I appreciate the useful advice and your time.

---

### Post by dolecannery on 2007-12-03
Thank you for the advice on the chmod command.  I will study it and hopefully make some further progress.  I did get the file to the computer, unzip it, and 'install' it.  So far nothing works, and I can not see any evidence it can do anything but I think I can hammer through it with your advice.  Thanks again.

---

### Post by dolecannery on 2007-12-03
Thank you for taking the time to lay out details.  I appreciate the useful advice and your time.

---

### Post by dolecannery on 2007-12-03
using the chmod command as indicated, and ignoring the 
'chgrp -R groupname /usr/local/sbin/GCALDaemon' command given on the website which means nothing to me (I do not know what a groupname is, nor do I have any idea of how to find out what mine is, or what I want it to be, or what the program wants it to be) .    The program responds asking for my google password when I enter the ping sort of command given on the gacaldaemon website.  This is progress  - something does something when I enter something indicating the program is on the computer and runs.  I will continue to next step to try to configure gcaldaemon. Thank you for your help.  Does this sort of installation procedure seems either easy or intuitive to anyone?  What am I missing?  Thank you all for your advice and patience.

---

