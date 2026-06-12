---
title: "Setting Enviroment variables for C-shell"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by Jonas thomas on 2008-04-05
I feel like the guy whose been sort of lost driving and has been sort of reluctant to ask for directions. I keep thinking I'm almost there, but I at a point where think I'm better off pulling over and posting on this  forum. A summary of how I got to where I'm at.
btw: I'm pretty much a newbie at this stuff and this is my first post on this forum..(Hello all)

    * I've been wanting to get Java 6 setup on my machine to run the C-shell script for the Opencascade installer. I found an interest article on the web that made sense to me:[http://www.antbook.org/display/antbook/Installing+Java+6+on+Ubuntu+7.04](http://www.antbook.org/display/antbook/Installing+Java+6+on+Ubuntu+7.04)

I managed to set the environment variables to the bash shell successfully per his instructions but got real confused trying to set this up for the C-shell.
In this guys instructions he talks about the "simple matter" about adding Java properties to the file: /etc/csh/login.d/java
My personal logic leads me to think that the /etc/csh/login.d would have been created at install or when I fire up csh in terminal. I suppose I could brute for and create the sub-folders, but my gut tells me that will not work. Am I wrong? I guess these are the questions I have:

    * Is /etc/csh/login.d/ something that csh recognize out of the box?
          o Do I need to manually create the folder for the file /etc/csh/login.d/java?
            I found: The C shell tutor([http://www.eng.hawaii.edu/Tutor/csh.html](http://www.eng.hawaii.edu/Tutor/csh.html) ) which talks about .cshrc .login .logout

      I think all I need to do is to plot the setenv stuff is .cshrc
      Is that correct?? Where is .cshrc located?
      Thanks in advance
      Jonas Thomas
      [http://blog.metalshaperman.com](http://blog.metalshaperman.com)

---

### Post by keeler1 on 2008-04-06
As far as setting up java 6, it is in the repositories. You shouldnt need to do anything but tell it to install.

There is sun-java6-bin, sun-java6-jre, sun-java6-jdk, sun-java6-plugin.

simply sudo apt-get install those files

You will need to have the multiverse repository enabled to do this. I am sure there is a way to do that with a command but I do not know what that would be.  However you can open up the file /etc/apt/sources.list and edit that to enable the multiverse repository.  Open it with gedit or some other text editor and remove the preceding # before the line that starts with "deb http: <some more>" and at the end of the line has multiverse.  

The easier way in 7.10 and hopefully in 7.04 too, is to open up a graphical menu of /etc/apt directory and double click on sources.list.  In 7.10 this opened up a gui interface and there was a menu item to enable the multiverse repository.

As far as the environment variables go, all you have to do is put the setenv commands in your .cshrc like you have figured out.  Normally the .cshrc is located in your home directory.

However when you run the c-shell it looks in several locations and sequentially gets the commands from those locations.  I am not sure exactly where the locations are but I know it does this.  One of them is probably the /etc/csh/login.d

---

### Post by Jonas thomas on 2008-04-06
keeler1
Thanks for the advise on the the multiverse repository. (believe it or not, I actually had that one figured out already)

I was trying to figure out the exact sequence where csh looks by default when it fires up and I ran across this blurb in the man pages:
 [B]An instance of csh begins by executing commands from the file
     /etc/csh.cshrc and, if this is a login shell, /etc/csh.login.  It then
     executes commands from .cshrc in the home directory of the invoker, and,
     if this is a login shell, the file .login in the same location.  It is
     typical for users on CRTs to put the command stty crt in their .login
     file, and to also invoke tset(1) there.[/B]

btw... I just figure out how to exit a man page.  just type q for quit(learn something new every day)
In my experiments, I've set up multiple user accounts in some of my experiments, so I think I'm going to dump this in:
etc/csh.cshrc 
I think the thing that confused me was I assumed that a .cshrc file would have been setup somewhere in my system when I installed csh. So I tried a little experiment.  I did a updatedb from the terminal and tried locate bashrc which I figured should there somewhere since this is the default shell. I then did a search for "cshrc".  Here is what I got:
[B]jonas@jonas-desktop://etc$ sudo updatedb
[sudo] password for jonas:
jonas@jonas-desktop://etc$ locate bashrc
/home/jonas/.bashrc
/etc/bash.bashrc~
/etc/skel/.bashrc
/etc/bash.bashrc
/usr/share/base-files/dot.bashrc
/usr/share/ubuntu-docs/ubuntu/sample/bash.bashrc_promptbeforeremovaloverwrittenconsole
/usr/share/doc/adduser/examples/adduser.local.conf.examples/skel/dot.bashrc
/usr/share/doc/adduser/examples/adduser.local.conf.examples/bash.bashrc
/root/.bashrc
jonas@jonas-desktop://etc$ locate cshrc
jonas@jonas-desktop://etc$ 
[/B]
I guess my conclusion is you need to create a cshrc from scratch. Now that I figured my options are on where to stick it, I guess my next step is to figure if what I put in there works.  Once again thanks...
Jonas Thomas
[http://www.blog.metalshaperman.com/]("http://www.blog.metalshaperman.com/")

---

