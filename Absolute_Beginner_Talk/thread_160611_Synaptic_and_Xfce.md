---
title: "Synaptic and Xfce"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by JeffBlouin on 2006-04-15
Im new to Xfce Wm and I have some question: Im using Xubuntu on dapper flight 6

1)  Is there an utility to mount hard drive and if not, how do I do it so xubuntu do it on boot-up
2)  When i try to modify the repositories I get this: 

>  The repository information has changed. You have to click on the "Reload" button for your changes to take effect 

I click reload but I still cant get to the repo list...
 I looking to install mplayer but dont find it in synaptic...

Beside this a really enjoy xubuntu very fast on my slow computer...

Thanks

---

### Post by threegremlins on 2006-04-15
I was also looking for something like xffstab to mount the other partitions or drives, since I change the other partitions to rw,noauto,user, in fstab so I can open them without being root. They should be loaded by default anyway but maybe your machine sets up different. 

I use the mount command
eg
mount -t auto /dev/hdb /media/cdrom  for the cd drive
mount -t msdos /dev/fd0 /media/floppy0 for the floppy(yes i still have one)
mount -t vfat /dev/hdc3 /media/hdc3  for windows 98

and umount to unmount them. there's probably a repository you can add that has this program, didn't have much luck adding repositiories from other ubuntu distro's. I know breezy had xffstab, perhaps you can find it on the web and download it. then do this

sudo dpkg --install thepackage.0-1-1.0.deb

if it asks for other packages see if you can install them from synaptic then run the command again. I do this with blender, the version for breezy and dapper won't work on my box so I have to install the one from hoary. then lock the version in synaptic or I'm constantly asked to upgrade it.
Look at that got off topic, well hope this helps.

---

### Post by aysiu on 2006-04-15
How are you trying to modify the repositories?

I'd advise this method:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

... well, using Dapper instead of Hoary or Breezy, of course.

Also, for mounting stuff in XFCE, I'd advise using *gnome-volume-manager*. ```
sudo apt-get update
sudo apt-get install gnome-volume-manager
``` Alt-F2 ```
gnome-volume-manager
``` Save your session on logout.

---

### Post by threegremlins on 2006-04-16
I love it when some one else comes to help that has more experience than me.
That's a good idea hadn't thought of installing gnome-volume-manager.
I switched to xfce because it runs faster than gnome. When I had ubuntu running I was using windowmaker as a desktop for the reason I liked the look of it and prgrams like openoffice started faster. What I wondered running xfce or xubuntu is if and I already have installed some gnome apps will it start slowing down again. Another question I have is I found xffm4(it contains xffstab4), won't install because it requires,

Depends: libxfce4mcs-client-2  but it is not installable

there are a few more like this but I only looked for this one in synaptic to install
and I find libxfce4mcs-client-3 is installed. Now this has happened to me before where I tried installing a package but it keeps asking for older libraries and quits, how do you make an install package or program accept the new or upgraded libraries

---

### Post by aysiu on 2006-04-16
[QUOTE=threegremlins]
Depends: libxfce4mcs-client-2  but it is not installable[/QUOTE] When this happens, it generally means you have conflicting repositories. Are you mixing Breezy and Dapper ones? Do you have any Debian repositories in your /etc/apt/sources.list file?

---

### Post by threegremlins on 2006-04-16
hummm, I downloaded and installed the xubuntu install cd so I wouldn't have to use the live cd and do a server install, still I did the disk install with a connection to the server the if only to have upgradaded packages available. The only repositories are the ones for drake it set up with. Which leads me to another question concerning another deb package I downloaded to set up but won't worry about that now. 
jeffblouin are you still with us I'm afraid I hijacked your thread is any of this helping.

---

### Post by JeffBlouin on 2006-05-02
Thanks for all the answers...

         When I install new Apps from synaptic, some show automatically in the XFCE menu but others are not there... Is there a way to put them in a menu ex: Putting a link to gnome volume manager in System menu


Thanks

---

### Post by JeffBlouin on 2006-05-02
I installed the gnome-volume-manager but when i try to run it with ALT-F2 nothing happens

...

---

