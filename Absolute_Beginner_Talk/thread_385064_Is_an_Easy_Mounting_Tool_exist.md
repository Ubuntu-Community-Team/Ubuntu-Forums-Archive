---
title: "Is an Easy Mounting Tool exist?"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by Carignan on 2007-03-15
Hi, First, i'm new to Linux Ubuntu so please don't flame me if this subject has been beaten to death in the past.

Second, I'm already able to mount manually other kidf of partition like ntfs or Windows Shared drive.  Each time i have to mount a drive But i found somewhat unuser friendly to search for the good fstab command and edit manuallly the fstab file.

So I did my search and i found nothing about an easy Mounting tool with a nice GUI that can mount any kind of stuff and edit for me the fstab file?  ( google search with: Ubuntu "Mounting tool" GUI gave:  29 pages hits :confused: )

Is this kind of tool already exist?

If no, is there an old abandoned  project for this kind of tools ?

tks

---

### Post by markcls on 2007-03-15
If you're looking to mount an NTFS drive easily, go here:
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

I'm not really sure what you mean by fstab though. I'm a linux noob myself! :D

---

### Post by astrolabio on 2007-03-15
Storage Device Manager may be your answer.
gksudo /usr/bin/pysdm

It's very powerful. Use the Assistant to help you out with the options if you don't understand them.

I'm sure there are easier options. 

The problem is that linux has a long history behind. So you often find text file configuration tutorials instead of easier GUI tutorials. The reason is that all experienced linux guys learned to do that stuff the old school way, and since it still work they continue teaching it in that way.

But there are actually plenty of easier tools that actually should be taught.

---

### Post by Carignan on 2007-03-15
Ya i know that procedure, i don't know it by heart but i used it very often. but this is exacly what i want to avoid.

what i'm searching for is a tools that can do that in 5 secondes instead of 5 minutes  ( Am i lazy? probably :) )

maybe i'm missing something, because Ubuntu is very easy and fun to use in all aspect of an os should be,  except for the mounting stuff. Mount fat, mount ntfs, mount read/write shared drive is always a pain! why?  Is this because it's not technicaly trivial?

i'm sure such a basic tools already exist right before my eyes, but i can't find it!


fstab is the file where you specified the Auto mount stuff

---

### Post by Songwind on 2007-03-15
I believe there is a gnome took called "gnome-mount" but I have never used it.

---

### Post by gummo on 2007-03-15
> **markcls said:**
> If you're looking to mount an NTFS drive easily, go here:
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)


Yea thats what i use too. NTFS-3G to mount ntfs drives (used the autoconfig) very easy and does his job perfect.

And if u are looking for something that mounts ISO's here are 2 little Nautilusscripts to do just that. 

MOUNT ISO FILES:
```

#!/bin/bash
#
for I in `echo $*`
do
  foo=`gksudo -u root -k -m "enter your password for root terminal
access" /bin/echo "got r00t?"`
sudo mount -o loop -t iso9660 $I /media/ISO
  done
done
exit0
```

UMOUNT ISO FILES:

```
#!/bin/bash
#
for I in `echo $*`
do
  foo=`gksudo -u root -k -m "enter your password for root terminal
access" /bin/echo "got r00t?"`
sudo umount $I
 done
done
exit0
```

---

### Post by aysiu on 2007-03-15
Knoppix?

---

### Post by dannyboy79 on 2007-03-15
sounds like you want a gui which modifies your fstab for you. not sure if there exists a program like that but all you have to do is modify your fstab once and then everytime from then on, it should just automatically mount everytime if you have the auto option. otherwise if you want something to mount network shares easily, i use xsmbrowser because I use xfce which doesn't have nautilus or knoqueror for doing that. I am very curious as to why a programmer hasn't created a simple little program that uses a little gui for this yet. maybe after I learn how to use python, I'll try that as my first project.

---

### Post by Carignan on 2007-03-15
> **dannyboy79 said:**
> sounds like you want a gui which modifies your fstab for you. not sure if there exists a program like that but all you have to do is modify your fstab once and then everytime from then on, it should just automatically mount everytime if you have the auto option. otherwise if you want something to mount network shares easily, i use xsmbrowser because I use xfce which doesn't have nautilus or knoqueror for doing that. I am very curious as to why a programmer hasn't created a simple little program that uses a little gui for this yet. maybe after I learn how to use python, I'll try that as my first project.

Exactly that i'm searching for, a GUI that Mount and modifiy the Auto Mount script(fstab)

this could be realy cool for all kind of mountable stuff!

---

### Post by madmax69 on 2007-04-09
I found komba but it's only for mounting networks shares using smbfs. It would be cool if someone took its source code and made it a sys app or modified it to write to fstab

---

### Post by bikeboy on 2007-04-09
It's not what you're looking for, but setting up a .bash_aliases file and enabling bash aliases might at least ease the hassle for you somewhat.

A nice little howto already exists on our forums:

[http://ubuntuforums.org/showthread.php?t=44458](http://ubuntuforums.org/showthread.php?t=44458)

---

### Post by madmax69 on 2007-04-09
nar man i was doing command line back in the 80's on my commadore 64 

20 years has past it's time for linux to grow up and enter the wonderful world of point an click and drag and drop.

---

### Post by dannyboy79 on 2007-04-09
that'll never happen. there will always remain the ability to use the cli. it's way more efficient if you know it than to wait for some gui to come up to simply edit your fstab file!!!

---

### Post by nfinitone on 2007-04-10
Well, ironically I just did a complete reinstall of Ubuntu a few minutes ago, getting rid of Kubuntu. KDE has an excellent GUI for editing fstab entries. It's a part of the "system utilities" set of applets, so I don't know the exact name of the package, and it's installed by default as a part of KDE. What I do know is that it allows you to do *everything*. You can set the proper mount points, device names, filesystem types, and even enable/disable mounts on the fly. 

You can also select the "Advanced" tab and enter advanced parameters such as "async" and others. I've used it mainly when setting up various NFS mounts from a small file server. It worked with no problems at all. I've also successfully mounted and enabled my windows partitions for use in VMWare.

After switching to the GNOME window manager, I'm starting to feel a bit slighted when it comes to doing various sysadmin tasks in a GUI. I've been using KDE forever (I was familiar with the MS-like interface) and I decided to try GNOME out for a bit. I do not recommend just installing KDE system utility packages in a GNOME environment. I've had some bad results doing that before and it tends to make a mess of your installation.


> **madmax69 said:**
> nar man i was doing command line back in the 80's on my commadore 64 

20 years has past it's time for linux to grow up and enter the wonderful world of point an click and drag and drop.

madmax69, I have to agree with you %100. I've been using a command line since DOS 6.22 and SuSE 6.2 and it's tiring. I'm getting too old for this stuff and my brain's starting to put info in a trash pile. I can't retain all of these bash syntaxes like I used to.

The CLI exists not because it is easier to use, but because
a) It's easier to code a command line application, and
b) No person/group/company has designed the perfect GUI, yet
Look at the iPod. In all honesty, it's only just a music player. It's not like it serves you drinks and bears your children. But the interface is so simple and easy, you really cant   
get any simpler.

And anyone who says that the CLI is easier once you learn it...thats just circular reasoning. I mean, ancient Egyptian Hieroglyphs are easier,too, once you learn it....

---

### Post by sicofante on 2007-04-26
I've just found this: [http://flomertens.free.fr/disk-manager/features.html](http://flomertens.free.fr/disk-manager/features.html)

---

