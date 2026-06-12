---
title: "I need help!!"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by jex54321 on 2007-12-21
well...i just installed linux not to long ago

I have a graphics card (Nvidia w/ 64mb)

A couple games are not working, and all of a sudden, my screen enlarged, meaning...my taskbar is on the bottom, and i have to put my mouse at the top of the screen, to get to the applications bar

And, another problem, is i cannot "open" pidgin messenger.  i can open it, it logs me in, and i cant see my buddy  list


also, it wiped my whole hd, so i cannot install xp, because wine will close when i do

I do not have the disk that xp came with, i have a burnt copy.


--edit--

when i do move my screen around, all my task bars, and the application bar turns white, and does not show any buttons, and it also makes it where i see these lines, that are just like a distorted picture of my desktop =\


i do not know anything about  linux, so, please someone help (also, when i tried to adjust   my screen resolution, it gives me an error saying i cant

---

### Post by satx on 2007-12-21
Install Envy- it will fix your video problems.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by rickycodie on 2007-12-21
you can still install windows if you want to, it will not interfere with wine. you just ned to partition your disk.

---

### Post by jex54321 on 2007-12-21
i forgot to mention, im using i386

um...the version of envy are only for x86 i think

---

### Post by perlluver on 2007-12-21
> **jex54321 said:**
> i forgot to mention, im using i386

um...the version of envy are only for x86 i think

Those are the same i386 i486 and i686, are x86.  x64 is 64 bit I believe.

---

### Post by zabien1970 on 2007-12-21
The '86' part is just a labeling for the type of architecture, ie. 286, 386, 486,  x86 means it should work since the x is just replacing the first number

---

### Post by jex54321 on 2007-12-21
so..envy will fix all those problems?

---

### Post by DrMega on 2007-12-21
> **jex54321 said:**
> i forgot to mention, im using i386

um...the version of envy are only for x86 i think

i386 and x86 generally refer to the same thing. It means the 80x86 series of processors by Intel, and other chips that use the same instruction set. In layman's terms this means Pentiums, Celerons, AMD Athlons (pre the 64 bit version) etc.

--Edit--

In the time it took me to write my response, numerous others all said the same thing, so sorry for the duplication :)

---

### Post by jex54321 on 2007-12-21
i downloaded envy, and now its saying (when i push install) stuff about malicious,i pushed   the yes button so i could download it

now it says, could not download, check internet connection

--edit--


whats that terminal command for installation?

apt-install

or something like that? please post the code

--edit again--

i found the code: sudo apt-get install 


but, it gave me the same error as the package installer

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

how do i fix that?

---

### Post by zabien1970 on 2007-12-21
Did you make sure your repositories are enabled? there is a notice at the bottom of the envy page

---

### Post by ReverendJ1 on 2007-12-21
Pidgin will default to just an icon in your system tray. Open it and look at the system tray by the clock. There should be a new icon that looks like a speech bubble and a green circle. Right-click on that and then hit 'show buddy list'.

Is the internet working okay on that machine? If not, that would be why envy isn't working.

Are you trying to install XP alongside of Ubuntu, so that when you boot your machine, you can choose whether to run Ubuntu or Windows? If this is the case, you will have to install Windows first, because it will write over the boot-loader in Ubuntu, and not let you load Ubuntu. Windows doesn't play nice with other operating systems. :-)

If you just need to try and run a Windows program in Ubuntu then you can use Wine. It does not require you to have/use the Windows cd.

---

### Post by ReverendJ1 on 2007-12-21
This error:
```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```
is usually caused when you have another package manager program running. Close 'Add/Remove Programs' and Synaptic if you have either one open and try again.

---

