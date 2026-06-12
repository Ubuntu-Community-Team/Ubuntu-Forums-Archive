---
title: "Maintaining Ubuntu"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by milad on 2006-12-09
//Sorry for my poor English

Ok, I've been using Ubuntu for few months. I've fixed all minor problems I faced (Thanks to this forum) and now I have a quite stable system.

So, as you know, the process of learning Linux includes a lot of tweaking and playing around with the system. I've installed and uninstalled a lot of packages and executed countless commands in terminal which I don't know the purpose of half of them. So here is my question:

What are the task that I should do from time to time to keep my Linux in best shape? I mean in window$ I used to delete temporary files, defragment my hard disk, clean registry and so on. Are there any similar tasks in Linux?

---

### Post by az on 2006-12-09
> **milad said:**
> 
What are the task that I should do from time to time to keep my Linux in best shape? I mean in window$ I used to delete temporary files, defragment my hard disk, clean registry and so on. Are there any similar tasks in Linux?

Just keep up-to-date with software updates.

---

### Post by insane_alien on 2006-12-09
yeah maintaining  a linux system is easy and boring compared to the minefield that is windows. regular updates and thats about it.

---

### Post by oliviacond on 2006-12-12
that's all? wow, Linux is amazing!

---

### Post by Kobalt on 2006-12-12
One little thing you could do is cleaning up orphan packages (from installed and uninstalled softwares dependencies). There's a neat tool to do so, it's in the repos, it's called "gtkorphan".

---

### Post by hyper_ch on 2006-12-12
just execute on a regular base:

```

sudo apt-get update

```
and then
```

sudo apt-get upgrade

```

Or in your gui packet-manager you can enable auto-updates :)

---

### Post by 3rdalbum on 2006-12-12
The /var/cache/apt/archives folder will start to fill up with packages, if you're doing a lot of installing. You can clean out all the packages there as part of your regular maintanence (or you can set up Synaptic to have a limit to how much accumulates there).

Make sure fsck runs at every 30 mounts too; that's good preventative maintenence. And it's a good idea to download a rootkit hunter from the repos and run that occasionally. I can't think of anything else I've needed to do.

---

### Post by wieman01 on 2006-12-12
> **Kobalt said:**
> One little thing you could do is cleaning up orphan packages (from installed and uninstalled softwares dependencies). There's a neat tool to do so, it's in the repos, it's called "gtkorphan".
But be very careful as far as this tool is concerned. It's definitely meant for "advanced" users. Don't use if you don't know what you are removing/doing. It can destroy existing programs... e.g. codecs.

---

### Post by seijuro on 2006-12-12
> **insane_alien said:**
> yeah maintaining  a linux system is easy and boring compared to the minefield that is windows. regular updates and thats about it.

LOL, that is sooooooo true.

---

### Post by wieman01 on 2006-12-12
> **3rdalbum said:**
> The /var/cache/apt/archives folder will start to fill up with packages, if you're doing a lot of installing. You can clean out all the packages there as part of your regular maintanence (or you can set up Synaptic to have a limit to how much accumulates there).

Make sure fsck runs at every 30 mounts too; that's good preventative maintenence. And it's a good idea to download a rootkit hunter from the repos and run that occasionally. I can't think of anything else I've needed to do.
It does a check at every 25 mounts by default, doesn't it?

---

### Post by Delkster on 2006-12-12
> **3rdalbum said:**
> And it's a good idea to download a rootkit hunter from the repos and run that occasionally.

Remember that those often report false positives, though, so don't get overly paranoid about it either.

---

### Post by seijuro on 2006-12-12
You can also clear out your browser cache files and such too just like on windows but it really doesn't offer much other than keeping wasted hard disk space to a minimum and if I don't mention it I'm sure someone else will you can just limit the size of your cache and not worry about it at all.

---

### Post by hoagie on 2006-12-12
You can always delete left out libraries or dependencies of uninstsalled applications. You can do via Synaptic, in the Status section choose Not installed (residual config) and remove those packages. If you are more a terminal guy you can simply do
```
sudo apt-get autoremove
```

---

### Post by Delkster on 2006-12-12
> **hoagie said:**
> You can always delete left out libraries or dependencies of uninstsalled applications. You can do via Synaptic, in the Status section choose Not installed (residual config) and remove those packages.

Actually that doesn't remove 'orphaned' packages -- that is, those that have been installed only to satisfy dependencies but which aren't required for that anymore. You can use that to find packages that you've had installed at some point and later uninstalled but which still have some configuration files around somewhere. Normal uninstall doesn't remove the configuration. If you want to remove the configuration and all leftovers, do a 'complete remove' in Synaptic.

---

### Post by moshuptrail on 2006-12-12
> **3rdalbum said:**
> Make sure fsck runs at every 30 mounts too; that's good preventative maintenence. And it's a good idea to download a rootkit hunter from the repos and run that occasionally. I can't think of anything else I've needed to do.

Whoa!  What's a rootkit hunter?  What's a rootkit?  Sounds like a rootkit is something evil.  I checked the Wiki and rootkit doesn't have a title listing except oblique references like above.  From context I am thinking rootkit = virus.  I thought we didn't have to worry about virus software in Linux.

---

### Post by seijuro on 2006-12-12
> **moshuptrail said:**
> Whoa!  What's a rootkit hunter?  What's a rootkit?  Sounds like a rootkit is something evil.  I checked the Wiki and rootkit doesn't have a title listing except oblique references like above.  From context I am thinking rootkit = virus.  I thought we didn't have to worry about virus software in Linux.

A Rootkit is not a virus as in that is does not infect your system or try to transmit itself. Rather its a piece of software that is intended to allow a remote user to gain root privledges on your system. If you do not run any services and you only install from the repos and trusted sites you don't even need to check for rootkits.

In general you can look up almost any IT term at whatis.com its a really good resource for non-IT types to quickly get a definition of something that sailed over their head.

---

### Post by glotz on 2006-12-12
> **moshuptrail said:**
> What's a rootkit?[http://en.wikipedia.org/wiki/Rootkit](http://en.wikipedia.org/wiki/Rootkit)

Wackypedia to rescue! ;)

---

### Post by xyz on 2006-12-12
To set at what boot you want to run fsck, run:
```
sudo tune2fs -c 50 /dev/hdx@
```
Change "50" to whenever you want a check at boot. "x@"...you need to change those to wherever your Ubuntu partition is!  I put in "10"...laptops are more often turned on/off.

Originalle by Heiode/A-Start:
When you've got your OS running the way you like it, create a backup-easily-restorable copy/backup of your system:
In a terminal:
```
sudo su
cd /
 tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/media --exclude=/sys /

Restore command:

tar xvpzf backup.tgz -C /
```
You'll want to "mkdir" whatever you excluded when running the backup command. This will be done after you restore your system.
There are many other ways to back up...to name a few...Lice CD, Partimage,rsync....
Also:
[HOWTO: Cleaning up all those unnecessary junk files...]("http://www.ubuntuforums.org/showthread.php?t=140920&highlight=unnecessary+files")
Running Tip #4 caused problems to my system...so watch out!

---

### Post by smoker on 2006-12-12
> **3rdalbum said:**
> The /var/cache/apt/archives folder will start to fill up with packages, if you're doing a lot of installing. You can clean out all the packages there as part of your regular maintanence (or you can set up Synaptic to have a limit to how much accumulates there).

i've just had a look at this folder, is it safe to delete everything in here?

---

### Post by wieman01 on 2006-12-12
> **smoker said:**
> i've just had a look at this folder, is it safe to delete everything in here?
Yes, it's safe. Just don't remove any folders in there (e.g. partial). Will be fine. I generally keep all .deb files in case I should ever drop offline with Internet connection being unavailable. That got me into trouble once, so I keep the .deb files for backup.

---

### Post by smoker on 2006-12-12
thanks, wieman01,

good advice:-)

---

### Post by seijuro on 2006-12-12
> **wieman01 said:**
> Yes, it's safe. Just don't remove any folders in there (e.g. partial). Will be fine. I generally keep all .deb files in case I should ever drop offline with Internet connection being unavailable. That got me into trouble once, so I keep the .deb files for backup.

same here plus since my wife's laptop is almost identical to mine except I have some extra memory and we currently only have dialup and updates I download I can share the .deb file with her over our lan and save her the download.

---

### Post by Eddie Wilson on 2006-12-12
I also keep all my .deb files on a DVD-RW. I'm on dialup also and they come in handy if you ever have to do a new install.
Eddie

---

### Post by bodhi.zazen on 2006-12-12
I do two things:

Mirror my partition: [Mirror with gparted](http://www.ubuntuforums.org/showthread.php?&t=316237)

Clean/Degunk:
	[http://doc.gwos.org/index.php/RemoveJunkFiles](http://doc.gwos.org/index.php/RemoveJunkFiles)
	[http://ubuntuforums.org/showthread.php?&t=140920](http://ubuntuforums.org/showthread.php?&t=140920)

---

### Post by ragnar_123 on 2006-12-12
or if you really want to do some cleaning, install windows on a vmware virtual machine :P

oh, linux is so great :)

---

### Post by esaym on 2006-12-12
> **sjau said:**
> 

Or in your gui packet-manager you can enable auto-updates :)

I thought the packet manager always auto updated?  Is there a way to turn it off?  Might be helpful for my grandma on 56k.

We are talking about the icon that pops up in the bottom right hand corner for updates right?

---

### Post by Delkster on 2006-12-12
> **esaym said:**
> I thought the packet manager always auto updated?
Looks like he's running Xubuntu (with the lightweight Xfce desktop) rather than the traditional Ubuntu with (with the Gnome desktop). I don't know if the update manager icon automagically pops up by default on Xubuntu, although you're correct in that it does in Ubuntu.

> Is there a way to turn it off?  Might be helpful for my grandma on 56k.

In Edgy it's in System > Administration > Software Sources > Internet updates. I'm not sure about Dapper but it's probably either in something similar or possibly in Software Properties (or so) under Administration.

---

### Post by jbonll05 on 2006-12-12
"fsck runs automatically, no problem. The "gtkorphan" mentioned above is going in my three Ubuntu machines; two in my office and one personal. No M$ here. Your post has led me to another good tool and satisfied my craving to defrag, etc. from my windows days.

JB: Ubuntu user since oct05

---

