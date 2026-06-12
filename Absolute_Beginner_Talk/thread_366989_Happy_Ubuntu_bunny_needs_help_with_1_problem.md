---
title: "Happy Ubuntu bunny needs help with 1 problem"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by NonPapa on 2007-02-21
Hi there,

That was not just an attention-catching title for this post. I **am** a happy Ubuntu user; EXCEPT for the following problem:

I can't watch DVDs - neither with gxine nor Movie Player.
I also had a couple of bad crashes/freezes. (they are bought/hired DVDs not ripped ones, I don't have a DVD-R drive).

All of the above I relate to some problem with "extended memory", i.e. you can virtually extend the RAM by "putting some stuff" on the hard-drive, as opposed having it in RAM. Can I increase this?

Does this make sense? If yes, please, please help me to become the Ubuntu-in-paradis-user.
If it doesn't, please let me know what doesn't make sense...

Regards,
NonPapa

---

### Post by Sqwishy on 2007-02-21
...happy ubuntu bunny >_< l0l !!!
Did you lookit the ubuntu starters guide? Theres a section that tells you how to get the multimedia codeks that i'm thinking you need. [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs)

---

### Post by teaker1s on 2007-02-21
are you aware of restricted formats? if not look at this link
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

or automatix2

---

### Post by annda on 2007-02-21
the "extended memory" you are talking about is your /swap partition. if it actually is the problem with your crashes then your swap may be too small and you might need to resize it. how big is it? do you remember that from installation? if not, you can find out by the df command.

and how much RAM do you have?

---

### Post by NonPapa on 2007-02-21
> **Sqwishy said:**
> ...happy ubuntu bunny >_< l0l !!!
Did you lookit the ubuntu starters guide? Theres a section that tells you how to get the multimedia codeks that i'm thinking you need. [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs)

I thought I had done that, but
after doing the last line of the instructions I get
'0 packages upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 1102kB of archives. After unpacking 106kB will be freed.
Do you want to continue? [Y/n/?] '

Do I want to continue, or not?

HELP (please)! 
NonPapa

---

### Post by Sqwishy on 2007-02-21
well tell us what it says it's gonna remove lol! Also i forgot to tell you to check out the restricted formats page that teaker1s suggested [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by NonPapa on 2007-02-21
> **Sqwishy said:**
> well tell us what it says it's gonna remove lol! Also i forgot to tell you to check out the restricted formats page that teaker1s suggested [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Sorry, hadn't read everything:

The following packages will be automatically REMOVED:
  totem-gstreamer
The following NEW packages will be installed:
  totem-xine
The following packages will be REMOVED:
  totem-gstreamer


DOes this sound okay?

NonPapa

---

### Post by teaker1s on 2007-02-21
so select yes

---

### Post by Sqwishy on 2007-02-21
nvm teaker eddited his post, admin can delete this

---

### Post by NonPapa on 2007-02-21
> **annda said:**
> the "extended memory" you are talking about is your /swap partition. if it actually is the problem with your crashes then your swap may be too small and you might need to resize it. how big is it? do you remember that from installation? if not, you can find out by the df command.

and how much RAM do you have?

df

Filesystem          1K-blocks      Used          Available    Use%    Mounted on
/dev/hda3           7178972       3332400   3481900     49%       /
varrun                  111672         128             111544         1%       /var/run
varlock                 111672         0                  111672         0%       /var/lock
procbususb          10240          116                10124         2%       /proc/bus/usb
udev                     10240           116                10124          2%      /dev
devshm                111672         0                   111672        0%      /dev/shm
lrm                         111672     17580               94092       16% /lib/modules/2.6.17-11-generic/volatile
/dev/hda1             11888064   6584196   5303868  56% /windows

I have Knoppix still installed (would like to delete it but haven't yet found a Ubuntu programme for re-partitioning. I also can delete most of the windows partition. I can't see the swap partition
up there, but I seem to remember seeing two (one for Knoppix, and one for Ubuntu). I also want to delete Knoppix of course. 

[EDIT / ADDED INFO] RAM should be 512MB, if I'm not too tired to make this up - but it was always enough for WinXP. :))
Any hints appreciated.
NonPapa

P.S. If someone can give me a hint how I can re-partition the non Ubuntu partitions, that would help in increasing the swap partition for Ubuntu :-)

---

### Post by teaker1s on 2007-02-21
firstly the previous post only listed removed packages, it was then edited so is showed full changes so i changed my answer to yes. Allowing a package to be removed and another installed.

Depending on release version DMA may also need turning on, it's on in edgy and feisty, not sure dapper 6.06lts

---

### Post by Sqwishy on 2007-02-21
Did you try the restricted formats?? [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by NonPapa on 2007-02-21
> **Sqwishy said:**
> Did you try the restricted formats?? [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

No. I do like the spirit of NOT allowing all kind of stupid Win-centric formats (such as WMV)
to be working. :)

But I will read this page more thoroughly for background info.

---

### Post by NonPapa on 2007-02-21
DVDs are running now. Many thanks to Sqwishy, teaker1s and annda for all your help! Great support here!

If one of you can recommend a programme for re-partitioning from Ubuntu, that would be the icing of the cake. :)

Many thanks,
NonPapa

---

### Post by Sqwishy on 2007-02-21
> **NonPapa said:**
> DVDs are running now. Many thanks to Sqwishy, teaker1s and annda for all your help! Great support here! w00t you spelled my name right! :lolflag:

---

### Post by teaker1s on 2007-02-21
I'm not sure exactly what your looking for but gparted live iso is great point and click partitioner
[http://gparted.sourceforge.net/download.php]("http://gparted.sourceforge.net/download.php")

---

### Post by NonPapa on 2007-02-22
> **Sqwishy said:**
> w00t you spelled my name right! :lolflag:

Isn't that what cut & paste is for? :)

NP

---

### Post by NonPapa on 2007-02-22
> **teaker1s said:**
> I'm not sure exactly what your looking for but gparted live iso is great point and click partitioner
[http://gparted.sourceforge.net/download.php]("http://gparted.sourceforge.net/download.php")

Thanks, teaker1s. I will give that a try.

NP

---

### Post by annda on 2007-02-22
EDIT: i'm so slow again...

sorry, swap isn't listed using df, my bad. you can find it out by running fdisk -l

however, 512 MB RAM is good and should give you a great performance. you may be having problems with your video card's memory (if any), but not RAM. look around and see if you have the right drivers for your card. for example, on my previous laptop switching ati to radeon gave an impressive boost in performance.

but if you decide you need bigger swap, i recommend gparted here:
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
(it's based in knoppix)

---

### Post by steve.horsley on 2007-02-22
The command **free** will tell you if you have any swap, and how much is used. 
The command **sudo fdisk -l** will tell you if there is a swap partition on your hard disk.
**mount** will tell you if the swap partition is mounted. 
The file /etc/fstab is the one that contains the configuration of what to mount at boot.

---

