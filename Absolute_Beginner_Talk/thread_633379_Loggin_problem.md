---
title: "Loggin problem"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by Cushie on 2007-12-06
I am having a sudden problem with Gutsy (Mint) installed for about 2 weeks. Suddenly I can't get past the login screen (a title 'Gnome Desktop' and a footprint logo appear).

I have checked 'home' name and that is ok, I have reset 'passwd' at least twice, but cannot get past the login. It does not say 'error' or 'check Caps Lock', but just returns to the login entry box. Any help would be welcome.

---

### Post by Nano Geek on 2007-12-06
If you are using Linux Mint, then you should probably look on the Linux Mint forum. They probably have more knowledge on the issue than we would. 

But does it give you any error messages, or what does it do when it fails?

---

### Post by fermin on 2007-12-06
Hi:

Hi have the same error as of today. I installed Ubuntu 7.10 on my PC for about 2 or 3 weeks now and all was OK but today ¡I can't get past the login screen! I type my username and password correctly and it starts running as if it was loading gnome but after a few seconds i just get back to the login screen, as if i had never entered my user and password; if i enter my user and password again i get the same over and over in a never ending cycle. I had several other registered users and with all of them happens the same. When i enter a random inexistent user i get the usual error messager. Any ideas? Can anybody help me? :(

---

### Post by Cushie on 2007-12-07
Sadly it is not possible to join the Mint forum as it it closed, presumably to new members or maybe is only open to paid subscibers.

But nevertheless it is still 'Gutsy'.  There are several other posts fairly similar but not quite this problem.  Possibly something to do with the 'Gnome Desktop' which was an alternative preference, but I am not aware of its significance.

---

### Post by shuttleworthwannabe on 2007-12-07
Just to confirm, I also have had this problem before; I created a new account and it sorta worked.

---

### Post by Cushie on 2007-12-07
I booted in recovery mode, I checked the home user account (as I expected) and I reset the 'passwd'  I added  a new user and password.  After reboot neither will gets past the login screen!

Help appreciated or otherwise seems nothing is left but a complete reinstall and the the online updates?

---

### Post by fermin on 2007-12-07
I rebooted the system and set the sesion mode as fail proof (resetting all window manager settings to gnome's default) and it started OK, i havent had problems since. I recalled i had done something wich might have triggered this problem: since i couldn't enable the "desktop effects" to make my gnome better looking i asked for help with a friend who told me to introduce some code in the console to install something called Xgl or alike (i dont quite remember); it didnt solve my problem and i still cant enable the desktop effects (probably due to my video card) but when i rebooted my PC the login problem started. I reckon the solution is to eliminate this Xgl window system from the sesion options, unistalling it, or at least to eliminate it as default setting. I still have to contact my friend to tell me how i revert the instruction i entered... or, can anybody else help me do this?

---

### Post by Cushie on 2007-12-08
Could you suggest how I set  'failproof' I must give the command after the 'recovery' mode prompt.  Otherwise I cannot get the 'failsafe mode' option to boot from the login screen?

---

### Post by fermin on 2007-12-11
In my ubuntu 7.10 distribution in spanish, when you are at the login screen, theres a gear icon at the lower left corner where you can select to change session type and in there are several options available one of which is this "failproof" or "failsafe" gnome session (i don't know exactly how it says in english); there's also a "failproof" or "failsafe" command session. I picked the failsafe gnome session and it started OK. I did some research and the problem was i installed compiz xgl for the session with a comand i entered in the terminal (which i was given by a friend) and theres where the problem started since it modified my default session options. Now i don't know how to revert the problem but i can still enter normally by always selecting this failsafe mode from the login screen.

---

### Post by Cushie on 2007-12-13
Gracias Fermin, salute!

Yes I did try several options.  From the 'Recovery mode' I did 'startx' and got back into the system.  Reset the password again. Made a few screen changes, tried automatic login, and a  did a few upgrades. Fortuna! Now I'm back in as normal on Gnome as you can see..
Felicidades.
Cushie

---

### Post by diafygi on 2008-01-01
I am having the same problem as you, and it seems to be narrowed to the installation of xserver-xgl. You shouldn't need XGL for 2D stuff. If you want Compiz-fusion, look on Free Software Magazine's [chart]("http://www.freesoftwaremagazine.com/blogs/bored_with_3d_desktops") for what you need to enable 3d effects for your video card. It says my video card (Nvidia GeForce2 Ultra) should work with XGL, but I can't seem to get XGL to work. So if you have found a solution for this problem that doesn't involve uninstalling XGL, please post it.

[This]("http://ubuntuforums.org/showthread.php?p=4053221#post4053221") is where I'll be posting any solutions I find.

---

### Post by Cushie on 2008-01-02
I have no Video card and am not running Xgl so maybe your problem is slightly different.  Anyway it has been resolved and been stable since.

---

### Post by mark.tj on 2008-01-23
I had the same problem and it seemed to be linked to a recent ubuntu update for something and my Nvidia Geforce 8500GT card. There are some [[COLOR="Blue"]new drivers[/COLOR]]("http://www.nvidia.co.uk/object/linux_eu.html") on the Nvidia site after installing the newest one following their instructions [[COLOR="Blue"]Here[/COLOR]]("http://uk.download.nvidia.com/XFree86/Linux-x86_64/169.07/README/index.html") it worked and my system seems a lot better than it was before.

NB I am on 64 bit not sure if that makes any difference. I tried following the ubuntu instructions but they did NOT help this time.

Mark.

---

