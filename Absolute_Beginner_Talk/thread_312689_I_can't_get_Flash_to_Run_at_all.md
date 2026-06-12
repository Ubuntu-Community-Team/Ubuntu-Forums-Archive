---
title: "I can't get Flash to Run at all"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by Hoso001 on 2006-12-04
I can't get any kind of flash to run in my browser, or anything. Everytime i try to run it, it won't let me, i get this think saying no plugin installed to handle it or somthing. I like playing alot of flash game online, particualar from shockwave.com. I am using the Konqueror Broswer. I have tried installing flash from the repo's with apt-get and synaptic, and i tried downloading the installer from the website, no dice. 


Thanks for any Comments or Help,

Hoso001


P.S. I a running 6.06 Kubuntu

---

### Post by tbroderick on 2006-12-04
Install flashplugin-nonfree from the repo. sudo apt-get install flashplugin-nonfree.

Open konqueror, click on Settings -> Configure Konqueror. Scroll down on the left side and select Plugins. Click the "Scan for new Plugins" button. You should be good to go.

---

### Post by jordanmthomas on 2006-12-04
Just in case, also make sure the package
```
konqueror-nsplugins
```
is installed so Konqueror will look for netscape plugins

---

### Post by foxmulder881 on 2006-12-04
You're not trying to install them on 64bit are you?

---

### Post by Hoso001 on 2006-12-05
No Dice, I am on a 32 Bit, It keeps telling me i need to install Flash/Shockwave. I have both of those installed, I am thinking the site, might not like the broswer Identification maybe? I am playing around with that.  
Thanks for the Help, 
maybe I can get it working,

Thanks,

Hoso001

---

### Post by Sef on 2006-12-05
1) Are you using Dapper or Edgy or other?

2) What flash have you installed?

3) Where did you install it from?

---

### Post by Hoso001 on 2006-12-05
I am using Dapper, I installed the flash from the repo's and from the site, i think i have been installing it in the wrong place..

I figured it out a bit, 

Whats the install path for Konqueror?
its like /usr/lib/???? 

thanks for the help,

Hoso001

---

### Post by Sef on 2006-12-05
> I am using Dapper, I installed the flash from the repo's and from the site, i think i have been installing it in the wrong place..

From the multiverse repository, it should have automatically installed into the right place.   Where did you have it installed to, if you did not use the default?

---

### Post by Hoso001 on 2006-12-05
I used the default location of it,
I installed with synaptic, then i reinstalled using the commandline..

sudo apt-get install flash, somthing there abouts

---

### Post by Sef on 2006-12-05
> sudo apt-get install flash, somthing there abouts

Did you type this:

```
kdesu aptitude install flashplayer-mozilla
```

To find out if it is different in Kubuntu, type this first:

kdesu aptitude search flashplayer

This is what I get when I use the search in Ubuntu:

> sef@jokat1:~$ sudo aptitude search flashplayer
p   flashplayer-mozilla             - Macromedia Flash Player   

Do the search and see what it says is the install.

Note: Use kdesu since you have Kubuntu.   Sometimes sudo, I have heard can cause problems.  So try reinstalling it with kdesu instead of sudo.

---

### Post by Hoso001 on 2006-12-05
I am not new new to linux, but to a debian distro, I am, I usually running SUSE, but i have never heard of this aptitude thing? When I try to run the command you give me, it prompts for my root, pass, i enter it and click ok, and this is the only output i get from the terminal??

```

hoso001@hoso001-laptop:~$ kdesu aptitude search flashplayer
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

---

### Post by Sef on 2006-12-05
aptitude is an advanced version of apt-get.  If you install with aptitude then later uninstall with aptitude, it will remove all the dependcies installed.  Apt-get will not remove all the dependencies.  

Try this then from Konsole:

```
sudo aptitude search flashplayer
```

---

### Post by Hoso001 on 2006-12-05
Well, I guess Aptitude dosen't like me very much,

Still no output, using aptitude

```

hoso001@hoso001-laptop:~$ sudo aptitude search flashplayer
Password:
hoso001@hoso001-laptop:~$

```

Thanks for all this help Sef,

Hoso001

---

### Post by Hoso001 on 2006-12-05
Out of pure morbid curiosity, maybe the site is saying i don't have flash install because of a javascript error?? 

I noticed a werid icon on my lower right screen in konqueror, this came up..
```

http://ndc.shockwave.com/a/js/activex.vbs: SyntaxError: Parse error at line 2

```

would that make it say i don't have flash installed??

Thanks,

Hoso001

---

