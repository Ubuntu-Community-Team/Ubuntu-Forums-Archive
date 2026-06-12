---
title: "Can't install any apps..."
date: 2005-08-25
forum: Absolute Beginner Talk
---

### Post by poopdedoop on 2005-08-25
I just got Ubuntu installed in VMware and its awsome, but i can't manage to install and apps. I can't change anything in any folders except stuff on my desktop and in /home/myuser 

I'm told that i don't have permission to edit thoes files. How do i make it so i can? I can do other administrator actions but i can't install anything because i can't put anything in thoes folders.

also when i try to isntall something i start by unpacking the tar.gz file using this in the root terminal

> ~/home/david/dls$ tar xvzf vmware-linux-tools.tar.gz 
and i get this message back

> bash: /root/home/david/dls$: No such file or directory

i don't know what to do.

this is stopping me from installing anything.

I love ubuntu but i can't install anything!!

---

### Post by Nequeo on 2005-08-25
Heya,

> 
I'm told that i don't have permission to edit thoes files. How do i make it so i can? I can do other administrator actions but i can't install anything because i can't put anything in thoes folders.


I don't suppose you're new to Debian-based systems by any chance? I made this mistake when I first switched to Ubuntu, too. I was used to installing things by hand, or with .rpms.

If you haven't already, take a look at Synaptic. It's in the menu under System--->Administration--->Synaptic. Before you run it, however, I'd reccomend adding Universe and Multiverse repositories by following the instructions here:

[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

That should take care of downloading and installing just about any program you want, automatically. 

As far as installing vmware tools is concerned, though, you might want to read through this thread: [http://www.ubuntuforums.org/showthread.php?t=40165](http://www.ubuntuforums.org/showthread.php?t=40165) as it covered the topic specifically.

Cheers,

---

### Post by Kyral on 2005-08-25
I don't mean to sound "snappish" but you don't want to be root ALL THE TIME. Ubuntu uses sudo to gain root access for that command only. Its a really bad idea to login or be root for a long time, 'cause then anything (or anyone) that slices into your system will have the same power as root. Which is bad, and one of the reasons that Windows is so open to spyware/malware/virus/hacker attacks :P

</rant>

---

### Post by poopdedoop on 2005-08-26
[QUOTE=Kyral]I don't mean to sound "snappish" but you don't want to be root ALL THE TIME. Ubuntu uses sudo to gain root access for that command only. Its a really bad idea to login or be root for a long time, 'cause then anything (or anyone) that slices into your system will have the same power as root. Which is bad, and one of the reasons that Windows is so open to spyware/malware/virus/hacker attacks :P

</rant>[/QUOTE]
 Thanks guys. and I know that it's not too good to be root all the time, but i'm the only one using it. I will make another account but after i get everything installed.

---

### Post by Joshua on 2005-08-26
[QUOTE=poopdedoop]Thanks guys. and I know that it's not too good to be root all the time, but i'm the only one using it. I will make another account but after i get everything installed.[/QUOTE]
 You mention not being able to get to other files and stuff.  It looks to me like that's because you are browsing the files as a normal user.  Like they said above, Ubuntu only uses sudo (not a root user) to do root commands.  If you open a root terminal and do everything by command line you should be able to access all files on your system.  Alternatively, you may want to try this:

If you hit <alt><ctrl> + <backspace> your system will shut down X and go to a text login.  Log in with your normal name and then do sudo startx, then enter the password.  I think this should run Gnome in root mode and you should be able to do everything in the GUI.  (I'm pretty new, and can't try this cause I'm not at home, but this has worked for some other things I've tried.)

Also, as far as this problem goes:

~/home/david/dls$ tar xvzf vmware-linux-tools.tar.gz  
and getting this message back
bash: /root/home/david/dls$: No such file or directory  

when you use the "~" it says to the system "go to my home folder".  If you're in a root terminal then it assumes your home folder is /root.  When you issue that command are you really in the /root/home/david/dls folder?  I assue you want to extract the file into the user folder.  Maybe you should try to issue the command like this:

$ tar xvzf vmware-linux-tools.tar.gz /home/david/dls

---

