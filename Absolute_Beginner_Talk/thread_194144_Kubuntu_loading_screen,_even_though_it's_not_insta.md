---
title: "Kubuntu loading screen, even though it's not installed"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-06-11
i was trying to shut down my pc, but at the shut down screen (the one where it says ubuntu and it's reflected and all of the processes are being described on the bottom) after "shuting down LVM Volume groups  ok" it said; "will now halt" and then it just hanged. 

so i decided to manually shut down the pc, but when i turned it back on, instead of the loading screen with the relected ubuntu, i get the kubuntu version of that (look for the first attachment on my fourth post to see what this looks like).  after that everything loads fine (it loads into gnome; again look at the second attachment in the fourth post to see what this looks like)

OOPS! forgot to mention one major thing:  prior to all of this, i did a ```
sudo aptitude update && sudo aptitude install kubuntu-desktop
``` i logged out, went into KDE (did **NOT** choose "make KDE default session") then i went back to gnome, and did ```
sudo aptitude update && sudo aptitude remove kubuntu-desktop
``` 
i thought it would remove everything, but it didn't since i looked up any apps that started with a K in synaptic, so i uninstalled all of the remaining ones (at least i think that's all of them...), but I still have this one slight problem...:-k

---

### Post by user1397 on 2006-06-11
i'm sorry but i really need to bump this!!!

---

### Post by confused57 on 2006-06-11
I'm not sure how to solve your problem and you've probably already tried:

sudo dpkg-reconfigure gdm

sudo nano /etc/X11/default-display-manager

Wonder if kdm is still installed?  Sorry I can't really help you find a solution.

There may be something in aysiu's HowTo:

[http://www.ubuntuforums.org/showthread.php?t=96048](http://www.ubuntuforums.org/showthread.php?t=96048)

---

### Post by user1397 on 2006-06-11
[quote=confused57]I'm not sure how to solve your problem and you've probably already tried:

sudo dpkg-reconfigure gdm

sudo nano /etc/X11/default-display-manager

Wonder if kdm is still installed?  Sorry I can't really help you find a solution.

There may be something in aysiu's HowTo:

[http://www.ubuntuforums.org/showthread.php?t=96048]("http://www.ubuntuforums.org/showthread.php?t=96048")[/quote]
i only have gdm installed, not kdm.  tried all of your suggestions, so i'll reboot and see what happens. thanks.

---

### Post by user1397 on 2006-06-11
If this can make things clearer, the first screenshot is what it looks like when i boot up, then it goes to the next screen immediately.

---

### Post by user1397 on 2006-06-12
just gotta do it, BUMP!

you know it's really mind-boggling (this issue of mine i mean) ;)

---

### Post by confused57 on 2006-06-12
I thought maybe you found a solution, maybe you could run aysiu's kubuntu-desktop removal or find the package that's not removed:

[http://psychocats.net/ubuntu/puregnome.php](http://psychocats.net/ubuntu/puregnome.php)

---

### Post by user1397 on 2006-06-12
i don't think it's a kdm problem.  i have decided to reinstall the kubuntu-desktop package with aptitude, but gdm is still the default, so this shouldn't be happening.  is that kubuntu loading screen even related to kdm?

---

### Post by user1397 on 2006-06-13
A Really Friendly Bump!

---

### Post by learning on 2006-06-13
I have the same "problem" on one of my computers, because I did the same thing.

Would love to see a fix, besides re-installing.

---

### Post by ubnoobie on 2006-06-13
[QUOTE=erik1397]If this can make things clearer, the first screenshot is what it looks like when i boot up, then it goes to the next screen immediately.[/QUOTE]
the initial boot graphic (after grub and before display manager) is usplash. the default one is the ubuntu logo and there are extra ones for xubuntu, kubuntu, and edubuntu. the kubuntu one is in the kubuntu-artwork-usplash package.

---

### Post by user1397 on 2006-06-13
[quote=learning]I have the same "problem" on one of my computers, because I did the same thing.

Would love to see a fix, besides re-installing.[/quote]yes the word "problem" should be quoted, because it's not really an issue, it's just an odd situation

---

### Post by uzi09 on 2006-06-13
i think it's just a bug or something.

i installed kde using apt-get and then removed it again on breezy and it left the start up screen the same.

i did an xfce install with my dapper, but this time using APTITUDE, but when i removed it, a lot of the things remained. like the original background shows up blue when originally it should have been brown when gdm is starting up. i think it's working now randomly after an update.

---

### Post by user1397 on 2006-06-15
yea i think that its definitely a bug.  even when i uninstalled kubuntu-desktop, kdm, and kubuntu-artwork-usplash, it still appeared.  Oh well, it still works.

---

### Post by YoungGods on 2006-06-16
This may help [http://www.ubuntuforums.org/showpost.php?p=1104903&postcount=6]("http://www.ubuntuforums.org/showpost.php?p=1104903&postcount=6")

---

### Post by raptros-v76 on 2006-06-16
the booting screen problem is with usplash. to set it back to the default, look in /usr/lib/usplash. in there are kuubuntu-splash.so, usplash-default, and usplash-artwork.so.
the latter is a link to one of the two former. to fix the problem:

sudo ln -sf /usr/lib/usplash/usplash-default.so /usr/lib/usplash/usplash-artwork.so
and
sudo dpkg-reconfigure linux-image-$(uname -r)

that should bring it back to the normal usplash screen

---

### Post by raptros-v76 on 2006-06-16
actually, the link of YoungGods' is probably clearer and better

---

### Post by nitricacid on 2006-06-16
If you really don't want that and since i can't remember the file that it's placed in so you can change the splash screen back to the 'ubuntu logo starting app screen' just open a terminal and type ```
sudo gedit /boot/grub/menu.lst
``` and remove the word 'splash' from these lines 
```
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hda1 ro quiet splash
```
And
```
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
```

This will kill the start up and shutdown splash screen, which in my opinion makes linux boot faster anyway.

---

### Post by muep on 2006-06-16
I think that the bootsplash has something to do with the kernel. At one time I had both Kubuntu and Ubuntu installed and depending on which kernel was selected on boot, the splash would be different. Some kernels were installed after Kubuntu install and the others before it. The older kernels had Ubuntu splash.

Try booting with an older kernel image? You probably have more than one.

---

### Post by raptros-v76 on 2006-06-16
no. the problem is from which usplash art library is used. follow YoungGods's link. that will tell you exactly how to fix it.

---

### Post by user1397 on 2006-06-16
[quote=YoungGods]This may help [http://www.ubuntuforums.org/showpost.php?p=1104903&postcount=6]("http://www.ubuntuforums.org/showpost.php?p=1104903&postcount=6")[/quote]yep, thank you YoungGods, this link fixed my problem.  As to nitricacid's suggestion, i actually like the splash startup/shutdown screens, I HATE the command-line versions of those.  Good to know though, nitricacid.

---

### Post by upendran on 2006-06-20
My system boots with Kubuntu splash screen, login with Xubuntu screen, get a Ubuntu splash screen to startup gnome and shut down with Ubuntu screen!:lol:

I installed Ubuntu, added KDE and added Kubuntu and Xubuntu to experiment with everything and ended up with a cocktail!

---

### Post by user1397 on 2006-06-20
[quote=upendran]My system boots with Kubuntu splash screen, login with Xubuntu screen, get a Ubuntu splash screen to startup gnome and shut down with Ubuntu screen!:lol:

I installed Ubuntu, added KDE and added Kubuntu and Xubuntu to experiment with everything and ended up with a cocktail![/quote]well you should first try pasting this in a terminal (applications > accessories > terminal): ```
 sudo dpkg-reconfigure gdm
``` choose gdm as the default.  if you follow this thread, it might fix your problem: ([http://www.ubuntuforums.org/showpost...03&postcount=6)]("http://www.ubuntuforums.org/showpost.php?p=1104903&postcount=6")

---

### Post by dvarsam on 2006-06-21
Maybe it is too late to suggest things now, since you seem to have fixed your problem, but what if you had performed the following:

```
sudo apt-get install ubuntu-desktop
```

And if it is already installed, first remove it with:

```
sudo apt-get remove ubuntu-desktop
```

And then go ahead & re-install it...?

Probably the above could bring back the original settings...

It was just an idea...

Good Luck!

---

### Post by mycoted on 2006-07-02
For those getting a different "login screen", try changing the  default in;

System-->Administration-->Login Window

I know when I tried installing xubuntu and kubuntu (with aptitude) and removing them again, I was left with the xubuntu login screen as the default.  I just changed the default back, and set the colour to #2C160A (brown) from the blue, and all worked nicely.

---

### Post by user1397 on 2006-07-02
[quote=mycoted]For those getting a different "login screen", try changing the  default in;

System-->Administration-->Login Window

I know when I tried installing xubuntu and kubuntu (with aptitude) and removing them again, I was left with the xubuntu login screen as the default.  I just changed the default back, and set the colour to #2C160A (brown) from the blue, and all worked nicely.[/quote]thanks for the info, but the real default brown ubuntu color is #2B0600.

---

### Post by recover89 on 2006-07-04
A simpler solution would be to mark kubuntu-artwork-usplash for 'COMPLETE removal'.

---

### Post by user1397 on 2006-07-04
[quote=recover89]A simpler solution would be to mark kubuntu-artwork-usplash for 'COMPLETE removal'.[/quote]actually, that does not solve the problem.  you would have to follow these instructions:
[B]sudo update-alternatives --config usplash-artwork.so
[/B]
Choose usplash-default.so for the brown Ubuntu splash.

Then, run **sudo dpkg-reconfigure linux-image-`uname -r`**

---

