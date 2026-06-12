---
title: "install adobe flash"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by bkelly on 2008-01-26
I have spent most of the day trying to install the Adobe Flash player.  When my $40.00 Wyle "Ubuntu Linux" book gave me dozens of pages of information about installing software, but never said how to do it, I came here.

When initiating a new thread to install Adobe Flash, the forum recommended a thread which led to this site.  
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Browser_Plug-ins](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Browser_Plug-ins)

There it said to use this command:
sudo apt-get install flashplugin-nonfree

After opening a terminal and entering the command, it asked for the password.  After supplying the password, it returned to the prompt.  Nothing happened.  No error. No install.  No nothing.

So I logged out and back in as root.  That worked, but the install failed.  Per the noted web site, I went here:

[http://ubuntuforums.org/showthread.php?p=4073291](http://ubuntuforums.org/showthread.php?p=4073291)

It had more instructions that I followed and received this error message:

ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.

Two questions:

1)  Why did the sudo command not work?
2)  Can I do something to get the Flash player to work?

---

### Post by Kilz on 2008-01-26
You have a 64bit install. [Go here, get my script and run it. ]("http://ubuntuforums.org/showthread.php?t=476924"). You might also want to post future questions in the [64bit section so other 64bit users can help you.]("http://ubuntuforums.org/forumdisplay.php?f=134") 64bit users sometimes have issues that are specific to 64bit.

---

### Post by bkelly on 2008-01-26
The post from Kilz installed the flash player.  Thanks.

At the end of the Flash install, it asked for my user ID.  I entered my user name of bkelly.  If some day I add another account, will the installed FLASH work for that new account?

Why was I unable to run using the sudo command.  As before, I had to log off my personal account, log on a root, and do the install.

---

