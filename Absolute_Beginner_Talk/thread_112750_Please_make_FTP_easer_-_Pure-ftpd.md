---
title: "Please make FTP easer - Pure-ftpd"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by BlueIce on 2006-01-05
This is the first time I have really used linux, and I have installed it on my Server as I got fed up with windows. The install of ubuntu went perfectly but I then tried to set up a FTP Server.

This is what I did and how I think ubuntu could be made better:

Went to "Applications" then "Add applications"
Found "PureFTPd Administrator" and installed that.

Launched that and it could not find the service or what not. I then turned to the forums and followed a few things [http://ubuntuforums.org/showthread.php?t=79588&highlight=ftp]("http://ubuntuforums.org/showthread.php?t=79588&highlight=ftp")

I realised that was the wrong ftp program (ProFTPD).. that was ok but that program did not have a GUI and I was never going to add user by user via a terminal window etc.

So I reinstalled (don’t know what damage I did with all the fiddling with the other FTP program) and found that I needed to add extra Repositories.

I then went into "System" then "Administration" then "Synaptic Package Manager"

Added "pure-ftpd" and "pure-ftpd-common"

Well I guessed that installed it all, but "PureFTPd Administrator" still did not work.
I followed [http://www.ubuntuforums.org/showthread.php?t=91052&highlight=pure-ftpd]("http://www.ubuntuforums.org/showthread.php?t=91052&highlight=pure-ftpd")
but did not install the file they linked to as I think I had installed through the "add applications".

Those instructions failed as I’m guessing it installed it somewhere else when I added it with the repositories, but was able to use the run command.  I entered into the admin console where I was able to enter some of the settings which were supposed to be done via terminal window (not the security ones I think). I was able to log in to the FTP with my username (this username is the same one I get into the system).  When I created a new user it would not let me log in with them.

Anyways I think I have messed up all the security.

What I was hoping for is:
An easy click add users (did not want to create users that can actually log into the system, just the ftp).
Lock them into a directory, so they can’t get to root (I read you had to set some option or something (that’s scary)).

What I would love to see in the future is a GUI to do all this. Especially to find your own IP, because looking up commands to find out how to do basic stuff really sucks for a new person to linux.

Sorry don't mean to put anyone down for their hard work, I know it's take a lot of hard work to get to ubuntu, but I think their is a few finishing touches that need to be made for people who know the advance features of windows and want those features to be in a GUI in linux.

Any help would be greatfull. If not that’s ok as well.

---

### Post by frodon on 2006-01-05
Proftpd also have a GUI, but i often don't advice it because you need to run it as root, and so you can easily break your server configuration.
However if you really want a GUI, which is useless and resource eater, here is the link where you can find gproftpd ...  a GNOME proftpd GUI, maybe it's also in the repositories : 
[http://mange.dynalias.org/linux.html](http://mange.dynalias.org/linux.html)

---

### Post by BlueIce on 2006-01-09
Thanks frodon

I will have a good shot at getting Proftpd to work. It seems to be a more popular FTP server to use anyway.

A quick question, why do the GUI's need to be run as root yet the commands you need to type don't.  Also is using repositories a good thing or a bad thing?

Thanks

---

### Post by diggs on 2006-01-09
Why not just install fireftp  into firefox? It's an extension and works fine. Just fine.

---

### Post by BlueIce on 2006-01-09
[QUOTE=diggs]Why not just install fireftp  into firefox? It's an extension and works fine. Just fine.[/QUOTE]

Thanks diggs, but I wanted a GUI for a server, not a Client

---

### Post by frodon on 2006-01-10
[QUOTE=BlueIce]A quick question, why do the GUI's need to be run as root yet the commands you need to type don't.  Also is using repositories a good thing or a bad thing?

Thanks[/QUOTE]The GUI needs to be run as root because the FTP server could only be launched as root, also the configuration file (proftpd.conf) on which is based proftpd is in the root space so you need root access to write in this file, that's why you need to run the GUI as root to handle the server and it's also why i don't like FTP server GUI's in general.

But it's just my opinion and i will however make a kick guide for this GUI soon because even if i don't like this way to use proftpd (less secure i think), i think that beginners will like it.

---

