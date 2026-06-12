---
title: "Ubuntu much slower than Kubuntu??"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by pkiula on 2008-02-27
Hi. I have a Dell Latitude corporate laptop, C810. It used to work fine with Windows XP. Then I tried Kubuntu. I didn't like the interface, but it was fast enough even in Kubuntu. 

But then I installed Ubuntu on the same laptop, and absolutely love the more intelligent interface, but it works much slower! I mean, really slow -- the windows make concentric squares while minimizing and all that. 

This laptop has 512 MB RAM, 40 GB hard disk (which shows up as 60% full -- just how big is Ubuntu??) and Intel Pentium IV I think. It is three years old.

While installing, I chose the option that says "Use entire disk" so I presume entire disk is with Ubuntu. 

I only need to use Firefox, Picasa, Skype, and Thunderbird. Not much to ask is it. Any idea what's wrong? Should I uninstall any stuff or what else can I do to make the speed faster? 

I am on Ubuntu 7.10, the latest one.

---

### Post by uhappo on 2008-02-27
My desktop machine is old...

[[IMG]http://img149.imageshack.us/img149/6338/screenshotoa6.th.png[/IMG]](http://img149.imageshack.us/my.php?image=screenshotoa6.png)

But I have no troubles runnin Ubuntu.

Well, if I'm trying to do too much simultaneously, I get slowmotion.

Still, I'm a happy Ubuntu user.

---

### Post by mixmaster on 2008-02-27
You could try Xubuntu, which is generally accepted to be the preferred release for older machines,

---

### Post by Ubuntized! on 2008-02-27
i think you have some problems with video card drivers...and with something else too!Dunno what though !I'd suggest you to reinstall ubuntu!

---

### Post by Archmage on 2008-02-27
I think there is something defently wrong. I did use Ubuntu 7.10 on a AMD 600 with 512 MB and it was working okay.

---

### Post by Ubuntized! on 2008-02-27
Ok Xubuntu could be a nice choice!but i think it is strange!I have ubuntu on my box on a 20G partition (I do dual boot with XP:()!It runs like a charm!It takes far less that 4 gigs!Very strange!Reinstall would be my suggestion!and before doing that run a disk check for errors!the install disc of course!

---

### Post by TheDilettante on 2008-02-27
Other though is maybe somehow you have Desktop Effects enabled (System-> Preferences -> Appearance)?

---

### Post by KCormier on 2008-02-27
over 60% of a 40 gig drive is very odd.  Double check the restricted driver manager and make sure you have all your binary drivers installed!

---

### Post by kirenpillay on 2008-02-27
I've been using Ubuntu for 2 weeks now. A common slowdown is the trackerd daemon, it can eat the CPU up for a while, and the system becomes unresponsive. There are fixes on the forum for this. (I personally just kill the trackerd daemon (sudo pkill -STOP trackerd) , only side-effect is that search stops working).

I noticed that also, if one disconnects a connected network cable, the system practically comes to a halt. (Don't know if anyone else experiences this).

Openoffice also does something strange, its chews up the CPU up to 100% sometimes, I'm trying to figure out what's causing this, this started happening recently.

Have a look at these, you can use the "top" command in a terminal, and press C to figure out the process using your CPU.

---

### Post by gali98 on 2008-02-27
Yeah I think something may be wrong. Bad video driver or you have desktop effects enabled like the guy above me said.
I have a pentium 2 (overclocked to 412 mhz) and it runs ubuntu better than you would expect.
It also runs about 5 times better than kubuntu.
Kory

---

### Post by articpenguin on 2008-02-27
well he has a duron, the durons are the lowend ones. I belive they only have 64KB l2 cache.

---

### Post by uhappo on 2008-02-27
Yeah, Duron has 64KB l2 cache

---

### Post by DarkYang on 2008-02-27
> **articpenguin said:**
> well he has a duron, the durons are the lowend ones. I belive they only have 64KB l2 cache.

He has a Pentium processor, it is uhappo (the guy that replied first) that has the Duron processor. But yeah, sounds to me that you most likely have Desktop Effects enabled. Ubuntu saying that 60% of your 40GB drive is very odd, I don't know about that one.

---

### Post by redgilda on 2008-03-29
hmm at first I thought that Ubuntu is not running as fast as it could be (for sure its slower than the Win XP I have on another partition) but I just assumed thats how it should be.... - meaning that I also get the black squares when a window is being minimized - and now I read that should not be the case? :>

I have 1GB Ram,
AMD Athlon 64 Processor 3000+
Release 8.04
Kernel 2.6.24-12-Generic
Gnome 2.22

so is that normal that it's quite slow? I dont even have many things open - just Firefox, Pidgin and some nautilus window with folders... 

I have the special effects disabled... other than that I didnt have any problems with installation - I didnt even install any specific drivers for the graphic card or anything - should I have perhaps? I have an ATI Radeon.. old one I think 7200 ?

Any feedback appreciated.

---

### Post by waspbr on 2008-03-29
In my experience, ubuntu is in fact a little slow then Kubuntu, this is probably because of compiz/ awn  and all the other eye candy, but it is still quite snappy. I use my kubuntu for gaming and stuff since I don' t use any eye candy in  kubuntu.(I installed the kubuntu desktop through synaptic in ubuntu). I also have the xubuntu desktop which I use for heavy duty computations.

I am on gutsy @ 
Custom made desktop
Athlon XP +3000
2GB DDR
GF 6200 series 128 MB.

also on hardy @ 
Hp pavilion tx1320us laptop
Athlon X2 64 2.2GHz
GF Go 6000 series dynamic memory up to 384
2 GB DDR2


on a last note, hardy seems to be faster than gutsy imo

---

### Post by redgilda on 2008-03-30
hmm I just wonder if your idea of 'slowness' is the same as mine heh. Its kinda hard to compare when we're not sitting in the same room :P

So like, do you get the black squares when minimizing windows all the time for example?

And where can I check if my graphic card drives are installed correctly? (I didnt install anything separately)

---

### Post by pkiula on 2008-03-30
Yes, Ubuntu is slow, period. Much slower than Windows XP and a bit slower than Kubuntu. 

I managed to install the nvidia drivers (not for the faint of heart -- and if you want to do so, pls search for my name on this forum, that thread will come up). 

But it doesn't help much. Ubuntu is just slower in its visual interface. I suppose the open source bit is nice and all, but making a fast visual UI is not easy. You have to live with it I suppose.

---

### Post by Mazza558 on 2008-03-30
Yeah, I agree with pkiula. Hardy Heron is no better really, as the new ATI drivers are actually slower than the XGL ones, and have all sorts of problems with 2D rendering, and 3D apps flickering. I'd go so far to say that Vista is faster on this laptop than Ubuntu, which is a shame. I prefer Ubuntu due to the repositories and the other benefits mentioned countless times. Ubuntu for me would be so much better if the FOSS ATI drivers were improved.

---

### Post by psycosmyth on 2008-03-30
I'm running an old Celeron and it's plenty quick. My old Dell has Kubuntu....wait....I chiselled that away and ported Xubuntu via synaptic. Anywho, it runs quick. I had better speed from KDE but I also did well with Kiwi which is Ubuntu Gnome with some tweaks. Gnome will always be a little slower but not enough to make me cry. You have an odd issue with the drive, like everyone else said, re-install but more carefully this time.

---

### Post by armandh on 2008-03-30
with a desktop I had to move the refresh rate back down with a small mem onboard video
fast enough now

---

### Post by redgilda on 2008-03-30
> **armandh said:**
> with a desktop I had to move the refresh rate back down with a small mem onboard video
fast enough now
You mean the refresh rate of the screen right? I already noticed its quite low on ubuntu - 65. whereas on Windows I have it up at 75-80 (same screen of course ;-)).

---

### Post by crjackson on 2008-03-30
I'm using Gutsy and I can say that it's close to XP speed wise after some tweaking.  There are some exceptions however.  Applications don't launch as fast but I not sure if that's interface UI, File System, or application related.  I suspect it's a combination of factors.

That said, I turn off animations and turn on reduced resources setting in the gconf-editor.  Then I tune the file system by turning off atime (using noatime), and enabling datawritback in the fstab.

Next after rebooting I turn off all drive indexing and even disable the tracker service.

I also like to speed up my menus in both Ubuntu and Firefox.

Once these tweaks are done, things are pretty snappy for me provide I DON'T TURN ON DESKTOP EFFECTS.

---

### Post by redgilda on 2008-03-30
> **crjackson said:**
> That said, I turn off animations and turn on reduced resources setting in the gconf-editor.  Then I tune the file system by turning off atime (using noatime), and enabling datawritback in the fstab.

yeah but to do that, one has to know what to do - like a common user that just installed Ubuntu - wouldnt know how to do all these things (unless given a nice step-by-step command guidelines hehe)

---

### Post by prshah on 2008-03-30
> **pkiula said:**
> 
This laptop has 512 MB RAM, 40 GB hard disk (which shows up as 60% full -- just how big is Ubuntu??) and Intel Pentium IV I think. It is three years old.


60% is too much, don't think it's possible. open a terminal, and post output of ```
sudo fdisk -l
```

Specs wise the machine is OK for ubuntu, and I definitely find ubuntu faster than Kubuntu.

Looks like you are running off the old VESA driver ```
 cat /etc/X11/xorg.conf | grep -i vesa 
``` If it gives you anything, that means vesa, if there is no output it will be better if you use ```
top
``` and paste the screenshot here.

If you are running vesa, we can tell you how to change.

---

### Post by crjackson on 2008-03-30
> **redgilda said:**
> yeah but to do that, one has to know what to do - like a common user that just installed Ubuntu - wouldnt know how to do all these things (unless given a nice step-by-step command guidelines hehe)

Okay this is where I started [Optimize Ubuntu Feisty Fawn for Speed]("http://news.softpedia.com/news/Optimize-Ubuntu-Feisty-Fawn-for-Speed-53836.shtml")

It works fine in Gutsy and probably Hardy too.

For Firefox tweaks look [HERE]("http://www.ubuntugeek.com/speed-up-firefox-web-browser.html") and for Gnome Menu Tweaks look [HERE]("http://lifehacker.com/software/linux-tip/speed-up-gnome-menu-269934.php")

Open up a terminal and past this in:
```
gconf-editor
```

From there navigate to /apps/panel/global/enable_animations and uncheck the enable_animations check box.
Then goto /apps/panel/global/enable_animations and do the same.

Next find /desktop/gnome/interface and check off to enable accessibility


This should get you started.  I've go to run out right now, so I'll check back in later and post some other tweak instructions.

---

### Post by redgilda on 2008-03-31
wow, thanks a lot for these :) I did all of them already :) Will have to use the pc a bit more to see if there's any difference but I think there is already! so thanks a lot!

---

### Post by crjackson on 2008-04-01
> **redgilda said:**
> wow, thanks a lot for these :) I did all of them already :) Will have to use the pc a bit more to see if there's any difference but I think there is already! so thanks a lot!

You are welcome.  If this does the trick for you please don't forget to mark the thread solved and click the little star icon next to the quote button on the way out the door.

---

### Post by redgilda on 2008-04-01
> **crjackson said:**
> You are welcome.  If this does the trick for you please don't forget to mark the thread solved and click the little star icon next to the quote button on the way out the door.
Well, I don't think it got THAT much faster to be honest - and my Firefox keeps freezing all the time actually, I guess I'll try to change the settings back... I guess I also have to find some topics about the graphic card drivers or something... 

Also - I was not the originator of the post so I can't really change the topic or anything ;-)

---

