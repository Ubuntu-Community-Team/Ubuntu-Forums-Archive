---
title: "clean install vs. dist-upgrade what do u think???"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by gigi1234 on 2006-05-03
I'd to give Dapper a spin. 

But I am somewhat confused. Is it better to do a dist-upgrade or a clean installation?

Is there a way I can upgrade without losing my settings and user-installed packages?

Any general thoughts on the latest beta?

---

### Post by frodon on 2006-05-03
It's quite the same, but i prefer the dist-upgrade since it keeps your settings.
At the time i ran a dist-upgrade to move from hoary to breezy and all worked just fine, i just needed to reinstall nvidia drivers if i remember well.

So i would advice you to make a ghost of your partition (just in case) and run a dist-upgrade.

---

### Post by debernardis on 2006-05-03
Sunday I tried to dist-upgrade my kubuntu-breezy... thank God I had a backup because the result was unable to boot! :evil: I'll try a fresh install :-|

---

### Post by az on 2006-05-03
[QUOTE=debernardis]Sunday I tried to dist-upgrade my kubuntu-breezy... thank God I had a backup because the result was unable to boot! :evil: I'll try a fresh install :-|[/QUOTE]
You can always boot the old kernel.  Dist-upgrading doesn't remove the one that you previously used.

---

### Post by aggiechemist on 2006-05-03
How about disk space?

I'm curious if a dist-upgrade leaves more behind on the disk than a clean install. You said that it leaves the old kernels in place, but it there a lot of other stuff too? I'd rather not have my hard drives slowly collect bits of old versions over time, so maybe a clean install leaves less mess. But how many MBs of less mess?

---

### Post by ComplexNumber on 2006-05-03
> You said that it leaves the old kernels in place, but it there a lot of other stuff too? a distro upgrade removes ALL the old stuff first (including the kernel). when i upgraded suse, fedora, and mandrake/mandriva, it even went and uninstalled all the rpm packages i had used 'checkinstall' to turn compiled tarballs into rpm's. if the old kernel somehow remains, that may be because the previous installation had the boot info on a seperate /boot partition whilst the new installation used the MBR instead.


[quote=gigi1234]I'd to give Dapper a spin. 

But I am somewhat confused. Is it better to do a dist-upgrade or a clean installation?

Is there a way I can upgrade without losing my settings and user-installed packages?

Any general thoughts on the latest beta?[/quote] when going to the next version up(eg breezy to dapper), it is sometimes ok to just do an upgrade, otherwise do a clean install. however, in future, if you want to do a clean install and still keep your settings, i suggest that you set aside a partition for your /home directory (ie when you are partitioning your disk during the install, make /home as your mount point. therefore, you should have "/", "/home", and "Swap" as your various partitions. you can also choose to have "/boot" as a partition too, but i have yet to see any advantage because i write the boot info to the MBR). if you have your /home directory as a separate partition, all your user settings will be intact after a clean install.

---

### Post by az on 2006-05-03
[QUOTE=ComplexNumber]a distro upgrade removes ALL the old stuff first (including the kernel). when i upgraded suse, fedora, and mandrake/mandriva, it even went and uninstalled all the rpm packages ..[/QUOTE]
This is Ubuntu.  Thats not how it works.  apt-get upgrade will install any package that is already installed which has a newer version in the repositories.  It will install extra packages as needed by the dependencies.

A dist-upgrade will do the same thing, but be more aggressive and not balk at removing some packages.  It will not remove any packages it doesn't have to.

It is pretty dumb to remove an old kernel in favor of a new kernel you have not booted yet.  You can be left with an unbootable system.

aggiechemist:  You will be told how much there is to download and how much more or less disk space it will take.  It is not much since most of the packages get replaced (upgraded) and there are only a few that are left behind.

---

### Post by TimelessRogue on 2006-05-03
I did a 'dist-upgrade' yesterday afternoon and all went well ... much easier and perhaps safer than a fresh install with all my settings and such preserved.  Spent most of the night just playing and checking things out to make sure everything works.  All went well and it was the easiest upgrade I've experienced of any OS ...

Actually, I'm now going ahead with the upgrade on my HP laptop ...

And, Dapper Drake Beta is great!  Go for it ... and enjoy!

---

### Post by ComplexNumber on 2006-05-03
<accidental double post> **please delete.**

---

### Post by ComplexNumber on 2006-05-03
> It is pretty dumb to remove an old kernel in favor of a new kernel you have not booted yet. You can be left with an unbootable system.
i meant by burning the new clean installation to disk *first* and doing the clean installation that way.

---

### Post by mfarquhar on 2006-05-03
when i started up on hoary i did a clean install and it worked fine.
then when i got breezy and did a clean install, i had some problems with stteings i think. so i got my data off, wiped the drive, and re-installed hoary, then upgraded to breezy and it went much better the next time around.

just be sure to use the right commands to upgrade. 
i accidently updated all the packages instead of upgrading the distribution and wreaked havoc with my sysytem.

---

### Post by Symbios on 2006-05-03
I did a dist upgrade from Breezy. It wasn't pretty. It downloaded 900MB of files and then it rebooted. First it couldn't find the root file system, and after hours fiddling with it, I finally got it to see it. Everything started loading fine and I was getting ready to be greeted by the brand new login screen, and then... CRASH, xserver dies. The whole system froze up so bad that I couldn't even view the x config file to see what went wrong. I was so tired of messing with it that I just gave up and downloaded the 600MB live CD, as I really wanted to try out the Expresso installer. Well, that didn't go well either, it was buggy and couldn't install grub onto my boot sector. So, I tried the install CD, and SUCCSESS! I'm finally running Dapper. And all it took was 2GB of bandwidth, 2 Cd's and 15 hours of hitting my head on my desk... 

I guess what I'm saying here is, do a fresh install! And don't use the the live CD to do it!

---

### Post by stansz on 2006-05-03
im reading all of this...and im just wondering..how do u do a clean install?? 

say i want to do a clean install on my system which is dual booted, do i just put in the disc and click the option?

---

### Post by nalmeth on 2006-05-04
I suggest fresh install.
2 times attempted dist-upgrade, 2 times failed :(
Other people have been successful, but my take is to go fresh

---

### Post by RAV TUX on 2006-05-04
[QUOTE=gigi1234]I'd to give Dapper a spin. 

But I am somewhat confused. Is it better to do a dist-upgrade or a clean installation?

Is there a way I can upgrade without losing my settings and user-installed packages?

Any general thoughts on the latest beta?[/QUOTE]

I did both,...

If you do the distro upgrade, just create a dual boot so you have two Ubuntu's one you have been using, and a new one(the new one is what you want to do your distro upgrade on).

Fortunately, when I did the upgrade, when it didn't work; my original version was fine.

Then I burned a ISO CD and loaded from disc, worked great!

dapper is the greatest!.....

I then loaded PC-BSD as a dual boot, while nice I prefer Dapper and now only run Dapper and love it!

My answer to you question is do both.
:mrgreen:

---

### Post by Sef on 2006-05-04
Whatever you decide, **back up** your data first.  

Me I prefer a clean install.

---

### Post by gigi1234 on 2006-05-07
Hmmm seems to be that the fresh install is the safest approach. Maybe I'll try this home folder partition idea-sounds good. At least I wouldn't have to restore quite as much. 

I wonder though, does the dist-upgrade still work if you are dual booting?

And, as for the question about doing a fresh install-just pop in the disk and use the existing Ubuntu partitions. Of course you lose everything from your previous setup. 

Thanks to everyone who responded!

---

### Post by n3tfury on 2006-05-07
[QUOTE=stansz]im reading all of this...and im just wondering..how do u do a clean install?? 

say i want to do a clean install on my system which is dual booted, do i just put in the disc and click the option?[/QUOTE]

well, i spent a bit of time with trying the live beta2 installer (which i know is a bit buggy) and even though i assigned a partition root, it'd say that i didn't.  go with the install disc for sure.  i dual boot myself and things went very well and fairly quickly.

GL

---

