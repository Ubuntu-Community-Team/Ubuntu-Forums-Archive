---
title: "Access to System Directories"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by Kiwi Si on 2006-12-13
Hi all,

Sorry for asking such a newby question but I have looked around and can't seem to figure out how to do the following.  I am a Windows user making the transition across to Ubuntu and have so far been impressed with it (apart from the ease of trying to add drivers).

I have installed Ubuntu v6.10 and am trying out both the KDE and Gnome interfaces.  I have installed and am running VMWare server.  I accepted the default location for saving the image files used by VMWare and these are stored in the /var/lib/vmware directory.

I am wanting to access these image files so that I may copy and back them up and can't seem to find a way via the graphical user interface either through KDE or Gnome. I seem to have access to my 'home' directory and all the files within though am guessing I can't access (or even see) the 'var' or 'lib' directories as these are system files and are restricted.

So my question is how can I access the var or lib files and/or directories?  I suspect that it may have to be through the terminal and some 'sudo' commands.   Any assistance or pointers much appreciated.

Thanks in advance,



Simon  :)

---

### Post by Izobalax on 2006-12-13
I don't about KDE, but in Gnome you can create a little applet that gives you root access to your filesystem. 

Right click on your desktop and Create Launcher. Call your applet 'Root Nautilus' for example and in the command line type in 'gksudo nautilus'.

This should create a little applet on your desktop called 'Root Nautilus'. Double-clicking it will prompt Ubuntu for your admin password, and once you've provided that a window will open and you can browse through your filesystem in root. 

HTH. If you need more help, just ask.

---

### Post by wpshooter on 2006-12-13
I know that there are reasons why, but this is still one thing I do not like about Ubuntu.  It is to restrictive on what a NON-ADMIN. level user can do.

If you want to do this via GUI, you probably need to elevate yourself to root user by logging in as root to the GUI.  This is NOT strictly advisable, but is possible.  I forget the exact commands to do it but maybe someone else that is a terminal line GURU can give them to you or maybe you can google to them or you should be able to find them somewhere on the Ubuntu site.

Good luck.

---

### Post by Kiwi Si on 2006-12-13
Hi Izobalax,

Thanks for the prompt reply.  I tried this (which taught me who to create these useful applets) and it appears to work ok apart from it only giving me the ´Desktop´ folder when I run it.  Any ideas much appreciated.  Is there a ´unhide' switch I need to uncheck somewhere?

Cheers,


Simon

---

### Post by [S|G] on 2006-12-13
On kde you can use "kdesu konqueror" to open a file manager as root.
On the command line you can execute commands using "sudo command". If you really want to run the system as root user, log off the graphical interface and start it like this: "sudo startx"

---

### Post by Kiwi Si on 2006-12-13
Hmmm, there is something not quiet right here.  I just tried the Konquerer solution and still only get the ´Desktop´ folder displayed.  There definitely seems to be something that is turned off that is stopping me from viewing the root files.

Thanks for your help - any more suggestions much appreciated.

:)

---

### Post by Izobalax on 2006-12-13
> **Kiwi Si said:**
> Hi Izobalax,

Thanks for the prompt reply.  I tried this (which taught me who to create these useful applets) and it appears to work ok apart from it only giving me the ´Desktop´ folder when I run it.  Any ideas much appreciated.  Is there a ´unhide' switch I need to uncheck somewhere?

Cheers,


Simon
Hi Simon, 

You said in your first post that you need access to the /var/lib/vmware directory. My guess is that this is going to be in your filesystem. So when you've opened up Root Nautilus, on the left you should see a hard drive icon labelled 'File System'. Go in there, and you should see the 'var' directory.

Let us know if this works for you.

---

### Post by Kiwi Si on 2006-12-14
Hi there,

No luck unfortunately - I do see a hard drive type icon that say's Root though when I double click on this all I am presented with is a single folder called Desktop --> this just contains all the usual stuff you'd expect in the desktop folder.  :( 


Cheers,


Simon

---

### Post by macogw on 2006-12-14
> **Kiwi Si said:**
> Hi there,

No luck unfortunately - I do see a hard drive type icon that say's Root though when I double click on this all I am presented with is a single folder called Desktop --> this just contains all the usual stuff you'd expect in the desktop folder.  :( 


Cheers,


Simon

Click "places" at the top. See "Computer"?  Click that.  Click "file system".  Var should be near the end.

---

### Post by Kiwi Si on 2006-12-14
Hi macogw,

Unfortunately I seem to have adopted a new problem with my fresh Ubuntu install so can't test what you suggested.  ](*,) 

I have just rebooted my PC (running Ubuntu v6.10) and get to the logon screen just fine. I enter in my username and password (which are correct), press enter and then recieve a black screen for a few seconds before it returns me back to the logon screen again. 

I don't appear to be receiving any error messages and have tried logging on via KDE and Gnome.

Any ideas much appreciated.

Thanks,


Simon

---

### Post by macogw on 2006-12-14
Does it go to the gnome login or does it say "logon:" on the black screen?  If the former, I'm sorry, I can't answer.  If the latter, enter your username, then your password.  If it doesn't go to  your desktop this time, then type "startx" (without the quotes) into the command line.

---

### Post by Kiwi Si on 2006-12-14
Hi there,

I have KDE set as my default though was last using Gnome (prior to the reboot and this problem starting).

I just tried what you recommended from the command line and get a ton of error messages saying:

Error opening /dev/wacom  : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
            No such file or directory

Then at the bottom - after many of these error messages, it says:

waiting for X server to shut down FreeFontPath: FPE "/usr/share/fonts/X11/misc"
refcount is 2, should be 1; fixing

I've tried running the startx command again and get the same thing. I'm pretty new to Ubuntu but am guessing this is serious?

Thanks,


Simon

---

### Post by macogw on 2006-12-14
Well, at least this gives us an error message to decifer rather than just blankness.  Ummm do you have a wacom tablet hooked up to it?  If yes, try unhooking that and rebooting while I research.

EDIT: [http://ubuntuforums.org/showthread.php?t=318206](http://ubuntuforums.org/showthread.php?t=318206)
Go there :)
Wow, third "oops, that upgrade broke stuff for people..." I've seen.  Only one affected me.  It was the one that wouldn't let me get online to find that little green box at the top that says "oops, that upgrade broke stuff for you..." yeah...useful, eh?  Um, if you start up the comp, then hit the Esc button when Grub appears and scroll down and grab and older kernel you should be able to boot from that with no problem.

---

### Post by Kiwi Si on 2006-12-14
Nope no Wacom tablet device at all.  I do, or did (now swapped it out with a PS/2 keyboard) have a Mac USB keyboard attached which in turn had my Microsoft USB mouse attached to it.

Hmm, just rebooted with the USB mouse plugged into the USB port on the back of my PC (as opposed to the Mac keyboards expansion USB port) and having a PS/2 keyboard attached.  

Apart from those two things I have no other external USB devices attached.

I tried startx again from the console though I get exactly the same error message. :( 

Could it be a permissioning problem on the directories?  Is there an easy way to set them back to the defaults - just to make sure?

Thanks again.



Simon

---

### Post by macogw on 2006-12-14
Go to the front page of the forum.  Look at the green box at the top.  Click the link in it.

---

### Post by Kiwi Si on 2006-12-14
Good spotting - thanks macogw, I'll check it out.

Thanks for all your help.


Simon :p

---

### Post by contadinoste on 2007-01-21
It's a new security feature in Konqueror ( maybe also in Nautilus, I'm using Kubuntu). Open "root folder" in panel and activate from menu "show hidden files", then you will see all folders  in the main window, but not in the tree. Or type in konsole:
cd /
ls
Edit/Delete Message

---

