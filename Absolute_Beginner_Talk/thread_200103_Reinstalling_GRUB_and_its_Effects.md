---
title: "Reinstalling GRUB and its Effects"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-06-19
Here's the situation:  I had freshly installed dapper, when I decided to install fedora core 5 on a different partition.  I installed GRUB with the fedora installer, so the GRUB that was installed with dapper was overwritten with the new one.  I was able to add my ubuntu entries to the new grub, so I can boot into either fedora or ubuntu, so that's not a problem.  The problem is, how could I reinstall GRUB using the ubuntu cd? and which one would I use, the desktop cd or the alternate cd?  

Also, would reinstalling GRUB with the ubuntu cd affect my dapper and/or my fedora installations?

---

### Post by glotz on 2006-06-19
Uhm, why would you like to reinstall grub in the first place? Maybe it could be done via a package manager. I'd backup /boot/grub/menu.lst

---

### Post by user1397 on 2006-06-19
[quote=glotz]Uhm, why would you like to reinstall grub in the first place? Maybe it could be done via a package manager. I'd backup /boot/grub/menu.lst[/quote]i would like to reinstall it, because the new one was installed with fedora, and therefore i can only edit it with fedora (which is **NOT** my primary OS) and if fedora breaks, who knows if i'll be able to boot into anything?  (fedora is easier to break than ubuntu or so i've heard, plus im doing experimentation on it, so all the more reason)

i did find it in synaptic, and now i'm wondering if i just uninstall it/reinstall it, will it be back as it was before?

thanks for the backing up tip

---

### Post by glotz on 2006-06-19
I'm not familiar with a 2 Linux distro setup. What kind of partitioning scheme do you have? Do you actually have 2 separate /boot folders or partitions? How do you edit grub? (Besides sudo nano /boot/grub/menu.lst)

---

### Post by user1397 on 2006-06-19
[quote=glotz]I'm not familiar with a 2 Linux distro setup. What kind of partitioning scheme do you have? Do you actually have 2 separate /boot folders or partitions? How do you edit grub? (Besides sudo nano /boot/grub/menu.lst)[/quote]
here's my partitioning scheme:

partition 1: ubuntu, /, ext3, 15GB
partition 2: ubuntu, /home, ext3, 125GB
partition 3: fedora, /, ext3, 10GB
partition 4: swap, 1GB

to edit grub, i have to boot into fedora, and in the command line I type: ```
su -
gedit /boot/grub/menu.lst
```i hate being forced to go to fedora to change my very important grub settings, since its not my primary os

---

### Post by glotz on 2006-06-19
So that sounds like you have /boot folders on your partitions 1 and 3. Or at least on part. 3. Can't you just mount the partition 3 in Ubuntu and sudo gedit /mountpoint/boot/grub/menu.lst ?

---

### Post by user1397 on 2006-06-19
[quote=glotz]So that sounds like you have /boot folders on your partitions 1 and 3. Or at least on part. 3. Can't you just mount the partition 3 in Ubuntu and sudo gedit /mountpoint/boot/grub/menu.lst ?[/quote]i do have /boot folders on part. 1 & 3, but only on part. 3 does /boot/grub really "count" or matter, the other one (on part. 1, /boot/grub is basically useless).  And no you can't mount another distro while you're currently mounted on another one.  For proof, look at the error message I get when I try to click on the fedora installation's root icon (called 9.8 GB Volume) in "Computer" (look at attachment)

---

### Post by glotz on 2006-06-19
pmount, hmm...

```
me@mybox:~$ aptitude show **pmount**
Package: pmount
State: installed
Automatically installed: no
Version: 0.9.11-1
Priority: optional
Section: utils
Maintainer: Martin Pitt <mpitt@debian.org>
Uncompressed Size: 168k
Depends: libc6 (>= 2.3.4-1), libdbus-1-2 (>= 0.60), libhal-storage1, libhal1 (>=         0.5), libsysfs2
Suggests: hal, cryptsetup (>= 1.0)
**Description: mount removable devices as normal user**
 pmount is a wrapper around the standard mount program which permits normal
 users to mount removable devices without a matching /etc/fstab entry. This
 provides a robust basis for automounting frameworks like GNOME's Utopia project and confines the amount of code that runs as root to a minimum.

 This package also contains a wrapper "pmount-hal" which reads some information
 like device labels and mount options from hal and passes them to pmount.
 Install the package "hal" if you want to use this feature.

 If a LUKS capable cryptsetup package is installed, pmount is able to
 transparently mount encrypted volumes.
me@mybox:~$

```

What if you open a terminal and make a folder, say **sudo mkdir /media/fedora**
and then try **sudo mount /dev/hda5 /media/fedora**

Can you now access the part 3 via /media/fedora?

---

### Post by user1397 on 2006-06-19
the thing is, glotz, that mounting fedora, if i could wouln't do anythin.  i would need to **boot **into fedora to be able to do anything, unless i ran some virtual os like vmware.  sorry but im not even going to try to do your suggestion, because it doesn't make any sense to me.  i can boot into fedora anytime i want, just by restarting, entering grub, and selecting fedora, so booting into fedora is not an issue for me.  i just want to have a grub that is installed by ubuntu, and that i can edit from within ubuntu.

---

### Post by glotz on 2006-06-19
No you wouldn't need to boot anything. Just try it! *Trust me!* :)
(you can mount what ever partition and you can edit whatever file)
(booting maybe only takes 20 seconds, mounting takes less than 1)

Or, take a look at these [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub](https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub)

---

### Post by user1397 on 2006-06-19
[quote=glotz]No you wouldn't need to boot anything. Just try it! *Trust me!* :)
(you can mount what ever partition and you can edit whatever file)
(booting maybe only takes 20 seconds, mounting takes less than 1)[/quote]oh i see what you meant now.  sorry for underestamating you!  i still care more for reinstalling grub rather than editing fedora's grub.

[quote=glotz]Or, take a look at these [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")
[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub]("https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub")[/quote]thanks for the links, i will take a closer look at them.

---

### Post by tonyr on 2006-06-19
I don't mean to be harsh here, but **glotz**'s suggestion is spot on.  The only difference
you are talking about, actually, is where (what partition) grub expects to find menu.lst.

You can  re-install the grub boot loader from ubuntu directly if the grub package is installed. 
Look at the grub man page and **info** grub (make sure they are all installed).  You will
have to have **/boot/grub/menu.lst** defined correctly.  Here some more links
to check out.

[http://users.bigpond.net.au/hermanzone/p15.htm#cli]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")
[http://www.troubleshooters.com/linux/grub/grub.htm#_What_You_Absolutely_Need_to_Know]("http://www.troubleshooters.com/linux/grub/grub.htm#_What_You_Absolutely_Need_to_Know")
which is actually a part of
[http://www.troubleshooters.com/linux/grub/]("http://www.troubleshooters.com/linux/grub/")

---

### Post by user1397 on 2006-06-19
[quote=tonyr]I don't mean to be harsh here, but **glotz**'s suggestion is spot on.  The only difference
you are talking about, actually, is where (what partition) grub expects to find menu.lst.

You can  re-install the grub boot loader from ubuntu directly if the grub package is installed. 
Look at the grub man page and **info** grub (make sure they are all installed).  You will
have to have **/boot/grub/menu.lst** defined correctly.  Here some more links
to check out.

[http://users.bigpond.net.au/hermanzone/p15.htm#cli]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")
[http://www.troubleshooters.com/linux/grub/grub.htm#_What_You_Absolutely_Need_to_Know]("http://www.troubleshooters.com/linux/grub/grub.htm#_What_You_Absolutely_Need_to_Know")
which is actually a part of
[http://www.troubleshooters.com/linux/grub/]("http://www.troubleshooters.com/linux/grub/")[/quote]thanks! so will reinstalling grub in synaptic overwrite my fedora-installed grub?

---

### Post by rai4shu2 on 2006-06-19
I think reinstalling grub would put it back on your Ubuntu partition. You would probably also get the bonus of having Fedora automatically detected by the Debian scripts. At that point, you could edit menu.lst in Ubuntu or (if you were in Fedora) you would have to mount your Ubuntu partition to edit it.

---

### Post by user1397 on 2006-06-19
oh what the hell, i'm doing it.  so what anyways, i have all of my stuff backed-up on another computer, right? :D

---

### Post by user1397 on 2006-06-19
hmmm, i uninstalled/reinstalled grub from synaptic, then rebooted, but i still got the grub from fedora's install.  (the reason why i know it's the fedora one, is that it has a fedora splash image)

i don't really know what to do.  should I uninstall grub from fedora (how?) and then reinstall it with synaptic in ubuntu?

---

### Post by tonyr on 2006-06-19
If I understand you correctly, you are only installing/unstalling the **grub package**.
You actually have to run **grub-install** as a command, in a terminal, with all the
right command line options.  Did you do that?

EDIT: I assume you have only one HDD and it is known as **/dev/hda**  Then from a
booted Ubuntu, **sudo grub-install /dev/hda** will install the **grub** boot loader
into the MBR, and sudo **update-grub** will rebuild **/boot/grub/menu.lst**
by rediscovering all bootable installations.

---

### Post by user1397 on 2006-06-19
[quote=tonyr]If I understand you correctly, you are only installing/unstalling the **grub package**.
You actually have to run **grub-install** as a command, in a terminal, with all the
right command line options.  Did you do that?[/quote]what are all the "right command line options"?

---

### Post by tonyr on 2006-06-19
See the EDIT addition in my previous post.  I believe the correct invocation is
```

sudo grub-install /dev/hda
sudo update-grub

```

It is not entirely clear to me at this point whether the device argument is a **device**
name or **partition** name.  **man grub** says ***_device-name_***, so I assume
that means **/dev/hda**, not **/dev/hda1**.

EDIT:  The [grub_manual]("http://www.gnu.org/software/grub/manual/html_node/Invoking-grub_002dinstall.html") says
> 
The program grub-install installs GRUB on your drive using the grub shell (see Invoking the grub shell). You must specify the device name on which you want to install GRUB, like this:

     grub-install install_device

The device name install_device is an OS device name or a GRUB device name. 


---

### Post by user1397 on 2006-06-19
[quote=tonyr]See the EDIT addition in my previous post.  I believe the correct invocation is
```

sudo grub-install /dev/hda
sudo update-grub

``` 
It is not entirely clear to me at this point whether the device argument is a **device**
name or **partition** name.  **man grub** says ***_device-name_***, so I assume
that means **/dev/hda**, not **/dev/hda1**.

EDIT:  The [grub_manual]("http://www.gnu.org/software/grub/manual/html_node/Invoking-grub_002dinstall.html") says[/quote]thanks! this worked perfectly!!!

---

