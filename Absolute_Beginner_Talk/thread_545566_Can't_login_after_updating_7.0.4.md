---
title: "Can't login after updating 7.0.4"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by jonedwa on 2007-09-07
I have a brand-new installation of Kubuntu 7.0.4 on VirtualBox on my WinXP PC. I'm new to Unix and want to switch over eventually. The installation from the Live CD went fine, I got my user account set up, and booted into the GUI just fine. The system said there were >160 updates, so I set the update manager to downloading and installing them. Once they were all installed, I rebooted. Big mistake.

The system boots up to the login screen. I type in the password, the screen goes black for about five seconds, then returned right back to the login screen without any type of error message. Repeated tries didn't change anything.

I'm _very_ new to Linux, so will need more detail on how to perform any solutions presented.  I checked related threads but couldn't find a solution.

Thanks in advance for your help!

---

### Post by meborc on 2007-09-07
ok... what you can try is to boot into recovery mode (select from grub menu after rebooting)

this will boot you to a command line interface... let it load... you should come to a line where you can insert your username... do that and enter... then insert your password (you will not see it, or ***... you just type it and hit enter)

when you are loged in type "sudo dpkg-reconfigure xserver-xorg"

follow the questions... if you don't know all the answers, just choose the default one... the important Q's are the video driver and resolution... choose the correct ones...

once done, reboot into normal mode

if that doesn't help, report back here :)

---

### Post by eapache on 2007-09-07
That probably won't help, as the login screen uses x, so any x problems would happen earlier. It is therefore most likely a kde problem. Did you do any customization of your taskbar etc. (or startup programs)?

---

### Post by BrendanM on 2007-09-07
I think I've seen this before. Try this: at the login screen, there's an option for "Session" , pick it, and choose something other than "Last session" choose either "Gnome" or "KDE" or whatever. Then try logging in.

---

### Post by meborc on 2007-09-07
> **eapache said:**
> That probably won't help, as the login screen uses x, so any x problems would happen earlier. It is therefore most likely a kde problem. Did you do any customization of your taskbar etc. (or startup programs)?
it is way too late here... :D i shouldn't give advice when i'm sleepy... thanks for pointing this out

sorry :KS

---

### Post by Nythain on 2007-09-07
yeah, this is a commonly occuring problem, that generally doesnt have anything to do with the xserver, thats a whole different update break :) i dont know the solution since i havent had the problem, but searching the forums for "session lasted shorter than 10 seconds" might give you the answer you seek

---

### Post by jonedwa on 2007-09-07
Ok,  tried the first solution anyway just for kicks - no luck.  Tried logging in to "KDE" seesion rather than default, no luck again.

I did change a few things like screen background and screensaver, but nothing major I think...

Searched for "session lasted shorter than 10 seconds" and got only this post :(

Any other suggestions?  I saw something about file ownership somewhere, to type in "sudo chown username:username *.*", but it couldn't find the *.* - does this ring any bells?  It was something about the ownership of some files in the user directory being changed to root and having to be changed back to the user, but the syntax of the command must've been wrong.

---

### Post by parvinder on 2007-09-07
I really don't know the solution to this problem as I am also new to Linux but as per my knowledge based on Windows OS etc... it seems the session information is lost and hence when you login your session is terminated immediately because there is no persistent information.

You may try to uninstall and reinstall gnome-desktop if you are able to log in to text mode of ubuntu as described above.

Remove gnome-desktop :   apt-get remove ubuntu-desktop
Install gnome-desktop : apt-get install ubuntu-desktop 

Restart your system. I am not sure but the windows way to do it will be to remove and restart in text mode and then reinstall and restart the system.

Let me know if this works.:cool:

---

### Post by BrendanM on 2007-09-07
Yeah, if you can boot into recovery mode, you can change the ownership of your home directory in case the permissions on that got messed up. The command is going to be "sudo chown username:username /home/username/"

So give that a shot. It might help.

I've also occasionally seen it get mad where there isn't enough space free on the hard drive to start the session. So double-check that.

---

### Post by jonedwa on 2007-09-07
Well, the chown thingy didn't work.  I have a snapshot of the updated system just before I rebooted, is there anything I can look for there that'll help find a solution?  I have 3Gb left on the HD btw

---

### Post by jonedwa on 2007-09-07
Ok, also tried the apt-get remove and install for kubuntui-desktop and no luck there.

---

### Post by GuitarRocker2562 on 2007-09-07
that is because reoving kubuntu-desktop doesn't actually remove anything. My best suggestion would be to hit control+alt+f1 at the login screen to take you to command line and type sudo apt-get update && sudo apt-get upgrade

---

### Post by jonedwa on 2007-09-08
Alright.  I sudo'd update and upgrade and am still having the same boot problem.  It goes to a black screen briefly then back to login with no error.  How do I watch the boot process and login process in the console to see if there's a problem?

---

