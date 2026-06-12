---
title: "How do I exit from X server?"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by Adjutant on 2006-06-23
I'm trying to install drivers for nvidia, but no matter what I do I cannot exit X.

All I need is some quick guide to exit X server. I tried ctrl+alt+F1, I also tried the init 3. But no success. I read somewhere that you need to kill all the X processes at the same time but I'm too much of a noob to figure out how to do that.

Please help, thanks.

---

### Post by Kilz on 2006-06-23
[QUOTE=Adjutant]I'm trying to install drivers for nvidia, but no matter what I do I cannot exit X.

All I need is some quick guide to exit X server. I tried ctrl+alt+F1, I also tried the init 3. But no success. I read somewhere that you need to kill all the X processes at the same time but I'm too much of a noob to figure out how to do that.

Please help, thanks.[/QUOTE]
I believe its crtl alt backspace.

---

### Post by aysiu on 2006-06-23
Try Control-Alt-Backspace--that should reset the X server.

---

### Post by Kurt` on 2006-06-23
To restart X, hit Ctrl-Alt-Backspace or

```
sudo /etc/init.d/gdm restart
```

To stop X completely,

```
/etc/init.d/gdm stop
```

You can do this from any terminal, or even over SSH.

---

### Post by aysiu on 2006-06-23
If you're using KDM, it's a similar deal: ```
sudo /etc/init.d/kdm stop
```

---

### Post by Adjutant on 2006-06-23
[QUOTE=Kurt`]To stop X completely,

```
/etc/init.d/gdm stop
```

You can do this from any terminal, or even over SSH.[/QUOTE]

Thanks, worked like a charm.

Now I just have to get this valid CC compiler name thing fixed....

---

### Post by Kurt` on 2006-06-24
[QUOTE=Adjutant]Thanks, worked like a charm.

Now I just have to get this valid CC compiler name thing fixed....[/QUOTE]

apt-get install build-essential ?

---

### Post by tseliot on 2006-06-24
Try this guide of mine (see Method 2) or use my script:
[http://www.ubuntuforums.org/showthread.php?t=139264]("http://www.ubuntuforums.org/showthread.php?t=139264")

---

### Post by Chrishas on 2006-10-26
i want to login into a terminal,no x server running at all as i'm trying to install nvidia drivers and they cant have x running during installation, I used the commands mentioned but they just log me out

---

### Post by asi on 2006-10-26
1. You can log onto rescue mode when you're loging in first click onto setings->grafic shell (or something like it  I hawe it in other language)-> safe mode (not gnome safe mode!!!)
2. Or you can go to rescue mode when your computer is starting in Grub yust  chose Ubuntu (your version etc...) (rescue mode)...

As you're noviece is recomended for you first to instal mc because it'll be much easier to find something there...
yust write in terminal sudo apt-get mc (then answer "y" for the next ansver)
and after starting  Ubuntu in rescue mode write mc and use hym...

---

### Post by Chrishas on 2006-10-26
The safe mode u described still has X running,I dont want to just exit Gnome

---

### Post by asi on 2006-10-26
then you need to chose safe mode from  Grub when restarting computer...

---

### Post by asi on 2006-10-26
Or you can try this: (postet from other forum)

I still booted to X because I hadn't updated to the nVidia drivers, and I downloaded the *.run package off the nVidia website.
Moved to a console (Alt+Ctrl+Shift+F1) and shut down X using 
Code:
sudo /etc/init.d/gdu stop
Ran the package as root. It says it needs a package from nVidia.com. Select yes. Replys saying cant find one, will create one instead.
Go ahead with it.
Let it install.

Back at the console, get the glx by typing 
Code:
sudo apt-get install nvidia-glx
Enter
Code:
sudo nano /etc/modules
Add at the end nvidia <New line> glx
Type
Code:
sudo /etc/init.d/gdm start
Now it will load.

---

### Post by galdir on 2007-08-30
hi guys...
well... didn't work for me...
if I use de crtl+alt+f1 to go to virtual terminal 1, login and use gdm stop, the X dont stop in the virtual terminal 7, still working... seconds after a blue window informs that x is working and if i wanna open another x, i answer no and Im back in the X window gnome.
I tried logging in rescue mode, and is this case X dont open, but the nvidia install informs that the runlevel 1 is not the better level to the installer... them I exit the installer and use the initlevel 3... so again I have the login promp in shell... and when I log i have again the X login...
I my perspective... we need change the configuration file of the user to run only the runlevel 3... install de nvidia drivers e change back the conf file... but I didnt find this conf file... is not rc.conf and not inittab... what is?
mmm... I will try see the rc file for level 3
best regards...

---

### Post by galdir on 2007-08-30
well... to nvidia drivers, a solved the problem... im ubuntu user, so in the gnome System &#8594; Administration &#8594; Restricted Devices Manage, and enabled 3d driver... and Im using now Beryl Manager! the desktop is great!
but still wanna know how to run terminal in runlevel 3 without the X server runing...

---

### Post by Macca86 on 2007-12-19
> **Kurt` said:**
> To restart X, hit Ctrl-Alt-Backspace or

```
sudo /etc/init.d/gdm restart
```

To stop X completely,

```
/etc/init.d/gdm stop
```

You can do this from any terminal, or even over SSH.

thankyou so much, worked perfectly, top job!

---

### Post by 77midget on 2008-02-10
at the risk of necro-posting, I just wanted to thank all who contributed to this post. I am in week 1 of my linux experience, and was having a devil of a time getting the enhanced Nvidia  drivers installed. With the help in here, I was able to get it done tonight, and now can enjoy the enhanced content, etc. Also, my machine seems to be operating faster and crisper with the new drivers. 

I am a (former) hard core windows dude (occupational hazard) now running 7.10 on a Dell Precision M70 2,13Ghz w/ 2GB, and the Nvidia Quadro 1400 256mb video. I have been able to learn enough to fix and configure the broadcom wireless card and now the nvidia card, Once I get my work VPN client working, I will be scrubbing my Vista disk, and going 100% to linux, though there is still a lot to learn

---

### Post by fruhbolk on 2008-03-25
I'm getting the NVIDIA setup to run ok but I'm getting this message (I'm using Debian 4.0).

"ERROR: Unable to find the kernel source tree for the currently running kernel"

---

### Post by dtrot55 on 2008-05-11
I tried the above code and here is what i got:

dtrot@Ubuntu-Dtrot:~$ /etc/init.d/gdm stop
open: Permission denied
 * Stopping GNOME Display Manager...                                            open: Permission denied
                                                                         [ OK ]
dtrot@Ubuntu-Dtrot:~$ 


go to install the drivers and it still says i have a xserver running....any idea???

---

### Post by dweez on 2008-05-13
> **dtrot55 said:**
> I tried the above code and here is what i got:

dtrot@Ubuntu-Dtrot:~$ /etc/init.d/gdm stop
open: Permission denied
 * Stopping GNOME Display Manager...                                            open: Permission denied
                                                                         [ OK ]
dtrot@Ubuntu-Dtrot:~$ 


go to install the drivers and it still says i have a xserver running....any idea???

You have to do "sudo /etc/init.d/gdm stop" to close the xserver.

I'm having the same issue as fruhbolk.  When I try to run the nvidia driver installer I get an "Unable to find the kernel source tree...." error.  Any ideas?

---

### Post by Tsabrock on 2008-05-19
I've been trying to exit the X Server for the same reason, but I'm having a different problem than what other people have been reporting.  When I do the "sudo /etc/init.d/gdm stop" command, it exits the GUI entirely, runs a few commands, then stops.  It can accept keystrokes, and echos what I type, but nothing seems to happen.

(The following is a listing of what shows up on my computer screen.  All are prefixed by a "* " and all are ended by "[ OK ]" (minus the quotation marks).  Forgive any small errors, since I typed this on my laptop while looking at my desktop's screen.

Starting anac(h)ronistic cron anacron
Starting deferred execution scheduler atd
Starting periodic command scheduler crond
Checking Battery state...
Running local boot scripts (/etc/rc.local)

After that nothing else happens except for a flashing curser, and the ability to type information.  Again, the computer does not respond to any command entries, and sits there like a paperweight until I reboot the system in some fashion.

I'm using a fresh install of Ubuntu, version 8.04.  AMD 64-bit version.  All updates were installed as of this writing.

---

### Post by overdrank on 2008-05-19
> **Tsabrock said:**
> I've been trying to exit the X Server for the same reason, but I'm having a different problem than what other people have been reporting.  When I do the "sudo /etc/init.d/gdm stop" command, it exits the GUI entirely, runs a few commands, then stops.  It can accept keystrokes, and echos what I type, but nothing seems to happen.

(The following is a listing of what shows up on my computer screen.  All are prefixed by a "* " and all are ended by "[ OK ]" (minus the quotation marks).  Forgive any small errors, since I typed this on my laptop while looking at my desktop's screen.

Starting anac(h)ronistic cron anacron
Starting deferred execution scheduler atd
Starting periodic command scheduler crond
Checking Battery state...
Running local boot scripts (/etc/rc.local)

After that nothing else happens except for a flashing curser, and the ability to type information.  Again, the computer does not respond to any command entries, and sits there like a paperweight until I reboot the system in some fashion.

I'm using a fresh install of Ubuntu, version 8.04.  AMD 64-bit version.  All updates were installed as of this writing.

Hi and welcome, are  you using the command from a GUI (desktop) and have you tried to use the keys ctrl, alt, F1 keys all at the same time and this will bring you to the command line then login (if necessary) and use the command ```
sudo /etc/init.d/gdm stop
```

---

### Post by Tsabrock on 2008-05-19
I've tried that command from a few places - I've done the CTRL+ALT+Backspace, but all it does it takes me to the login screen.  From there, I've tried various instances (Including Safemodes without Gnome), but all seem to take me to some sort of GUI with X running (even the one that says Safe-mode Terminal) but the end results are still the same.

I've seen several people say there's a terminal accessible from the login screen, but I've not figured out yet how to access it (the login screen is a GUI still).

EDIT: Hmm, after i typed it, I realized a difference, you said CTRL-ALT-F1, I missed that part... I've seen CTRL-ALT-Backspace several times.  *smacks forehead* I totally missed the fact that "Backspace" and "F1" are two different keys on the keyboard :)

That has done the job.  Now there's other issues of getting the compiler for my kernel running (libc), but I think I've read how to do that in other posts.  If I have further problems, I'll post here.  Thanks!

---

### Post by wjsim on 2008-05-25
Pardon me for hijacking this thread but I decided to be nice and not create a new one.

Same problem here, X server running and I can't install Nvidia drivers. I did "Ctrl-Alt-F1" in the GUI. I did "sudo /etc/init.d/gdm stop". I went into desktop (that's where my nvidia driver is) and "sudo sh pkg.run" and the same message comes up.

Am I missing something? I'm a total noob at Linux/Ubuntu... will appreciate any help :)

---

### Post by wjsim on 2008-05-25
I've managed to get the drivers to run... but now it's telling me I don't have the kernel and the installer needs to recompile a kernel and goes on to tell me I do not have the library files to compile. This words used to mean something when I was still doing pascal but in ubuntu and nvidia? help, lost lost :lolflag:

---

### Post by dweez on 2008-06-03
Well, with one of the recent kernel updates, my gdm broke again.  Previously, I have just reinstalled the nVidia driver by switching to tty2 (Ctrl+Alt+F2...F1-F6, any will do, I just prefer F2), typing sudo /etc/init.d/gdm stop then running the sh pkg.  

Well, this time, no matter what I did, the install kept saying it appeared I had an X Server running.  Back, with inittab, I could easily change the runlevel to 3, reboot to bring it to multi-user console/terminal mode (i.e., no X) and run the sh pkg.  Now that Ubuntu has shifted to rcX type runlevel assignment, I haven't found a simple/easy/universal way to change the runlevel except via telinit (doing a telinet 3 and running the sh pkg still gave me the alert and killed the installer).  

I did a telinit 1 which pretty much kills all your running processes and then gives you an option to 1) Continue with normal boot, 2) repair packages, 3) drop into root console, or 4) Attempt to fix X server.  I chose 3 and ran the sh pkg but receive a warning regarding an (?)-fs so I canceled out.  After trying a bunch of other fruitless stuff, I decided to go ahead and run the sh pkg in telinit 1 and it worked perfectly.

All that to ask this, any of you guru's out there familiar with the error I got when I attempted to run the sh pkg in telinit 1 (I know, I should have written it down) and know whether I could have done some damage to the install?  I'm not too concerned for this box as I was already determined to reinstall if it hadn't of worked, but would like to know in case I see the same thing on other systems that might be more critical.

---

