---
title: "Gnome: Slower over time"
date: 2008-03-13
forum: Arch and derivatives
---

### Post by Ub1476 on 2008-03-13
So, I've been using Arch with KDEmod for a while, and it's lighting fast. Most apps takes just a second to open (Konsole, Control Center etc), and Opera and Amarok uses about 3 seconds. However, I missed Gnome a lot so I made a new Arch install with Gnome. Lighting fast after install, but now, a few days later, it's becoming kinda slow (Terminal 3s, Liferea 5s etc). On KDE I had Amarok, Akregator, Kopete and Klipper to start up automatic (Compiz and kNetworkmanager I started manually). On Gnome I have Compiz-Fusion, AWN, Networkmanager and Parcellite to start up automatic (Emesene, Audacious I start up manually).

I don't know if a startup session effects how fast I launch apps later, but might be useful.. I posted this on the Arch [forums]("http://bbs.archlinux.org/viewtopic.php?pid=341950#p341950") too, but I don't feel like getting anywhere. I fixed my /etc/hosts file though. It's of course only the first time I launch the app it takes some time though. After it has been launched and closed, opening it only takes about 1s. 

Any thought on this? I thought KDE (mod or not) was supposed to be large and slightly slower, and Gnome small and faster?

---

### Post by Hallvor on 2008-03-13
> **Ub1476 said:**
> 
I thought KDE (mod or not) was supposed to be large and slightly slower, and Gnome small and faster?

I have used Gnome, XFCE and KDE, and Gnome is in my experience the heaviest desktop environment of the three. KDE is very efficient if you use KDE applications with it.

---

### Post by disturbed1 on 2008-03-13
After you fixed your hosts file, did you restart? Not just log out, log in, but actually restart the PC.

Also, check to see what is running in the session and what loads by default.

System -> Preferences -> Session

Under heavy usage, I notice no slow down

top - 16:40:53 up 24 days,  2:58,  1 user,  load average: 2.55, 3.09, 2.91
Tasks: 137 total,   12 running, 125 sleeping,   0 stopped,   0 zombie


Perhaps a rouge program is eating CPU resources? FAM, Totem-thumbnailer, nautilus, java, those are notable suspects.


Since it opens slow only on the first instance, but subsequently the loading time is better, it could just be a file system problem, or fstab option.

ReiserFS is the slowest desktop file system to use, besides FAT and ext2. Ext3 is even faster than Reiser for desktop useage. JFS and XFS are most likely the best for desktop use, with ext3 being the old standby. You can also try the noatime option in FSTAB. Some people claim they see a difference.

A simple hdparm -Tt /dev/sda1 (or what ever /dev/ your hard disc is) will give you a simple speed test.

Timed buffer reads should be at least 70mb/s. If it's much slower, 65mb/s is on the slow side but ok ;) , it looks like a filesystem, or slow hard drive issue.

KDE uses a prefetch feature. Just as KDE borrows many things from Windows (IE/Explore Konquerer/Web Browser) it also borrows pre-loading some libs for faster loading. Gnome doesn't use this, since it's libs are already optimized and layed out in a sane manor. You could try adding prelink to your system to see if it helps.

Pacman -S prelink
man prelink

---

### Post by Ub1476 on 2008-03-13
Wow, thanks for a great reply:)

I'm not sure if I should install Prelink, as I'm already running Preload (deamon is added to rc.conf of course). What's better, the difference? From Sessions:

[LIST]
[*]AWN
[*]Compiz-Fusion
[*]Network Manager
[*]Parcellite
[*]Volume Manager
[/LIST]

Top command:
```
top - 22:53:55 up 9 min,  1 user,  load average: 0.06, 0.18, 0.13
Tasks: 100 total,   1 running,  99 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.0%us,  0.2%sy,  0.0%ni, 98.5%id,  0.2%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   1033352k total,   545920k used,   487432k free,     4020k buffers
Swap:   265064k total,        0k used,   265064k free,   239316k cached

```

hdparm from active partition:
```
/dev/sda1:
 Timing cached reads:   2314 MB in  2.00 seconds = 1158.15 MB/sec
 Timing buffered disk reads:   72 MB in  3.03 seconds =  23.80 MB/sec

```

I might add that those results are from a restart, only opened Terminal, Sessions and Firefox so I could reply. Disk reads differs over time though (from 70 to 80), cached reads goes slightly down.

File system is Ext3. What does the noatime option do? Advantages and disadvantages?

---

### Post by disturbed1 on 2008-03-13
Your disc timings are slow, painfully slow.

@arch libsoup-2.4.0]$ sudo hdparm -Tt /dev/sda1
Password: 

/dev/sda1:
 Timing cached reads:   1972 MB in  2.00 seconds = 985.94 MB/sec
 Timing buffered disk reads:  230 MB in  3.02 seconds =  **76.11 MB/sec**

Your drive is only reading data at ~24mb/s. This is fine if it's an older ATA 33/66 drive. If it's a newish ATA 100 or SATA drive, this could be an issue. Another program could be accessing the drive (Preload?) Check the hd light to see if activity is taking place. Beagle, and other indexing programs are also resource/disc hogs.

-------edit----------
sudo /etc/rc.d/**preload** stop
**preload** is the name of the preload module.
The above command will stop preload from running. This way you won't have to sudo nano /etc/rc.conf edit, restart, repeat :D
To start preload again
**sudo /etc/rc.d/preload start**

-------edit--------

Try removing AWN, Compiz-Fusion, and Parcellite, from your session. See if it improves. Then add Parcellite, check, then AWN.....Compiz.

Compiz will cause some slow down, this is normal.

It gets to a point where a compromise has to be made between speed and features. We could all load Win2000 on QuadCore machines and have blazing fast performance, but a dead boring experience ;) If the performance is lacking, you might have to tone down some features.

I'm honestly not the one to give a correct answer about Prelink vs. Preload. Preload is in the AUR, Prelink is in ARCH extra. Prelink is a RedHat utility for linking elf libraries, Preload preloads binaries into memory. Try not loading Preload, to see if it makes a difference. If that isn't broke, I wouldn't fix it ;)

man mount -

noatime
Do not update inode access times on this file system (e.g, for faster access  on  the  news  spool  to  speed  up  news servers).


> 
           Linux has a special mount option for file systems called *noatime* that can be added to each line that addresses one file system in the /etc/fstab file. If a file system has been mounted with this option, reading accesses to the file system will no longer result in an update to the atime information associated with the file like we have explained above. The importance of the noatime setting is that it eliminates the need by the system to make writes to the file system for files which are simply being read. Since writes can be somewhat expensive, this can result in measurable performance gains. Note that the write time information to a file will continue to be updated anytime the file is written to.Here's what a sample on my fstab looks like -
**/dev/sda1 / jfs defaults,noatime 0 1**

^^ NOTE!!!! Mine says jfs, because that's the file system **I** use. Yours says ext3?

---

### Post by articpenguin on 2008-03-13
I switched back to gnome even though i dont like its simplicty.

as for ext3 and jfs. JFS is faster than ext3 IMO. Ext3 does wat fat does for file looks ups is using linked lists. 

Also i dont like the disgusting overhead with ext3.

---

### Post by Ub1476 on 2008-03-13
Computer is Fujitsu, Amilo Pi 1536, maybe 1,5-2 years old. HDD is Sata, I believe.

lspci:
**SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)**


I'll check out your tips tomorrow. Got to sleep now. Thanks:)

---

### Post by deepclutch on 2008-03-14
hrmm...some project like kdemod for Gnome also!yeah,hopes so! :-|

---

### Post by Ub1476 on 2008-03-14
Instead of cleaning up my session, I made a new user and logged in with it. It's basically the same speed. Gnome do feel faster now, but it might be Preload doing its magic. I added the noatime option too. Not sure if it's faster, but certainly not slower. 

I'm still concerned about my disk reads though. Might it be a hardware problem?

---

### Post by disturbed1 on 2008-03-14
Try turning off compiz and preload, and see what happens.

**sudo /etc/rc.d/preload stop**

**sudo hdparm -Tt /dev/sda1**

You could also time it with dd
**dd if=/dev/zero of=bin bs=1024 count=200000**

dd if=/dev/zero of=bin bs=1024 count=200000
200000+0 records in
200000+0 records out
204800000 bytes (205 MB) copied, 2.35873 s, 86.8 MB/s


dd if=/dev/zero of=bin bs=1024 count=500000
500000+0 records in
500000+0 records out
512000000 bytes (512 MB) copied, 7.30953 s, 70.0 MB/s


If the file seems slow, you could try a different one. Like jfs or xfs. I have no idea of the best way to convert/resize/reformat one file system to another, other than a reformat and reinstall.

You could create a new partition, format as jfs, mount it, then perform the tests on it. Ext3 has plenty of utilities to resize it. If you go this route, it would save you from a reinstall to a different file system that show the same problems.


It is strange that KDE is blazing fast, and Gnome seems slow. Usually KDE is slow, or they both have speed issues. I seriously doubt it's a hardware issue, because KDE has the performance you want. It seems to be more of a software, and or settings issue to me.

Some other things that can slow down Gnome are the theme, icon set, and background. I once had a background loaded that was a 100mb png file. This caused a noticable slow down. As do some themes.

Perhaps try the default, but ugly ;), Gnome theme with no background. This will rule out some things.


By the way, my system setup is in my sig, and I use Arch64. Arch 32bit runs *almost* the same with an AMD Sempron 3000+, 1gig DDR, nVidia fx5500 agp.

---

### Post by Ub1476 on 2008-03-14
As I said I tried to create a new user, which is using default theme, session etc.. Not much noticeable performance gain, really. Turning off preload does not help either (the opposite in fact). Next time I'll probably try a new file system though. However, I tried this dd command, and results:

For /dev/zero:
```
[kasper@myhost ~]$ dd if=/dev/zero of=bin bs=1024 count=200000
200000+0 records in
200000+0 records out
204800000 bytes (205 MB) copied, 1.78025 s, 115 MB/s

```

For active partition, /dev/sda1:
```
[kasper@myhost ~]$ sudo dd if=/dev/sda1 of=bin bs=1024 count=200000
200000+0 records in
200000+0 records out
204800000 bytes (205 MB) copied, 23.0804 s, 8.9 MB/s
```

I don't know if this is normal?

---

### Post by eljoeb on 2008-03-16
> **deepclutch said:**
> hrmm...some project like kdemod for Gnome also!yeah,hopes so! :-|

Doubtful.  One of the main purposes of KDEMod was to give users an optimized, modular KDE that conforms to the "KISS" philosophy (with some changes to the appearance).  KDE typically a big, interdependent DE; you typically get more crap you aren't going to use with the DE.  KDEMod fixes this.  If I remember right, GNOME is designed with KISS in mind; it's inherently modular.  I really don't know what big changes you could really make to justify a "GNOMEMod" project.  

But hey, who knows.

---

### Post by Rumor on 2008-03-16
> **eljoeb said:**
> If I remember right, GNOME is designed with KISS in mind; it's inherently modular.  I really don't know what big changes you could really make to justify a "GNOMEMod" project.

Correct, it is already modular in nature. The base Gnome 'metapackage' gives you more or less the equivalent of what you get with the base KDEmod package. By that I mean you get a vanilla Gnome. From that point you can install the Gnome extras as you like. I think Arch does a great job with Gnome.

---

### Post by deepclutch on 2008-03-17
Yep it is modular.what I meant was some "performance" enhancement like the way kdemod have.

---

### Post by disturbed1 on 2008-03-17
> **Ub1476 said:**
> 
Any thought on this? I thought KDE (mod or not) was supposed to be large and slightly slower, and Gnome small and faster?

First off, I **HATE** KDE. Just a personal opinion :D

I decided to check out all this KDE Mod stuff. I installed it on an older computer besides my main PC. It's a Celeron 2.0 with an nVidia mx400 and 1gig ram. 

I'm sorry to say, your problem isn't anything that can be *fixed*. KDEMod is just that blazin fast. All there is too it. Nothing wrong with your PC, Gnome, or anything else. It's just that KDEMod is that good.

My Cele 2gig is faster with KDEMod than my dual core Intel, which has 2x the Ram, not mention a faster bus, is with Gnome.

No I won't install KDEMod on my main PC. Yes I despise KDE that much ;).

If you like KDE, I highly advise you to use KDEMod. If you require a few GTK apps, they will install just and run just fine on top of KDE.

I honestly did give KDE a go. Used it for a couple of days. By the time I was done changing the looks, the behavior -stopping that annoying *** Windows like pop messages on everything I close - the Windows like task bar - the windows like everything - setting the preferences to use all my favorite GTK apps - I ended up with..............................Gnome. 

So there's no point in someone like **me** using KDEMod. I'm too much of a Gnome Head :)

---

### Post by deepclutch on 2008-03-18
@disturbed1:is this too low?
> localhost:~# dd if=/dev/zero of=bin bs=1024 count=200000
200000+0 records in
200000+0 records out
204800000 bytes (205 MB) copied, 7.39189 s, 27.7 MB/s

localhost:~# dd if=/dev/zero of=bin bs=1024 count=500000
500000+0 records in
500000+0 records out
512000000 bytes (512 MB) copied, 21.1607 s, 24.2 MB/s

---

### Post by mips on 2008-03-18
> **disturbed1 said:**
> First off, I **HATE** KDE. Just a personal opinion :D

I decided to check out all this KDE Mod stuff. I installed it on an older computer besides my main PC. It's a Celeron 2.0 with an nVidia mx400 and 1gig ram. 

I'm sorry to say, your problem isn't anything that can be *fixed*. KDEMod is just that blazin fast. All there is too it. Nothing wrong with your PC, Gnome, or anything else. It's just that KDEMod is that good.

My Cele 2gig is faster with KDEMod than my dual core Intel, which has 2x the Ram, not mention a faster bus, is with Gnome.

No I won't install KDEMod on my main PC. Yes I despise KDE that much ;).

If you like KDE, I highly advise you to use KDEMod. If you require a few GTK apps, they will install just and run just fine on top of KDE.

I honestly did give KDE a go. Used it for a couple of days. By the time I was done changing the looks, the behavior -stopping that annoying *** Windows like pop messages on everything I close - the Windows like task bar - the windows like everything - setting the preferences to use all my favorite GTK apps - I ended up with..............................Gnome. 

So there's no point in someone like **me** using KDEMod. I'm too much of a Gnome Head :)

What I appreciate about this post is your honesty. You hate KDE but you are honest enought to say kdemod is blazingly fast.

I like KDE and have found KDEmod to be a breath of fresh air. I cannot see myself moving back to normal KDE ever. KDEmod is how KDE should be done originally. Seeing KDEmod is only available on Arch means I'm also sticking with Arch which I like anyway.

---

### Post by Ub1476 on 2008-03-18
Well, I certainly hope there will be performance and speed improvements in GTK3/Gnome3 (which they hopefully has started to plan in secret).:)

---

### Post by deepclutch on 2008-03-18
GTK3?GNOME3? dreams baby! :lol: !
well,I really hope so!
> **mips said:**
> What I appreciate about this post is your honesty. You hate KDE but you are honest enought to say kdemod is blazingly fast.

I like KDE and have found KDEmod to be a breath of fresh air. I cannot see myself moving back to normal KDE ever. KDEmod is how KDE should be done originally. Seeing KDEmod is only available on Arch means I'm also sticking with Arch which I like anyway.
I too am a fan of kdemod.while I still hopes kdemod project should be the "official" kde for archlinux.is a waste of developers time and energy just doing 2 kde's :evil: instead ppl shud support @funkyou(kdemod) to develop kdemod.

Well,even I am a Gnome guy!!:D I really wants a "gnome-optimized" by them :D

---

### Post by aeto on 2008-03-20
Qt is faster and more efficient; better code. I've nothing against GTK+ nor GNOME, but Qt and KDE are just _better_ in every way.

Oh yeah, figure this one out: GURGHNOME

 :mrgreen:

---

