---
title: "Cannot install nvidia drivers"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by RodneyW on 2007-03-09
I cannot after some 5hrs of trying get the nvidia drivers installed. Ive download the newest ones from nvidia. when i try to do it i get msg   you appear to be running an x server etc. I have ctrl alt f1, logged in, then changed to root with sudo -s  then entered string   init 3   but still keep getting this msg. Please help because im not far off giving up on linux all together. In this time I could have built 3 computers from scratch and had them running on a network with win xp. I cant even get it to install drivers for one device before i can even use it without it looking like crap with low refresh rate.

---

### Post by Patrick K on 2007-03-09
Try this script. it's the easiest way I know of:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by rsambuca on 2007-03-09
These instructions are pretty easy to follow for using the envy script.

[[COLOR="Red"]Link[/COLOR]]("http://www.ubuntuforums.org/showpost.php?p=2254863&postcount=3")

---

### Post by igknighted on 2007-03-09
> **RodneyW said:**
> I cannot after some 5hrs of trying get the nvidia drivers installed. Ive download the newest ones from nvidia. when i try to do it i get msg   you appear to be running an x server etc. I have ctrl alt f1, logged in, then changed to root with sudo -s  then entered string   init 3   but still keep getting this msg. Please help because im not far off giving up on linux all together. In this time I could have built 3 computers from scratch and had them running on a network with win xp. I cant even get it to install drivers for one device before i can even use it without it looking like crap with low refresh rate.

The nvidia instructions are not for Ubuntu.  Ubuntu does not use standard init run levels (if you don't know what that means its OK, point is init3 in Ubuntu is different than most linux so those directions are no good).  Most software in Ubuntu that you will ever need is in the Ubuntu repositories.  You should almost never look online for programs/drivers to download.  Try typing these commands in a terminal to get the drivers you need installed:
```
sudo aptitude update
sudo aptitude install nvidia-glx
sudo nvidia-xconfig
```

the first command calls a program called aptitude to run a command called "update" which updates your software sources.  The second command tells aptitude to download and install "nvidia-glx", your drivers.  The last command configures your system to use the new drivers.  The sudo in front of each line gives admin rights for the command.  When you have typed (or copy/pasted) these commands into the terminal reboot and you should be all set.

edit: envy is a decent alternative too, but it almost borked my system so I cannot in good faith recommend it

---

### Post by RodneyW on 2007-03-09
sry none of these ways have worked

for the one above this, i get an err when it try to update could not connect, but firefox works and connects to net np and i can ping my laptop running xp in network. when i do the second command i get msg 0 packages upgraded etc, and when i run third command i getcommand not found. i have the driver saved to my desktop.

as for the 2 above about using the script, same thing i cannot connect to do it although i can follow links to the pages and read it. i downloaded it through firefox but that too still doesnt work.

---

### Post by igknighted on 2007-03-09
can you post the exact error you get when it says it cannot connect?

FWIW, since the other methods aren't working, replace the init3 command with these two:
```
sudo /etc/init.d/gdm stop
sudo killall Xorg
```

^^^note the X in Xorg MUST be capital.

---

### Post by Iceni on 2007-03-09
> **RodneyW said:**
> I cannot after some 5hrs of trying get the nvidia drivers installed. Ive download the newest ones from nvidia. when i try to do it i get msg   you appear to be running an x server etc. I have ctrl alt f1, logged in, then changed to root with sudo -s  then entered string   init 3   but still keep getting this msg. Please help because im not far off giving up on linux all together. In this time I could have built 3 computers from scratch and had them running on a network with win xp. I cant even get it to install drivers for one device before i can even use it without it looking like crap with low refresh rate.

This is rather easy. Just kill X, as the installer tells you. When you go ctlr+alt+f1 you just switch to another "window" ( I don't know what these are called:) ), but X is still running on your f7, usually. You have to completely quit X then run the install program from nvidia. Worked like a charm here.

---

### Post by igknighted on 2007-03-09
> **Iceni said:**
> This is rather easy. Just kill X, as the installer tells you. When you go ctlr+alt+f1 you just switch to another "window" ( I don't know what these are called:) ), but X is still running on your f7, usually. You have to completely quit X then run the install program from nvidia. Worked like a charm here.

Yes, but the issue is w/ most distro's init 3 kills X by default.  Not Ubuntu, we are an oddball here, hence a new linux user might not see this workaround instinctively

---

### Post by RodneyW on 2007-03-09
Ignighted:

this is the error for update, the first command i tried 

rodney@Rodney-linux:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy Release.gpg                               
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US         
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/universe Translation-en_US
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/universe Translation-en_US
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy Release     
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates Release
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/universe Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/universe Packages
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/universe Packages
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/universe Packages
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Reading package lists... Done
rodney@Rodney-linux:~$ 

as for the next ones you gave me, done from f1 with root:

sudo /etc/init.d/gdm stop
i get: command not found

as for sudo kilall Xorg
i get: no process killed

?????

---

### Post by RodneyW on 2007-03-09
so i log in as root from f1 or f7? and how do i kill all x?

---

### Post by igknighted on 2007-03-09
> **RodneyW said:**
> Ignighted:

this is the error for update, the first command i tried 

rodney@Rodney-linux:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy Release.gpg                               
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US         
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/universe Translation-en_US
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/universe Translation-en_US
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy Release     
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates Release
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/universe Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/universe Packages
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/universe Packages
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/universe Packages
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Reading package lists... Done
rodney@Rodney-linux:~$ 

as for the next ones you gave me, done from f1 with root:

sudo /etc/init.d/gdm stop
i get: command not found

as for sudo kilall Xorg
i get: no process killed

?????

Ok, 2 fixes.

1st, forget the gdm one.  I typo'd the second one (should be w/ 2 "l"s - sudo **killall** Xorg).  Do all of this at tty1 (F1), as F7 should disappear for the moment.

2nd, I think the australian server is having issues.  Try typing (from a normal terminal in F7) "gksudo gedit /etc/apt/sources.list".  This will open a text file in an editor, remove the "au." from the beginning of each server.  Also remove the # sign from any line with a server listed.

---

### Post by RodneyW on 2007-03-09
Tried removing the au. from the servers and saving it but it will still not update. ctrl alt f1 and logged into root and ran killalll comand and it went back into the GUI so it looked like it worked, ctrl alt f1 again into root and tried running setup but still getting x is running message

---

### Post by RodneyW on 2007-03-09
so am i absolutely going to need the update to work to install the vid driver or should that not matter?

---

### Post by igknighted on 2007-03-09
Are you using Ubuntu or Kubuntu?

try:
```
ping -c 5 http://archive.ubuntu.com
```

---

### Post by igknighted on 2007-03-09
> **RodneyW said:**
> so am i absolutely going to need the update to work to install the vid driver or should that not matter?

shouldn't matter... I guess you need to kill gdm after all.  Try hitting <tab> to auto complete everything.  Type 'sudo /e<tab>(should go to /etc/)in<tab>(should go to /etc/init.d/ or something like it)gd<tab>(hopefully /etc/init.d/gdm) stop'

---

### Post by RodneyW on 2007-03-09
ping returns:
ping: unknown host [http://archive.ubuntu.com](http://archive.ubuntu.com)

and i am using ubuntu, at least thats what it said when i d/l it and when it starts up
thx for helping too
im just about to leave it i think, ill d/l vista instead, atleast i know it will work

---

### Post by RodneyW on 2007-03-09
ok now im getting past running x problem with last command given but get another error. you do not appear to have libc header files installed on your system. please install etc etc. Forget it. Its just not worth it. Im going to stay with windows which works. thx for all your help anyway

---

### Post by Iceni on 2007-03-09
Don't do that:) I've tried vista, and you really don't want to go down that road. Actually vista was the biggest reason I made the switch. Now if I can only remember what I did to kill X completely. Maybe I restarted and chose something, I think there is a command line option in the grub menu.

Remember to write down where you put the installer if you are new like me:)

---

### Post by igknighted on 2007-03-09
> **RodneyW said:**
> ok now im getting past running x problem with last command given but get another error. you do not appear to have libc header files installed on your system. please install etc etc. Forget it. Its just not worth it. Im going to stay with windows which works. thx for all your help anyway

You probably need the kernel source... hmm, this might require the repo's.  You could try going to packages.ubuntu.com and getting the "build-essential" package and the "kernel-source-generic" package.

As for vista... I like it more than XP but right now there are almost no drivers for any devices, so g/l getting stuff set up.  NVIDIA graphics don't work last I checked cause NVIDIA doesn't have working drivers out yet (or at least by mid feb)

---

