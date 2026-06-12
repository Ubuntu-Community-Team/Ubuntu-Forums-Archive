---
title: "Running XP programs on Ubuntu"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by cobaltinfinity on 2007-11-07
This is a total newbie question, but I may as well get it over with. 

As Ubuntu will let me access all the XP stuff on my other hard drive without any fuss (so I can transfer music files, documents etc.), will I similarly be able to transfer any programs, i.e. executable files over from there and simply run them on Ubuntu? Or is this against every principle of software design known to mankind, something akin to trying to grow plants on the moon?

---

### Post by anemptygun on 2007-11-07
> **cobaltinfinity said:**
> ...Or is this against every principle of software design known to mankind, something akin to trying to grow plants on the moon?

lol. quite funny. I wouldn't say its like growing plants on the moon. But unfortunately you will not be able to use any of the programs that you used on windows in ubuntu, unless.... you use an emulator such as wine ( winehq.org ). But first i would recommend looking around in the Add/Remove Programs. Their is most likely an alternative ubuntu native application that you will find suitable.

Happy hunting:KS

---

### Post by Technoviking on 2007-11-07
You can try Wine, which runs many Windows apps under Linux. But most will have to be installed under Wine, you may not be able to run the Windows .exe directly from Wine.

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

Ubuntu can now read and write to Windows NTFS and FAT volumes.

---

### Post by bakeneko on 2007-11-07
If you encounter problems trying to run a particular application, you might check the Wine Application DB [http://appdb.winehq.org/](http://appdb.winehq.org/) and read about other users' experience.

---

### Post by Maestro23 on 2007-11-07
> **Mike said:**
> You can try Wine, which runs many Windows apps under Linux. But most will have to be installed under Wine, you may not be able to run the Windows .exe directly from Wine.

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

Ubuntu can now read and write to Windows NTFS and FAT volumes.

Can also run Windows vitrually thur something like Vmware or Virtual Box.

Vmware: [http://www.vmware.com/](http://www.vmware.com/)

Virtual Box: [http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by cobaltinfinity on 2007-11-07
Does running windows programs via one of those emulation methods naturally make slighter higher demands on your system, than if you were to simply run it natively in windows? Or is the difference negligible? 

Thanks for the help.

---

### Post by Maestro23 on 2007-11-07
> **cobaltinfinity said:**
> Does running windows programs via one of those emulation methods naturally make slighter higher demands on your system, than if you were to simply run it natively in windows? Or is the difference negligible? 

Thanks for the help.

Depends on your system specs.  It is going to tax the system a little more because the programs are going thru an emulator, rather then running natively.  If you system specs are good, you shouldn't see take that much of a performance hit.

---

### Post by anemptygun on 2007-11-07
> **cobaltinfinity said:**
> Does running windows programs via one of those emulation methods naturally make slighter higher demands on your system, than if you were to simply run it natively in windows?

yes your performance will decrease when running an emulator. But it's all realtive to what you are doing, games, itunes..

but the beefier the system the better ;)

---

### Post by lazyart on 2007-11-07
This is much like asking "can I run a Linux program in WIndows?"  You might be able to with WINE, but don't be surprised if it doesnt work correctly.  What programs are you trying to run?

---

### Post by anemptygun on 2007-11-07
Btw I have heard nothing but good things about Vmware: [http://www.vmware.com/](http://www.vmware.com/)

definitely check them out.

---

### Post by m0rphex on 2007-11-07
What windows programs do you want to run in the first place? Maybe you could find linux alternatives before you start an epiq quest into this emulation world :)

---

### Post by cobaltinfinity on 2007-11-07
> **lazyart said:**
> This is much like asking "can I run a Linux program in WIndows?"  You might be able to with WINE, but don't be surprised if it doesnt work correctly.  What programs are you trying to run?

There's nothing specific really, and in most cases I've been able to get hold of analogous programs. I'd just like to know how to do the whole emulation thing in case it becomes necessary at any point. 

Thanks for the responses anyway, I'll have to get experimenting with WINE! :)

---

### Post by anemptygun on 2007-11-07
no prob.

---

### Post by underdog512 on 2007-11-07
to sum up, ubuntu will read your ntfs (windows) partition just fine.  As far as documents, music, and other files you will find that alot of the programs that ubuntu comes with out of the box will handle these files just fine (you may have to plugins but that is easy).

---

### Post by tombott on 2007-11-07
Sorry just for your info Wine is not an Emulator.

Wine is an Open Source implementation of the Windows API on top of X and Unix

[More info]("http://www.winehq.org/site/myths")

I use Wine and [Crossover]("http://www.codeweavers.com/products/") for running some 3rd party windows applications that there is no Ubuntu alternative for.

---

### Post by SoloSalsa on 2007-11-07
> **tombott said:**
> Sorry just for your info Wine is not an Emulator.
I was just going to point that out myself...  But one could think of it as a 'soft emulator'...  VMware is partially an emulator, though.

---

### Post by hogwartsnigel on 2007-11-07
Hi all,
this is going to sound a little lame but the only thing that is keeping me from ceasing to dual boot is the following.....
My kids use Encyclopedia Britannica Win and Mac only so I can use wine to run this on my home system?
To install under wine I simply open wine and install from there I presume??

Any recommendations on the best DVD authoring tool
Any Recommendations on the best dvd shrinking tool?

All help greatly appreciated.
Gotta love Linux.....converted 4 out of 6 pcs and counting, converted 3 friends today to try linux.

Nigel

---

### Post by tombott on 2007-11-07
> **hogwartsnigel said:**
> Hi all,
this is going to sound a little lame but the only thing that is keeping me from ceasing to dual boot is the following.....
My kids use Encyclopedia Britannica Win and Mac only so I can use wine to run this on my home system?
To install under wine I simply open wine and install from there I presume??

Any recommendations on the best DVD authoring tool
Any Recommendations on the best dvd shrinking tool?

All help greatly appreciated.
Gotta love Linux.....converted 4 out of 6 pcs and counting, converted 3 friends today to try linux.

Nigel


There are some lovely DVD Authoring packages available for linux check out [GetDeb]("http://www.getdeb.net/category.php?id=12") for more info

DeVeDe is good as is ManDVD

---

### Post by 3rdalbum on 2007-11-07
> **tombott said:**
> There are some lovely DVD Authoring packages available for linux check out [GetDeb]("http://www.getdeb.net/category.php?id=12") for more info

DeVeDe is good as is ManDVD

This isn't a personal judgement, but no; it isn't.

ManDVD is a DVD authoring environment.

DeVeDe really just does transcoding.

For DVD shrinking, check out k9copy.

---

### Post by tombott on 2007-11-07
> **3rdalbum said:**
> This isn't a personal judgement, but no; it isn't.

ManDVD is a DVD authoring environment.

DeVeDe really just does transcoding.

For DVD shrinking, check out k9copy.


Well personal opinions rule!

The OP asked for DVD Authoring and Shrinking packages, i pointed him in the direction of some tools i use for authoring.

---

### Post by hogwartsnigel on 2007-11-08
All help greatly appreciated guys...and i sincerally meen ALL help:).
Thanks for the info will check them out.
Have used creative suite 3, WIN(urrrrgggghhhh)DVD Platinum and NERO8 previous. Oh and DVD shrink for shrinking...funny that.
Thanks Again
Having fun

Nigel

---

