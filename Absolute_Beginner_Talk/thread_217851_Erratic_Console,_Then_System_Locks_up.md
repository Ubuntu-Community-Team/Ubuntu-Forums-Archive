---
title: "Erratic Console, Then System Locks up"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by brn on 2006-07-17
I have a 2nd-hand Dell Latitude CPx laptop that came with Windows XP Professional.  I repartitioned the disk and first installed Breezy and now Dapper with GRUB. Both exhibit very erratic behavior although XP is always completely stable. Ubuntu might be stable for minutes or hours after login, then the cursor flies off-screen, and frequently random application or system utilities are invoked.  Very shortly, it just locks up and I have to unplug the battery and AC adapter to start over.  

Starting up in recovery mode everything looks fine.  When I enter 'init 5' (as root) the normal Ubuntu login screen appears and once logged in, the same behavior eventually occurs.  When I enter 'startx' from recovery mode I get what looks like the usual Gnome desktop except that it is very different.  The lists of Applications and System utilities are much shorter (e.g. Network Control is missing, I have to use wvdial to get online).  Even when I su to my non-privileged identity the background wallpaper presists (I had changed it when logged in normally) and I still have root privilege.  But in this configuration,the system is absolutely rock stable. I'm using it now.  Starting from 'init 5' the first message I see says "This program cannot start until you start the dbus system..."  I have tried typing 'dbus-launch' from recovery mode (although I have no idea what it does) but this makes no difference, I still get that message when switching with either startx or init 5 and when trying to shut down.  I'm baffled! ](*,)

---

### Post by givré on 2006-07-17
> **brn said:**
>  I repartitioned the disk and first installed Breezy and now Dapper with GRUB. 
You mean you install both breezy & dapper or you dist-upgrade to dapper?
> **brn said:**
> Both exhibit very erratic behavior although XP is always completely stable. Ubuntu might be stable for minutes or hours after login, then the cursor flies off-screen, and frequently random application or system utilities are invoked.  Very shortly, it just locks up and I have to unplug the battery and AC adapter to start over. 
I heard about a lot of problem, but never heard about that kind of things. 
> **brn said:**
>  When I enter 'init 5' (as root) 
why you wantedd to start as root. Just type 'init 2'.
> **brn said:**
>  When I enter 'startx' from recovery mode I get what looks like the usual Gnome desktop except that it is very different.  The lists of Applications and System utilities are much shorter (e.g. Network Control is missing, I have to use wvdial to get online).as far as i know startx directly to gnome never worked well. You should try to launch  a failsafe terminal session in GDM and exec 'gnome-session' if you want to have debuging information about what's happens > **brn said:**
>  Even when I su to my non-privileged identity the background wallpaper presists (I had changed it when logged in normally) and I still have root privilege.if you su from a terminal, i don't know how your right could change for the gnome-session 8)

---

### Post by brn on 2006-07-17
Quote:
_Originally Posted by brn_ 
*I repartitioned the disk and first installed Breezy and now Dapper with GRUB.*

> You mean you install both breezy & dapper or you dist-upgrade to dapper?

The Dapper CD installation didn't show an option to upgrade from Breezy.  It was a full installation.  Then I was advised to download 10 hours worth of upgrades, which I did. But the problem still persists.

> _Originally Posted by brn_  
*When I enter 'init 5' (as root)*

why you wantedd to start as root. Just type 'init 2'.

Recovery mode starts as root.  su-ing to non-privileged ID before issuing 'init 5' (or 'startx') makes no difference.  When the GUI comes up I am still root.

> as far as i know startx directly to gnome never worked well. You should try to launch a failsafe terminal session in GDM and exec 'gnome-session' if you want to have debuging information about what's happens

"Failsafe"?  Is that the same as what GRUB calls "recovery mode"?  Worth a try if it is.  If otherwise, how do I launch it?

Thanks!

---

### Post by givré on 2006-07-17
Okay i just check /etc/inittab since i didn't remenber what did init 5 (i usually use init 2) an it appears that runlevel 2-5 are all multiuser, so init 2 or init 4 will have the same effect. sorry for that 8) 
If you see difference between a total gnome session, and an not total one (start with startx) i will suggest you, like before. to run gnome from a terminal. In gdm, just type F10 > session and choose failsaife terminal. Then you can launch gnome with gnome-session.
Also, since it appears to be an hardware problem, i suggest you to post your configuration (with the mouse also).
Good luck.

---

### Post by brn on 2006-07-18
> Okay i just check /etc/inittab since i didn't remenber what did init 5 (i usually use init 2) an it appears that runlevel 2-5 are all multiuser, so init 2 or init 4 will have the same effect. sorry for that  


(From one of the nine Linux books I have collected;)  8) 
Run level  Description
    0      Halt shut down everything
    1      Single Usere
    2      Multiuser without NFS
    3      Full Multiuser (Default)
    5      X11
    6      Reboot

I think Run Level 4 is the same as 3.

> If you see difference between a total gnome session, and an not total one (start with startx) i will suggest you, like before. to run gnome from a terminal. In gdm, just type F10 > session and choose failsaife terminal. Then you can launch gnome with gnome-session.

I did this and arrived at my normal (erratic, crash-prone) user desktop.  It crashed just as I was logging into this forum.  I unplugged and restarted in recovery mode, went to runlevel 5, brought up the stable but restricted desktop and then entered 'init 2' from a terminal window.  This brought up the normal user loging with a window asking if I wanted to make this the default.  I declined.  Right now the console is erratic with the cursor jumping around but it has been 15 minutes now and it has not yet locked up.  

Hardware:  Dell Latitude CPx Laptop, BIOS dated 2003
           650 MHz Intel Pentium III
           256 MB RAM - 20 GB disk
           CD-RW
           Generic Optical Mouse (PS2) (Built-in touchpad works the same)
           Alternative USB "mini-mouse" works the same also
           2 PC Card slots (unused) 
           1 serial port (external USR 56K modem)
           1 parallel port 
           1 USB socket
           Windows XP Professional.  Last copywrite date = 20011

I would immediately suspect a hardware problem except that Win-XP exhibits none of the bizzare problems I hope I have described here.

Flakiness is getting worse, I'd better submit this right now.

Thanks again.

---

### Post by brn on 2006-07-19
Since recovery mode (runlevel 1), X11, and Windows XP are all very stable, I thought perhaps there was some sort of disconnect unique to this hardware and Gnome.  So I installed Xubuntu (Xfce) and it too is completely solid, at least for the past six hours.  I had never heard of Xfce before.  Although it is a lot less feature-laden than Gnome, so far I have found everything I need.  But just to complete the suite, I have also ordered Kubuntu and will try that when it arrives.

Thanks again. :D

---

