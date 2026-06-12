---
title: "Creating a boot/install CD of current set up"
date: 2007-07-18
forum: Apple Intel Users
---

### Post by mitchellsimon on 2007-07-18
I have now got my MacBook Pro dual booting between OS X and Ubuntu. I use rEFIt to boot into either.

Though now I have my Linux desktop set up exactly how I want it I want to make a backup of it so I can just reinstall it when I inevitable break everything. 

Ideally I would like to boot OS X, Windows XP and Ubuntu but I don't really want to start messing with partitions again until I have backed up my Ubuntu install.

Is there an easy way of doing this like creating an install CD like the one I used to install it in the first place which will just install my OS as it is now?

Thanks,

Simon.

---

### Post by black_raven2525 on 2007-07-18
There is a pretty good thread about this [_here_]("http://ubuntuforums.org/showthread.php?p=3033844#post3033844") and a HowTo [_here_]("http://ubuntuforums.org/showthread.php?t=35087").

---

### Post by cyberdork33 on 2007-07-18
There are SEVERAL, SEVERAL, ways to do a full system backup. It is really debatable what is the best way, etc. 

There are quite a few backup apps in the repos, as well as the low-level unix tools that most of them use to actually do the work (like rsync, tar, or dar)

black_raven already beat me to posting the tutorial that uses tar.

---

### Post by Gen2ly on 2007-07-18
I've used this one before:

[**[COLOR="Sienna"]Howto Backup and Restore[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=35087")

Works nicely.  Honestly however if you ever need to be concerned with diskspace the most important are your config files.  Having done fresh installs, losing 'em is a drag, you won't realize the degree of personalization till they are not there anymore.  Everything else can be reinstalled.

I execute a script like so:

```
cd /
tar cvpzf ubuntu-macbook-home-configs.tgz --exclude=/home/user/Applications --exclude=/home/user/Desktop --exclude=/home/user/My\ Documents --exclude=/home/user/My\ Music --exclude=/home/user/My\ Pictures --exclude=/home/user/My\ Videos --exclude=/home/user/Storage --exclude=/home/user/.mozilla/firefox/i6vgpy2n.default/Cache /home/user/ && chown user:user ubuntu-macbook-home-configs.tgz && mv ubuntu-macbook-home-configs.tgz /home/user/Storage/Safe/Backups/Configs
```

---

### Post by mitchellsimon on 2007-07-20
Thanks everybody. I'll check out all that's been recommended and let you all know what works best.

Simon.

---

### Post by mitchellsimon on 2007-07-20
> **Dirk.R.Gently said:**
> I've used this one before:

[**[COLOR="Sienna"]Howto Backup and Restore[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=35087")

Works nicely.  Honestly however if you ever need to be concerned with diskspace the most important are your config files.  Having done fresh installs, losing 'em is a drag, you won't realize the degree of personalization till they are not there anymore.  Everything else can be reinstalled.

I execute a script like so:

```
cd /
tar cvpzf ubuntu-macbook-home-configs.tgz --exclude=/home/user/Applications --exclude=/home/user/Desktop --exclude=/home/user/My\ Documents --exclude=/home/user/My\ Music --exclude=/home/user/My\ Pictures --exclude=/home/user/My\ Videos --exclude=/home/user/Storage --exclude=/home/user/.mozilla/firefox/i6vgpy2n.default/Cache /home/user/ && chown user:user ubuntu-macbook-home-configs.tgz && mv ubuntu-macbook-home-configs.tgz /home/user/Storage/Safe/Backups/Configs
```

This worked really nicely. I now have a 900MB .tgz file called backup though, If I erase my partition to then add space for windows how can I restore this to a ext3 partion without having to go through the whole process of reinstalling Ubuntu again. Can I copy this from an external drive (or another partition on my HD) to the ext3 file using the Ubuntu Alternate CD I used to install it in the first place?

My instincts say yes but I am a bit new to this Linux stuff so just wondered what anyone else says.

Thanks,

Simon.

---

### Post by benanzo on 2007-07-20
Absolutely.  All you need to do is boot to the Live CD (or alternate), mount the partition that you want to decompress your backup file onto, mount the external disk that contains your backup, and go to work like this:
```
tar xvpfz /media/usbdisk/backup.tgz -C /media/ubuntu
```

---

### Post by mitchellsimon on 2007-07-22
Excellent. Thanks.

What's the command for mounting a disk from the command line/terminal? I know 'mount' can be used for cd's but will that apply for USB/Firewire drives too?

Thanks.

Simon.

---

### Post by cyberdork33 on 2007-07-23
> **mitchellsimon said:**
> Excellent. Thanks.

What's the command for mounting a disk from the command line/terminal? I know 'mount' can be used for cd's but will that apply for USB/Firewire drives too?

Thanks.

Simon.

yep

you can type 'man mount' at a command line for more details

---

### Post by mitchellsimon on 2007-07-23
> **cyberdork33 said:**
> yep

you can type 'man mount' at a command line for more details

Thanks. You've all been really helpful. Great forum!

Simon.

---

### Post by pveith on 2007-07-23
i might add, that i used "partimage" with great success on my dekstops/servers for windows and ubuntu partitions. Right now i backuped my feisty install and upgraded to gutsy. So if all fails, i can switch mak in a mater of minutes using the ubuntu live-cd (partimage is not part of the live-cd, but is easiely installable via apt-get). It makes a compressed binary copy chunked down to fit dvds, so you can recreate the backup from dvd. It is "Norton-Ghost"-like program for those who know the norton-ghost and it can be used to create images for large scale deployment...

---

### Post by apotaktikos on 2007-07-24
> **Dirk.R.Gently said:**
> I've used this one before:

[**[COLOR="Sienna"]Howto Backup and Restore[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=35087")

Works nicely.
 
This is may be a very dumb question, so don't be too harsh on me....

Would it be possible to use this method for V2P migration? What I'm envisaging is installing a distro in vmware and doing the usual customizations and hacking about - then using tar to roll up the changes, doing a physical install and rolling them out on the real install. Is this a road to ruin?

Clearly if it can work at all it has limits, but could someone wiser than me tell me what they are??

Thanks.

---

### Post by cyberdork33 on 2007-07-24
> **apotaktikos said:**
> This is may be a very dumb question, so don't be too harsh on me....

Would it be possible to use this method for V2P migration? What I'm envisaging is installing a distro in vmware and doing the usual customizations and hacking about - then using tar to roll up the changes, doing a physical install and rolling them out on the real install. Is this a road to ruin?

Clearly if it can work at all it has limits, but could someone wiser than me tell me what they are??

Thanks.

Could work for some things, but you have to remember that the hardware is not the same in the VM as your real machine. Having customized config scripts and the like in your VM may not work correctly in your Real Machine.

---

### Post by apotaktikos on 2007-07-24
> **cyberdork33 said:**
> Could work for some things, but you have to remember that the hardware is not the same in the VM as your real machine. Having customized config scripts and the like in your VM may not work correctly in your Real Machine.

Thanks
Yep, the hardware issue is precisely what worries me...and I realise that config scripts would have to be tweaked...but in theory it should work, right? I've read a posts on the vmware forums citing instances of using Ghost to clone a vmware install with redeployment on a physical drive...and using tar or rsync is just the down and dirty way of doing the same thing, isn't it?
what I'm really interested in is fairly 'soft' customizations - adding a few applications, tweaking desktop environments, themes etc...I don't expect a 'one click' clone of the whole sytem by any means, more to perform a base install and then to overlay changes worked on in vmware..as you say it could work for some things, I suppose my question is could you specify what those hardware-independent things are?

(btw I realise this is somewhat off-topic for this forum..but I am the proud owner of an iMac with a shiny new copy of Ubuntu Studio residing on its second partition and this place has been my home for the last few days!!)

---

### Post by cyberdork33 on 2007-07-24
> **apotaktikos said:**
> Thanks
Yep, the hardware issue is precisely what worries me...and I realise that config scripts would have to be tweaked...but in theory it should work, right? I've read a posts on the vmware forums citing instances of using Ghost to clone a vmware install with redeployment on a physical drive...and using tar or rsync is just the down and dirty way of doing the same thing, isn't it?
what I'm really interested in is fairly 'soft' customizations - adding a few applications, tweaking desktop environments, themes etc...I don't expect a 'one click' clone of the whole sytem by any means, more to perform a base install and then to overlay changes worked on in vmware..as you say it could work for some things, I suppose my question is could you specify what those hardware-independent things are?

(btw I realise this is somewhat off-topic for this forum..but I am the proud owner of an iMac with a shiny new copy of Ubuntu Studio residing on its second partition and this place has been my home for the last few days!!)

I think they should work... imaging is not the same as tarring or rsync, but you can build systems that way... this is essentially how you would install a Gentoo system.

---

### Post by pveith on 2007-07-25
As said before partimage from universe is a really good CLI Norton ghost clone. I just switched back from gutsy to feisty just by restoring my root partition with it. Just took 15 Minutes and a reboot to have everything as beofre gutsy upgrade.
As for vmware: Just shutdown the guest and make a copy of the directory the guest is installed in. This copy can be used just like the original version. So no need for Ghost or binary copy of partions.

---

### Post by cyberdork33 on 2007-07-25
> **pveith said:**
> Just shutdown the guest and make a copy of the directory the guest is installed in. This copy can be used just like the original version. So no need for Ghost or binary copy of partions.

Huh? You can't directly access the filesystem in your VM hard drive image.

---

