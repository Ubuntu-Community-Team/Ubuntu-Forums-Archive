---
title: "what happens when new release arrives?"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by ADH on 2007-08-27
As I've said in other threads, I was able to install Ubuntu 7.04, and have been looking at it and trying to pick things up a litttle at a time.  I download updates when the OS tells me they're available.  What will happen when the next release comes out?  Will I be told there's an update, and all I have to do is download the new version and let the system install it over 7.04, or is there more to it?

I'm sure there is a way to uninstall unwanted programs in Ubuntu, but I haven't found it yet.  Is it under "System" somewhere?

I haven't figured out how to install tarballs and such yet (I'm even unsure what to do with zips in Ubuntu.)  I'm used to zips, self-extracting .exes in Windows and OS/2, and self-extracting .wpis in OS/2, going to a command line or using a file manager to create a directory on drive C, D, E, or whatever, unzipping into it, and creating a program  object in OS/2 (in Windows, I've pretty much stuck with self-extracting programs, as I rarely use Windows.)  I'd like to install the Seamonkey browser suite and the hard drive utility DFSEE (I'm a registered user, so I miight as well have it available in Ubuntu as well as in eComStation and Windows.)
 
I'm still studying my "Ubuntu Linux for Dummies."  Thus far, most of my time in Ubuntu (when bot trying things) has been used to browse the web, as Linux has more plugins available than eCS does, so I can view videos.

Thanks as always for help.

---

### Post by Jimmyfj on 2007-08-27
If you are running Ubuntu 7.04 then shortly after the final/official release of 7.10 Gutsy Gibbon your update manager should inform you that there's a new release available and give you the option to upgrade over the Internet. But, as always, a clean install is the best. An upgrade can fail for various reasons. And Tribe 5 of the new release are already available for download. I find it very stable even though it IS beta and might break.

For the uninstall you can use either Add/Remove or Synaptic.

---

### Post by insane_alien on 2007-08-27
a clean install is recommended(this is immensly easy if you have a seperate /home partition. from your description of your linux prowess i doubt this is the case(although i may be wrong.)

in which case you would need to use a backup medium to keep your data.

---

### Post by Magneticgravity on 2007-08-27
If you want to know how to install things, like extracting etc. i suggest you read through this useful guide:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Theres plenty more guides out there, just ask here or google if any more problems arise :D

---

### Post by ADH on 2007-08-27
II believe I created a separate home section when I installed.  How would I check that I did so?

---

### Post by davidjmayo on 2007-08-27
> **ADH said:**
> II believe I created a separate home section when I installed.  How would I check that I did so?

from a terminal
```
sudo fdisk -l
```
l is a lowercase L
You should see 2 Linux partitions and one for swap

Check the partition sizes to make sure!!

---

### Post by david_e on 2007-08-27
You should look at the mount output to see if you are using a separate partition for the home folder

```

mount

```

for example this is my output:

```

/dev/sda1 on / type ext3 (rw,noatime)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec)
udev on /dev type tmpfs (rw,nosuid)
devpts on /dev/pts type devpts (rw,nosuid,noexec)
/dev/sda3 on /home type ext3 (rw,nosuid,noatime)
shm on /dev/shm type tmpfs (rw,noexec,nosuid,nodev)
usbfs on /proc/bus/usb type usbfs (rw,noexec,nosuid,devmode=0664,devgid=85)

```

You can see that I have "/dev/sda3" on "/home" and "/dev/sda1" on "/"...

---

### Post by davidjmayo on 2007-08-27
whoopps I forgot about mount

---

### Post by ADH on 2007-09-15
I have two Linux partitions and one for swap, according to fdisk.

---

### Post by skymera on 2007-09-15
> **Jimmyfj said:**
> If you are running Ubuntu 7.04 then shortly after the final/official release of 7.10 Gutsy Gibbon your update manager should inform you that there's a new release available and give you the option to upgrade over the Internet. But, as always, a clean install is the best. An upgrade can fail for various reasons. And Tribe 5 of the new release are already available for download. I find it very stable even though it IS beta and might break.

For the uninstall you can use either Add/Remove or Synaptic.

i got told to do clean install

but then you have to redo EVERYTHING!

i really cant be bothered, i think you should do straight upgrade.

if it fails then do a clean install

---

### Post by alienexplorers on 2007-09-15
When a new release arrives doesn't mean you have to load it on your computer.  You can wait for support of your current version to end or you can go for the LTS version and keep it around if you are not looking for all the new bells and whistles.

---

### Post by Kilz on 2007-09-15
> **alienexplorers said:**
> When a new release arrives doesn't mean you have to load it on your computer.  You can wait for support of your current version to end or you can go for the LTS version and keep it around if you are not looking for all the new bells and whistles.

Good advice, lots of people feel they must have the latest. But some times stability is more important. Feisty is very stable. I would also recommend that new users wait a week or so before upgrading Ubuntu to the next version if they plan on upgrading to Gutsy. Especially people who dont have a firm grasp of troubleshooting a broken system. While lots of people test the beta versions, a bug could slip through. Waiting a week will make sure that enough people have installed Gutsy and no major bugs have been missed.

---

### Post by chrome307 on 2007-09-15
How do you lock down Feisty Fawn so it does not want to upgrade?

I know how to do this for a single package via Synaptic, but when the new release is available will the update manager simply keep on popping up each time you login and remind you?

Is there not a way to simply turn off these core updates?

---

### Post by badactress on 2007-09-15
Your Fiesty won't try to upgrade itself to Gutsy automatically so there's no problem. You'll keep getting Fiesty updates through the update-manager for as long as it's supported.

If you wanted to upgrade to Gutsy using the update manager you'd have to change your repositories from the Fiesty one's to Gutsy, which isn't something you can do by mistake.. and isn't even really advisable.

---

### Post by Skidpad on 2007-09-15
> **chrome307 said:**
> How do you lock down Feisty Fawn so it does not want to upgrade?

I know how to do this for a single package via Synaptic, but when the new release is available will the update manager simply keep on popping up each time you login and remind you?

Is there not a way to simply turn off these core updates?
The "upgrade" will be viewable at the top of the Update Manager screen.  It won't install unless you click it, nor does it "nag" you...there is simply an upgrade icon at the upper right of the window.  See my attached screenshot.

Keep in mind that this is on Edgy, and I'm being reminded that there is a 7.04 distribution upgrade available; a Feisty>Gutsy upgrade window may be different.  :)

---

