---
title: "Ubuntu freezes randomly and often"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by fca_neo on 2006-12-21
I'm pretty new to Ubuntu/Linux. I installed a fresh copy of ubuntu(6.10) 4 days ago and I love it.

I kept my Windows XP installed (dual boot). But I don't think I''ll ever need it again.

Well, ever again until now. My Ubuntu has been freezing pretty much randomly today, and it is extremely anoying. So anoying that I'm writing this post from windows.](*,) 

**The symptoms:**
While I'm doing pretty standard things such as reading PDFs (default gnome reader) or surfing the web (firefox) everything freezes (exept for the mouse).

The only way I can recover is to restart using the reset button. ctr+alt+Backspace doesn't work.

This happens every 5 to 30 minutes. And doesn't seem to follow any pattern.

I tried to search for this problem and did not get any solution that worked or that I understand.

**My guess:**
something about drivers or something about Firefox (like java, but i don't think so).

**The things I have installed on Ubuntu **(at least those that I remember):
[LIST]
[*]nVidia drivers (I think they work, I see the nvidia screen at startup)
[*]Beryl + Emerald +... (this stuf is completely amazing and works remarquably fast)
[*]mp3 and other media plugins (work fine)
[*]Flash 9 (working fine)
[*]Automatix
[*]Gambas
[*]some gnome themes and icons
[*]many firefox addons
[*]Acrobat Reader
[*]Azureus (wich worked fine for one day, but now it closes a few seconds after I open it)
[*]SMB (sharing files and printer with other windows and Linux computers well)
[/LIST]

**My system:**
[LIST]
[*]Atlhon Thunderbird 1GHz
[*]640 MB Ram
[*]Linux partition 5GB
[*]swap 1GB (some info on the swap size would be welcome also)
[*]nVidia GeForce 2 Mx (I get 3D acceleration and everything)
[/LIST]

Please help me solve this problem. Today I got very frustrated and was willing to give up Ubuntu. But don't worry, I won't let M$ win so easily.

Thanks

---

### Post by bigken on 2006-12-21
lockups like this are usually down bad to video drivers in a terminal run 
sudo dpkg-reconfigure xserver-xorg and select nv or vesa as your video driver and see if the problem persists



swap should be twice the size of your ram ie 512mb = 1gig of swap

---

### Post by fca_neo on 2006-12-23
I could not solve this problem using xorg configuration. Now I use my XLG session and the problem is gone, which is good. But I don't know why is that or if it is a good thing to do?
Thanks anyway for your reply. I really appreciate the help.

---

### Post by trixxz on 2006-12-23
I think we're both having the same issue. I'm not sure what it is, I'll try to load firefox, or just open a folder and the system completely locks up. If this is due to drivers, then I'll add that I did use the  ATI installer script from this post :

[http://ubuntuforums.org/showthread.php?t=235145&page=11](http://ubuntuforums.org/showthread.php?t=235145&page=11) (post #109) 

his instructions mention that edgy doesn't support compositing, but I disabled it in xorg.conf. However, once I crashed it said that it was due to the compositing...could be because I attempted to use transparency..

Anyways, I'm out of ideas for now, I hope I don't crash again :X

/edit

One of the times it crashed, firefox and cupsd were at 100% cpu, after killing firefox, it couldn't be restarted, and killing cupsd didn't work, even as root.

---

### Post by fca_neo on 2006-12-23
While using an XGL session that I created using the guide for installing beryl i don't get any freeze ups, perhaps you could try the same. The guide is here [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL)

I'm really really new to this son don't take my word for it.

---

### Post by saphil on 2007-01-21
This has started happening to me when I attempt to open a pdf through firefox... only since the last firefox update came down.
I am using edgy with firefox 
2.0.0.1

---

### Post by Shatrat on 2007-01-21
@saphil
Firefox is locking you up so bad that ctrl alt backspace doesn't work?
I think it might be an unrelated problem.
In my experience working with large PDFs is laggy and unresponsive in any viewer.  
PDFs are for printing in my opinion, not suited for much else.

---

### Post by sailor2001 on 2007-01-21
what size is your ram? I think all your problems will go away if you increase ram to 1 gig.....i;ve had the same problems with a 512 ram..... now no more problems......

---

### Post by saphil on 2007-01-21
This may be unrelated, true.  Yes Firefox locks up entire GUI.  cannot escape it.  I am sure that more ram would help (have 3/4Gb) 
I am thinking about deleting acroread, and going with ghostview, which works better.  Apt cannot find acroread to delete it.  Grrrrr.

Sometimes, what a update breaks, the next update fixes, so I might could just wait a couple of months...;)

---

### Post by RetepNamenots on 2007-03-25
Firefox locks up the computer for me, Epithany too. So at the moment I'm using Konqueror but it's not the best...

With firefox, the mouse also locks up..

---

### Post by ramzai on 2007-03-25
Execute

free

and see if you have enough swap/memory

---

### Post by TURNER on 2007-03-25
I am also experiencing very similar issues, and I am pretty sure it isn't down to drivers...

My issues are pretty similar to the original post, I am also pretty new to linux and my troubles started as I installed Beryl...

```
Here is a report from free...
             total       used       free     shared    buffers     cached
Mem:        256160     252164       3996          0      12844      69536
-/+ buffers/cache:     169784      86376
Swap:            0          0          0
```

I also have "conky" installed which specifies that 160mb of my 256mb available is consistently in use, even when I am not performing any actions!!

Could this be Beryl related, is Beryl using too many system resources, for the record this is also a problem whilst in a normal (non xgl session).

I am pretty stumped and also a bit pissed with all this, although I promise not to go back across to the dark side...

A recent ubuntu update also coincides with this behaviour btw...:-\" :-\" :-\" :-\" :-\"  

As mentioned, I only have 256mb RAM, this will obviously affect system performance, but ubuntu WAS working quite happily until Beryl came into the picture...[-( 

Any assistance will be rewarded with a giant bag of smarties :biggrin:

---

### Post by ramzai on 2007-03-25
As you can see on the free output, you don't have swap, so you need to set it up in order to make system stable.

First look at /etc/fstab (`more /etc/fstab`), pretty sure it was set up during install but for somewhat reason is not functional any longer
if you see line with swap in it, try `sudo swapon -a` (that means turn on all the swap partitions)
an error may appear, then we'll need to reformat swap area. look at the line in /etc/fstab with swap, smth like
/dev/sda8       none    swap    sw      0       0
`sudo mkswap /dev/sda8`  - recreate swap area (CHANGE /dev/sda8 to YOUR actual partition)
if ok, `sudo swapon -a`
look at the `free` to see if swap works ok.

NOTE: if any of the step fails, don't proceed to the next one, just post the output here.

---

### Post by TURNER on 2007-03-25
ok, I attempted to switch swop on, and here's what I got:

```
turner@turner-desktop:~$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3 -- converted during upgrade to edgy
UUID=5ad56dbb-72c8-4bf3-befb-30c9c918cfe4 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda6 -- converted during upgrade to edgy
UUID=edd67c10-9483-4c63-acdf-c6acc568b2cd none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
none /proc/bus/usb usbfs auto,devmode=0666 0 0

```



I then attempted the second part and heres what it kicked up

```
turner@turner-desktop:~$ sudo swapon -a
Password:
swapon: /dev/disk/by-uuid/edd67c10-9483-4c63-acdf-c6acc568b2cd: Invalid argument
turner@turner-desktop:~$ 
```


next:

```

turner@turner-desktop:~$ sudo mkswap /dev/hda6
Setting up swapspace version 1, size = 230268 kB
no label, UUID=ad3299a9-16a9-44cb-95c4-934e9cf3ed7e
turner@turner-desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:        256160     252024       4136          0        556      46644
-/+ buffers/cache:     204824      51336
Swap:            0          0          0
turner@turner-desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:        256160     252144       4016          0        688      46660
-/+ buffers/cache:     204796      51364
Swap:            0          0          0
turner@turner-desktop:~$
```

---

### Post by ramzai on 2007-03-25
Replace 

# /dev/hda6 -- converted during upgrade to edgy
UUID=edd67c10-9483-4c63-acdf-c6acc568b2cd none swap sw 0 0

with

/dev/hda6 none swap sw 0 0

(to edit /etc/fstab use `gksudo gedit /etc/fstab`)

after you have saved file, do `sudo swapon -a`
after that, `free` should show you something in the swap row and you're ok.

---

### Post by saphil on 2007-03-25
I just deleted acroread entirely.  Now problem is gone.  Ha ha.

---

### Post by TURNER on 2007-03-26
> after you have saved file, do `sudo swapon -a`
after that, `free` should show you something in the swap row and you're ok.

Your a genius, many thanks!  I now have swap mem available.

For everyone else in this thread, perhaps give this a whirl; apparently by adding a simple tweak to your “/etc/hosts” file Gnome will run quicker:

[[COLOR=Blue]Performance tip for Edgy and Feisty users[/COLOR]]("http://beuno.com.ar/?p=4")

I tried this, and my sys does seem quicker, although it could also be the addition of the swap file, see above.:confused:

---

