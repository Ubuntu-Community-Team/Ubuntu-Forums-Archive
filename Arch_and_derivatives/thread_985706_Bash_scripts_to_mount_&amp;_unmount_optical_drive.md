---
title: "Bash scripts to mount &amp; unmount optical drive?"
date: 2008-11-17
forum: Arch and derivatives
---

### Post by handy on 2008-11-17
I'm running xfce on Arch with the HAL daemon being called in rc.conf.

I can access media on my optical drive (DVD's or CD's) through the desktop icon that appears after HAL has recognised the drive, & VLC automatically does its thing also.

The reason I'm posting is that I found a great DOpus clone yesterday called [***_Worker_***]("http://www.boomerangsworld.de/cms/worker/index?lang=en"), which I have been configuring (fonts, colours, partitions & layout at this point).

A problem I have is being able to access the optical drive via Worker.  

The way it is on my system, with HAL handling it, the first line below appears after HAL mounts the media, which basically makes the two lines below it useless:

/media/<title of disk>
/media/cd
/media/dvd 

I have tried using /media/dvd (or cd), these don't work for the reason stated above & /dev/sd0 doesn't work.

So, do I have to turn off HAL, uncomment the lines in fstab & use mount?

If there was little bash script, that would do the job for me as *Worker* will accept a script or a command string.

All input welcome.

Thanks. :-)

---

### Post by mips on 2008-11-18
> **handy said:**
> 
The reason I'm posting is that I found a great DOpus clone yesterday called [***_Worker_***]("http://www.boomerangsworld.de/cms/worker/index?lang=en"), which I have been configuring (fonts, colours, partitions & layout at this point).

Very nice find! DOpus was the dogs you know what on the Amiga, the memories :)

---

### Post by handy on 2008-11-18
> **mips said:**
> Very nice find! DOpus was the dogs you know what on the Amiga, the memories :)

Yes, Jonathon Potter was my hero!

I always like version 4 of DOpus best too. :-)

---

### Post by handy on 2008-11-18
I removed hal from the rc.conf daemons & also the comments from the lines in fstab.

I've turned off the need for a password when mounting the optical drive in the sudoers file with the following:

[B][I]handy   ALL = NOPASSWD: /sbin/umount /CDROM,\
                /sbin/mount -o nosuid\,nodev /dev/cd0a /CDROM[/I][/B]

Now when I enter *mount /mnt/dvd* in the Terminal the media is mounted, I can then use the button I have configured with */mnt/dvd* to list the root contents of the drive in the active panel of Worker.

The last part of this problem which I'm trying to understand, is how to get Worker to handle the *mount /mnt/dvd* command?

---

### Post by handy on 2008-11-18
An easy solution is to make a couple of simple executable scripts & call them from buttons Mount & uMount, using the Add Command / Own Command options.

The simple mount script without the need for sudo:

[I]#!/bin/sh
# ~/mountdvd.sh mounts the optical drive 
# via the Mount button in Worker.

cd /
mount /mnt/dvd[/I]

I think that there may probably be a way to use a variable so that the the same 2 scripts can be used for any mountable devices?

---

### Post by handy on 2008-11-19
I found out that *(u)mount {F}* works for whatever device you have selected.

I've attached a picture of the beast :-)

***[Edit:]** I just looked at the screenshot & noticed that the Mount button did not have the dog ear indicating that there is a RMB option under it, which in this case is supposed to be the uMount button, which I forgot to move in my reshuffling of buttons. :)*

---

### Post by handy on 2008-11-19
Interestingly, a new version of emelFM2 was released on 18-11-08, it is somewhat more polished than it was, & now has an advanced configuration option, which makes it easier for an emelFM2 beginer to go through the setup with the advanced options turned off.

That said, I will be deleting the excellent emelFM2 from my system due to having found Worker, which gives me so much more room for customisation. Worker has the ability to accept bash scripts, has a huge number of built in commands, (many I will never need to tie to a mouse button), has a large range of compression algorithms built in, the ability to rip from CD to ogg, wav, mp3 & flaac, also bulk conversion of images such as .jpg to png, the list goes on & on. It has the ability to have many panes of buttons that can have both left & right mouse button configurations applied to them, you cycle through the panes by clicking on Worker's footer bar.  All of this & it is light, fast & free as well.

The Amiga dirutil DOpus was the inspiration for Worker.  I used to run my Amiga's from DOpus, & I expect that now Worker will be my distro' control centre from now on (I think it works in Leopard too!).

Now I'm wondering, do I need a WM on top of X to use Worker? ;-)

---

### Post by K.Mandla on 2008-11-20
Is this helpful at all?
```
#!/bin/sh
mtab_sda1="$(cat /etc/mtab | grep sda1 )"
if [ -z "$mtab_sda1" ]; then
mount /dev/sda1
else
umount /dev/sda1
fi
```
You'd have to change it to use your optical drive mounts, but it could work.

Some gob posted that on a blog somewhere. ;)

---

### Post by handy on 2008-11-20
Thanks for that K.Mandla. :-)

I found I can use ***(u)mount {F}*** on any selected device. So, my current requirements in that regard was met without the need for any scripts.

It is still possible that the code you provided may find a use sometime in the future though?
 
I know very little about bash scripting, though using Worker is causing me to extend my knowledge some, which is always a good thing. :)

---

### Post by K.Mandla on 2008-11-22
> **handy said:**
> It is still possible that the code you provided may find a use sometime in the future though?
I used it for a little while as a right-click USB mount in Openbox. That was before I adopted emelFM2, which has mount options in the command panel, and that's where I needed them most anyway. ;)

---

### Post by handy on 2008-11-23
> **K.Mandla said:**
> I used it for a little while as a right-click USB mount in Openbox. That was before I adopted emelFM2, which has mount options in the command panel, and that's where I needed them most anyway. ;)

Have you had a look at Worker?

It may woo you away from emelFM2 :-)  as it is far more configurable/customisable, it is fast & light & only requires the X window system.

---

