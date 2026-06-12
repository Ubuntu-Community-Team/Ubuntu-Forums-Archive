---
title: "automount usb device"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by siehtschlecht on 2007-05-02
Come on Folks!
This problem is discussed a long time and nobody can solve it.
After updating to feisty my external usb-hd with fat32 (and from many other users too) wont mount automatically. My usb-Sticks will .
With dapper and edgy it was no problem: Plug in, new icon on my desktop and open the devices.
Now i make a complete new install, no changes.

My fdisk -l:
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2431    19526976    7  HPFS/NTFS
/dev/sda2            2432        4757    18683595   83  Linux
/dev/sda3            4758        4864      859477+   5  Extended
/dev/sda5            4758        4864      859446   82  Linux swap / Solaris

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12161    97683201    b  W95 FAT32

I don want to mount it manually everytime and then try to get sudo-rights to write on it.
I only have this laptop, so i need the external hd for saving. I've searched the forum and tried all possible solutions without luck.
I dont understand why this is such a problem. None of the "Cups of ubuntu" tells what went wrong. in older versions it was no problem!
Please solve the problem, so it is as easy as in edgy or tell us what to do.
Greets, siehtschlecht

---

### Post by obbe on 2007-05-02
have you checked in system-preferences-unit and support....?

---

### Post by siehtschlecht on 2007-05-03
Yes, i think i have checked all. I´ve read all forum entries. No help.

---

### Post by SamChameleon on 2007-05-03
Perhaps your problem is similar to the one discussed [here]("http://ubuntuforums.org/showpost.php?p=2580033&postcount=27")?

---

### Post by siehtschlecht on 2007-05-03
No, this doesnt fit to me. I have no such errors.
Anyone with new help?

---

### Post by Wiebelhaus on 2007-05-03
> **siehtschlecht said:**
> No, this doesnt fit to me. I have no such errors.
Anyone with new help?


Automatix read / write NTFS & Fat32 Automounter installed?

---

### Post by siehtschlecht on 2007-05-04
No! But i will try on the weekend.
Thank you.
But, why do you think one should use automatix? It should  work automatically! Or am i wrong?

---

### Post by siehtschlecht on 2007-05-05
The automount option from automatix did not change anything. Now way to work the external harddrive fine and comfortable. I ma very disappointed.

---

### Post by Conan_the_Librarian on 2007-05-05
I had a problem with external volumes not being mounted too. In my case it was due to a gparted crash where it did not remove a file it uses to prevent disks being mounted by HAL while parted is in operation. 

Check to see if the file :/usr/share/hal/fdi/policy/gparted-disable-automount.fdi exists and, if so, delete it. Restart hal (sudo /etc/init.d/dbus restart) and plug drives in again. That should take of that problem, if indeed that is your problem.

---

### Post by Bloch on 2007-05-05
I have the same problem - memory sticks will automount, but the external hard drive does not.
The problem was compunded when I put an entry in fstab - memory sticks would not mount, there would be an automatic error message when I plugged one in. I fiddled about for a while and now I am satisfied with automounting of memory sticks and I made an executable file called "mount external drive" with the command:
```
gksudo mount -t vfat /dev/sda1 /media/EXTERNAL
```

But for a long time I didn't have any automounting.

---

### Post by t2000kw on 2007-05-05
> **siehtschlecht said:**
> No, this doesnt fit to me. I have no such errors.
Anyone with new help?

In Feisty there is an experimental USP_SUSPEND implementation that causes problems with some (maybe many or all) USB devices. It's enabled by default, and unless you rebuild the kernel and turn it off it is there to support Laptops, whether you want it or not. 

Someone posted a fixed kernel where that function was disabled. You'll need to read through the posts to find the place to download the fixed kernel if you want it--and read through all of the posts first to see where to get it--the location has been changed and possibly some a=other changes you'll need to know about. The bug report posts are mainly about USB scanners not working in Fiesty but they were in Edgy. Mine worked in SuSE but not in Feisty. Some people reported other USB-related problems. The information about the fixed kernel starts on May 1st posts. The scanbuttond posts begin on April 27th. 

I installed the fixed kernel but had problems of the video kind and didn't want to install non-restricted drivers, had problems removing the kernel (I'm new to this), and subsequently screwed up my /home partition (I was keeping /home separate from the / partition). I'm mostly back in business, fortunately. Copied my bookmarks and Windows email program folder over to the default /home directory, reinstalled Wine and then my email program, which left the files intact so I have my email back.

Anyway, there is also a fix to use a program called scanbuttond, which is easy enough to try, even though it's for a scanner.

The posts that cover both of these ideas is here: 

[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/85488](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/85488)

If you want to try the scanbuttond work-around, you need to follow these directions. If you know how to write a script that runs when you boot, you could make it automatically load instead of having to open a terminal when you log into Ubuntu. 

The fix does not work with all scanning software, as you will read in the posts. It may or may not hold the port open for your device. 

Even though your problem does not involve a scanner, it seems related because of the USB port being involved. The scanbuttond trick is worth a try. 
**************************************************************************
This was taken from the bug report posts I mentioned earlier:

Some more explanation about scan button daemon:

install the software
sudo aptitude install scanbuttond

now start the daemon as normal user
scanbuttond.

after this my epson scanner with snapscan backend is working fine.

But what is going on?
the daemon allways watches for the scanner and the usb did not suspend.

the real function of this software is to look for the buttons on the scanner and do something usefull lke 
scanning -> printing - scanning -> email

---

### Post by crmccreary on 2007-05-06
Same story. Found a post, [http://ubuntuforums.org/showpost.php?p=2580033&postcount=27](http://ubuntuforums.org/showpost.php?p=2580033&postcount=27)
that fixed it right up. In short:

sudo modprobe -r ehci_hcd

Don't know what happened nor how long the fix will last.
Edit/Delete Message
On further research, it appears that this (my) problem is a kernel bug. I found that adding irqpoll as a boot option is a more permanent fix. I also read that this may slow the system (true?)
Relevant section of menu.lst:
## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=cf89718b-0b16-4131-a8d1-4932be9aef95 ro quiet splash irqpoll
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

---

### Post by siehtschlecht on 2007-05-06
Thank you all!
1. _Conan_, the file :/usr/share/hal/fdi/policy/gparted-disable-automount.fdi does not exist.
2. _Bloch_, this will be a possible option, but i have to get sudo rights for saving on my hd. I think it should work automatically. If i can get no other ways i will do so.
3. _crmccreary_, this doesnt fix my problem. I get no reaction at all.
4. _t200kw_, this sounds very interesting. But i fear to break my system, because i am not very firm in programming ubuntu. Is it worth to wait for an automatic update?

---

### Post by t2000kw on 2007-05-06
> **siehtschlecht said:**
> .
4. _t200kw_, this sounds very interesting. But i fear to break my system, because i am not very firm in programming ubuntu. Is it worth to wait for an automatic update?

The scanbuttond thing is safe enough and easy to install. If it doesn't work for you, just don't run the command and it won't be running in the background. It doesn't appear to slow my system down, though. 

I don't have it load at startup since I don't know how to do that yet. But you can load it in terminal once it's installed. If it works, it's the least invasive approach I've seen so far, and the simplest to implement, no compiling or any strange (to newbies like us) actions required. 

---------------------------------------------------------
install the software
sudo aptitude install scanbuttond

(the sudo command temprarily gives you root/superuser privileges (equivalent of administrator in Windows XP)

now start the daemon as normal user in terminal
scanbuttond

---

### Post by siehtschlecht on 2007-05-07
I installed scanbuttond, but it changed nothing. Thank you.

---

### Post by t2000kw on 2007-05-07
> **siehtschlecht said:**
> I installed scanbuttond, but it changed nothing. Thank you.

Well. it was worth a try. Sorry to hear that it didn't work for your problem. But now you can buy a scanner that has buttons on the front! Not that it will work properly with all scanning software yet, though.

My inside source tells me that this USB problem will likely be fixed in the next release, Gutsy Gibbons. Though that will be a while. He tells me that there is quite a bit of chatter about this in Feisty in the bug report forums right now. 

My guess is that it will be stable enough to try around the end of August, but late October is the official release time. 

You may not want to wait that long, and you also probably don't want to use the hacked kernel someone posted. It's better to compile your own and disable the USB_SUSPEND "feature" if you want to learn how to do it (I am not one to explain it as it was quite a long time ago when I did it, and I followed someone else's directions.)

[https://wiki.ubuntu.com/GutsyReleaseSchedule](https://wiki.ubuntu.com/GutsyReleaseSchedule)

---

### Post by siehtschlecht on 2007-05-09
Thank you t2000kw!
This is the first time someone told me definitely that somethings wrong in feisty and it is not necassariely (iis it spelled correct?) my fault.
So i have to downgrade to edgy or try to manage the problem so long.
Maybe in a while somone find a solution for it. Hacking or compiling is to high for me.
If you know some news please let me know too.

---

### Post by t2000kw on 2007-05-09
> **siehtschlecht said:**
> Thank you t2000kw!
This is the first time someone told me definitely that somethings wrong in feisty and it is not necassariely (iis it spelled correct?) my fault.
So i have to downgrade to edgy or try to manage the problem so long.
Maybe in a while somone find a solution for it. Hacking or compiling is to high for me.
If you know some news please let me know too.

PM me with your email address and I'll put it in my address book. (I think you can do private messages here.)

Then I can keep you posted. I have a Ubuntu tester who I've made friends with that will keep me posted, too. 

Recompiling actually might be simpler than going back to Edgy. I'm not interested in doing that but I'll see what I can dig up on the "how-to" on it to see how difficult it is. Gping back may "break" the applications you've installed if they are tailored to feisty. That's why, in your /etc/apt/sources.list you have "feisty" everywhere, as in mine below. (Mine is not the default, and I do have Automagix installed.) There might be a lot of work to do to go back one version of the kernel. Not sure. If you're thinking seriously about that, I would ask questions in another thread, and please let me know when you do. I might not want to do that, but I'd like to know how to understand more about what goes on under the hood of Linux. 

If you don't mind just backing up the stuff you want to keep (data files like letters, etc.), you could just reformat by installing Edgy. It would erase Feisty and everything you saved in it.

A good book I found is Ubuntu Linux Bible. Amazon.com has it and it's shipped free is you use super saver shipping (not 2-day or overnight). It got here in 4-5 days. It covers edgy (no book will likely cover the current version since it changes every 6 months).

Don

---------------------------------------------------

####################################
 ### Official Ubuntu Repositories ###
 ####################################
 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main multiverse universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe

#end of Dean's sources.list
#anything after this was added by automagix or another program or myself

deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/debian](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/debian) ./
deb-src [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu) ./

deb [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty fonts
deb-src [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty fonts

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END

---

### Post by TNBY963 on 2007-05-09
Hi All,

this is my first post, i'm normally just someone who likes to read these forums.

I too am having prob with my external media. Mp3 players, external harddisks, and even my cdrom drive. I never had any prob like this in dapper, edgy or the feisty fawn live cd. 
[rant]
Look, I really like Ubuntu, it made me see things more clearly about Windows (wich I don't run anymore) and it has made me aware of OSS. I'm now a firm believer of OSS and I promote it's programs or even Linux to many of my students, I even use it in class.
But, now I read in this thread that this issue won't be fixed until the relaese of Gutsy Gibbon! Feisty, how much I love it, is pretty useless to me now since all my data is on my external disks and I use my mp3 players alot.
I thought the strenght of OSS was that problems could be fixed faster?
[/rant]

I'm sorry to rant like this. I understand the hard work that makes up a release like this and that most of the people who do the work do it in their free time. So really, no hard feelings. I just feel bad that I can't use the latest version of Ubuntu since all the other things run really great.

This week-end I'll reïnstall dapper I guess, because IMHO that one was the most stable.
It's just a bummer that Ubuntu studio will be based on feisty so I'll have these problems again.

Thanks for letting me blow off steam.

Gert

---

### Post by t2000kw on 2007-05-09
You are correct, my friend! However, Windows has had some serious problems in the past, too. 

There may be an official temporary solution to this, but I haven't read about any so far. 

You can save your important documents to another partition, reinstall Edgy, then copy your important documents back to the Edgy installation. That would give you your USB stuff back. 

Most companies won't install the latest version of anything until a year or so later when all the bad (and good) reports are in on the OS, program, etc. We as individuals like to hop on the latest things thinking that there aren't going to be any problems. Not that it's our fault, but companies take a much more practical, though less exciting approach. They miss out on new features during the wait, too. 

I don't know which version of SuSE it was that I installed, but it supported the scanner I have. But the suport forums were like being in a desert. No one around.

---

### Post by TNBY963 on 2007-05-16
Hello all,

I think my problem is fixed. I reinstalled Feisty last Saturday and then added the ubuntuStudio repo's and installed everything from that. It worked great, I had all the apps, the theme, and the lowlatency kernel. Now this is where it gets interesting.
I have almost no problems with external media whatsoever. My external disks mount without probs (automatically) and I can burn cd's and DVD's. I only have to unmount manually, but that's not a big deal. I waited with this post, because I wanted to be absolutely sure.

I think it's because the new kernel. Maybe the 'Studio guys changed something that had to do with usb. I don't know, but it works great now. The only other things I can think of now that I did differently was that I didn't install the ntfs3g tools with automatix and I didn't try to put it to sleep (which has never worked on my laptop).

So, if you have this problem and want to fix it maybe try to install the whole ubuntuStudio package or maybe just the lowlatency kernel. You can find it in synaptic.

I hope things will stay the same with me now (knock on wood) and that maybe others are helped with this post.

Greetz

Gert

---

### Post by siehtschlecht on 2007-05-16
Sounds great!
I´ll try tomorrow.
Thanks

---

### Post by t2000kw on 2007-05-16
I just got word that the USB problem will be fixed in Gutsy. The newest kernel (2.6.21) has the fix but it's a bit early to jump into Gutsy.

---

### Post by siehtschlecht on 2007-05-18
Ok, first i tried the lowlatency-package from synaptics without success. Then i did the ubuntuStudio-package and again nothing changed:(.

---

### Post by TNBY963 on 2007-05-18
Ah, that sucks man.

Are you sure you booted the lowlatency kernel? This really has me puzzled :confused:, because external media support is still going strong (knock on wood)
The only other thing I did differently this time was that there were no external drives mounted during install.

I really can't think of anything else. Sorry I can't help you further.  :(

Greetz

Gert

---

