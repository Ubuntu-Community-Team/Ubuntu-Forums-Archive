---
title: "I thought xubuntu was supposed to be fast"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by Exershio on 2007-05-31
I recently (yesterday) installed Xubuntu, and I'm quite disappointed with it. I thought it was supposed to be more responsive and faster than Windows XP, but it turns out to be quite the opposite! Is there a problem with my computer/setup, or is Xubuntu just slower than Windows XP in general?

My system specs:
2ghz intel p4 processor
256mb ram
onboard graphics card

Programs I'm running at the moment:
Mozilla Firefox 2.0.0.3
Amarok 1.4
Pidgin 2.0.1

I'm also running a resolution of 1152x768 with a refresh rate of 75hz (dont know if that would affect performance at all).

Can anybody help me find out what's wrong?

---

### Post by smoker on 2007-05-31
hme, xubuntu should fly with those pc specs, have you given it a big enough partition to play with, and a decent swap partition?

---

### Post by Exershio on 2007-05-31
I don't know a whole lot about that kind of stuff, so I just had it erase my 40gb HDD and setup the partions automatically.

Any way I can check it to see if it's big enough, and change it if it isn't?

---

### Post by smoker on 2007-05-31
hi, if this is your sole os, then i would imagine you have plenty partition space and swap. can you say if it is slow to boot, or slow in general use once booted, or slow with boot, running, and shutdown?

also, did you do a check on the integrity of you install cd, perhaps a bad install due to a disk problem may be causing trouble?

---

### Post by Exershio on 2007-05-31
Well, I used a Xubuntu 6.06 install CD. Once it was installed, the first thing I did was use the update manager to go from 6.06 -> 7.04.

It's just not as fast as I thought it would be. It's slower than Windows XP. It doesn't take forever to boot, it just runs a little slow when using it. I figured it would be faster than Windows since it's such a light OS.

And yes, this is my sole OS.

---

### Post by smoker on 2007-05-31
hi, i'm not sure what the problem is then, i installed xubuntu on a P3 500 with 256 ram a week ago, and it flies, much faster than the windows 2000 that it replaced, that was a straight install of 7.04 though, so, perhaps you had a problem with the upgrade,

sorry i can't offer more help, maybe someone more knowledgable about xubuntu could offer more,

---

### Post by Exershio on 2007-05-31
Thanks a ton for trying anyways. I'll download the Xubuntu 7.04 ISO and just do a fresh clean installation. How would you recommend I divide the partitions?

I have a 40gb hard drive - I'm using the entire hard drive.

---

### Post by Benbow on 2007-05-31
I am fairly new myself, but I would think that 256mb of ram is a little low. 512mb would be a reasonable minimum for good performance.

---

### Post by smoker on 2007-05-31
> **Exershio said:**
> Thanks a ton for trying anyways. I'll download the Xubuntu 7.04 ISO and just do a fresh clean installation. How would you recommend I divide the partitions?

I have a 40gb hard drive - I'm using the entire hard drive.

hi, i would just let the installer take care of partitioning then, you should end up with a swap around twice your ram, and the rest for the os.

>  I am fairly new myself, but I would think that 256mb of ram is a little low. 512mb would be a reasonable minimum for good performance.

256 is fine for xubuntu, i believe you can run it ok with 128, but obviously, the more the better,

best of luck with the reinstall, and please post back it you find the new install of 7.04 is faster than at present,

cheers:D

---

### Post by sessine on 2007-05-31
> **Exershio said:**
> I recently (yesterday) installed Xubuntu, and I'm quite disappointed with it. I thought it was supposed to be more responsive and faster than Windows XP, but it turns out to be quite the opposite! Is there a problem with my computer/setup, or is Xubuntu just slower than Windows XP in general?

My system specs:
2ghz intel p4 processor
256mb ram
onboard graphics card

Programs I'm running at the moment:
Mozilla Firefox 2.0.0.3
Amarok 1.4
Pidgin 2.0.1

I'm also running a resolution of 1152x768 with a refresh rate of 75hz (dont know if that would affect performance at all).

Can anybody help me find out what's wrong?

I see that you are using Firefox (a Gnome/gtk app) and Amarok ( a KDE/qt app), this means that you need to load both the gtk AND qt libraries into memory if you run them both at the same time.  You may find that sticking to just gtk apps may make things go a bit quicker as I think XFCE also use gtk.

---

### Post by Exershio on 2007-05-31
> **sessine said:**
> I see that you are using Firefox (a Gnome/gtk app) and Amarok ( a KDE/qt app), this means that you need to load both the gtk AND qt libraries into memory if you run them both at the same time.  You may find that sticking to just gtk apps may make things go a bit quicker as I think XFCE also use gtk.
Well I can't find any decent media players besides Amarok. Are there any other good ones?

Also, what about web browsers? I love firefox because of the adblock extensions, and I wouldn't use another web browser without it. So, any recommendations?

---

### Post by dolphin_oracle on 2007-05-31
opera is supposedly faster on xubuntu, but i haven't tried it.

Also, I did an upgrade from 6.10 to 7.04, and my performance took a big hit.  I went back to 6.10 since I knew it would work.  I've got a fresh 7.04 iso, but I haven't tried it yet.

by the by, I use a 900 duron with 128 mb of ram, and xubuntu is WAY faster (responsive) than XP.

---

### Post by Exershio on 2007-05-31
> **dolphin_oracle said:**
> opera is supposedly faster on xubuntu, but i haven't tried it.

Also, I did an upgrade from 6.10 to 7.04, and my performance took a big hit.  I went back to 6.10 since I knew it would work.  I've got a fresh 7.04 iso, but I haven't tried it yet.

by the by, I use a 900 duron with 128 mb of ram, and xubuntu is WAY faster (responsive) than XP.
Thank you for your input. The ISO for 7.04 is 55% downloaded, so another 2 hours and I'll have everything installed and setup. I'll let you all know how well it works out!

Also, one more question (for now anyways, heh): Does Opera have an adblock extension like firefox?

---

### Post by ap9er on 2007-06-02
> **Exershio said:**
> Well I can't find any decent media players besides Amarok. Are there any other good ones?


You could check Exaile
[http://www.exaile.org/](http://www.exaile.org/)

---

### Post by lavs23 on 2007-06-03
Xubuntu should be much quicker then Win XP, especially on a machine with 256MB of RAM.  However I haven't had very good results with Xubuntu (honestly haven't tried since 6.06 though).  I personally prefer SAM Linux, which is based on PCLinuxOS, for XFCE desktop distros.  I think Amarok might be your problem unfortunately.  On my Ubuntu 7.04 system it is currently using 94.8 MB of RAM.  I would second the recommendation for Exaile! I can't get it to work right in Ubuntu but it comes as default in SAM and seems to work good.  Banshee might be another option but it's lacking some features that I'd like, mainly Streamcast streams in radio by default.

---

### Post by rsambuca on 2007-06-03
I agree with one of the earlier posters.  With your system specs, you should try very hard to avoid using amarok due to the fact that the qt libraries have to be loaded.  Stick with the xubuntu default music player and you should notice quite a difference in performance.

---

### Post by Sweet Mercury on 2007-06-03
> **sessine said:**
> I see that you are using Firefox (a Gnome/gtk app) and Amarok ( a KDE/qt app), this means that you need to load both the gtk AND qt libraries into memory if you run them both at the same time.  You may find that sticking to just gtk apps may make things go a bit quicker as I think XFCE also use gtk.

How can one tell if an app is gtk or qt?

edit: Second small question, I've noticed that while browsing the repositories with Synaptic, most of the games are for KDE. I can still run them under GNOME, if I want to install them.

---

### Post by misfitpierce on 2007-06-03
Did you update all of your items such as graphics card drivers etc. I ran Xubuntu and it was quite fast but I missed gnome so I came back to Ubuntu

---

### Post by cordle on 2007-06-05
I'm an absolute beginner, so I have no advice or wisdom to give...just to say, I run xubuntu 7.04 fine on my old 448MHz Pentium III with 128MB RAM.

---

### Post by eeried on 2007-06-27
> I'm also running a resolution of 1152x768 

That can be a load on your graphic card. If your screen isn't recent you ought to go down (1024x768 If you have some info about your screen have a look at it and set the right resolution and refresh rate in Xfcs settings. Or better reconfigure Xorg: from a terminal (Ctrl+Alt+F1) that gets you out of X, login then type:
```
sudo dpkg-reconfigure xserver-xorg
```
everything's easy. most of the time you simply say okay to all question. The screen should be detecetd automatically. then choose Advanced when you get the choice and check the refresh rate (should be okay) and say okay to the question: should these setings be written in the file? (or sth like that).

I would stick with Dapper even if Xfce has improved a lot since that version. Dapper seems to work better with old hardware than Feisty.

Edgy was excellent with Xcfe and Gxine, I found but rotten for the resolution. I was unable to set 1024x768 on my screen whatever I did and 1280x1024 which my old  14/15" screen can go up to was quite uncomfortable and a dreadful load on the 8Mo Matrox graphic card. So I switched back to dapper and now I use Feisty on three old computers. PII, 400 MHZ, 256MB RAM, PII, 233MHZ 300MB RAM, PIII 400MHZ, 380MB RAM approx.

On the PIII, I installed k3b and k9copy and both run fine. K3b takes a while to launch, though. A CD that I wanted to rip nearly froze the computer though it was ripped fine on a much more powerful one but I've been also able to rip a DVD with k9copy.

A friend of mine with am AMD k6-2, 4000MHZ, 256MB RAM is having some trouble with  an old DVD reader/CD burner on Xubuntu Feisty (she doesn't use the DVD part of the drive since her PCI S3 graphic card is rotten and she's got no AGP port). On Xubuntu Dapper she was able to burn CDs in about 20mns which I can too with her burner on my PIII,  with my new Samsung DVD/CD burner doesn't go any faster on that old machine. Now on my friend's Feisty, the burner declares it needs about 3 hours to burn a CD, and I had to set DMA on whereas Dapper set it automatically.

Another friend of mine is going to test the burner on an old machine running on Debian Etch 4, and we'll see if it works better on Dapper.

I've never used WindowsXP. My old PII originally ran  Windows98 and I added Libranet (Debian-based) on dual-boot before switching entirely to Linux. The main problem is Firefox, it seems to me. Take care not to open too many tabs (of course never open windows, there's a setting in about:config), even on modern computers with 512MB RAM, I've seen Firefox freeze. However feel free to keep Firefox, I only use it. it would be a pity to install proprietary software you don't need really.

Hope you haven't added acrobat reader which is silly on Linux since we have Xpdf or Evince which is installed on X/ubuntu.

on the PIII which has a big enough HDD (20GB compared to the 8GB on which I have Debian Etch and Xubuntu, and the other PII with only 2GB) I install lavishly. Perhaps you ought to refrain from installing the entire OOo. I make do with OOo writer which is onboard so to speak.

I'm used to old computers, and adding RAM up to 256MB or thereabout to all three machines has made some difference, though not dramatic, especially while surfing with Firefox.

I've always been able to use Firefox, GIMP, OOo, Thunderbird, Psi, Thunar, GQView at the same time (so to speak) on my good PII with hardly 200MB RAM while the equivalent wasn't really possible with Windows (whose memory gets choked on open apps even though they aren't all active at the same time).

Apps may get some time to launch but after that they run fine, I think.

Still, I'd like to have a faster version of Ubuntu, and I'll try fluxbuntu when it's stable or before if I get the time to download it and install it.

I find Xgine in Dapper and in Feisty isn't good. it was very good in Edgy. So I uninstalled it and a few other apps, like xfbuner, and on the two PII I uninstalled all things connected with printing (except when GIMP or Abiword would get uninstalled as well, of course). This makes a difference I find.

Conclusion (sorry for this long post): 
- The amount of RAM isn't everything. The quality of the sticks counts. I had to give back a 256MB stick that made my machine slower than the 128MB stick.  I have to do with noname RAM sticks which isn't the top notch of course. 
- The quality of the processor is quite important. My PII (HP vectra vli8) works better than the PIII with less RAM. I had to add more RAM to the PIII to see a difference.
- try Dapper, and stick to it if you're happy with it. Or try Feisty: if it all doesn't work as in Dapper go back to Dapper.

And keep an eye on Fluxbuntu, or try Debian Etch-XFCE if you feel at ease with Linux (it takes a litlle more configuring but it's lighter than Xubuntu).

Many thanks for mentioning SAM Linux, lavs23, I'm sure to try it sometime!

Cheers,

---

### Post by scruff on 2007-06-27
One quick tip - it is always better to mount /home on its own partition. This way, your personal data and desktop settings are not lost during a reinstall. Its quite amazing. Keep /home on its own partition, re-install, boot, and everything looks and acts the same while all your docs and stuff are still around :)

---

### Post by ljpp on 2007-07-11
WindowsXP was released **back in 2001** and therefore designed for the modern 2001 hardware in terms of resource requirements. 

As such WindowsXP is very fast on modern computers of 2007, and should run on any decent hardware built in between 1999-2007+. 128mb is the minimum amount of memory, but 256mb should make it very comfortable. You can tweak barebore XP installation to consume about 64mb:s of RAM after boot.

Modern  desktop Linux distributions, like recent Ubuntu family generations, require rather modern hardware and as such they are not faster (in basic desktop usage) than WindowsXP.

Of course you can ruin your WinXP performance by installing low quality software that consume your memory and CPU resources. Many people are doing that, and then complaining about the poor performance - modern Linux distro has almost everything ready to go after installing.

You should compare modern Linux distributions to Vista rather than XP. 
[I]
Disclaimer: I am well aware that as a server Linux typically outperforms Windows by far, but I made the presumption that we are discussing basic desktop usage[/I]

---

### Post by Bartender on 2007-07-11
If you can get some more RAM that would be good.  512 or better.  Of course, that would make Windows go faster, too, but who cares.  Also, get familiar with ```
top
``` 
It lists the processes that are consuming CPU cycles in the order of usage.  I've got an old PIII 450 MHz Linux test PC.  (sig)  Loaded PCLOS2007.  Brought up Amarok and tossed in a Jethro Tull CD.  Then I ran top.  CPU usage was hanging at around 80%.
Swapped HDD's.  Started up Xubuntu 7.04 and the default CD application and spun the JT CD.  According to top CPU usage was around 17%. 
With an older PC, just the act of starting the System Monitor increases CPU usage so top is better.

---

### Post by kerry_s on 2007-07-11
You want speed, ditch the desktop and use a wm. better yet custom build it to your needs.

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by orb9220 on 2007-07-11
Your problem is using non-light  apps on:

My system specs:
2ghz intel p4 processor
[B]256mb ram
onboard graphics card
[/B]

with the bold text the reason you are having slowness. If you would add an old nvidia card like FX5200 then you would fly again.

Your onboard video is eating 64,128mb of your ram.
Have you installed the video drivers for the chipset on your mobo?

---

### Post by sugarland2k on 2007-07-11
I would consider a memory upgrade.  This is usually the most cost effective upgrade to most PCs.  I will not run a machine with less than 1GB or memory with MS Windoze or Ubuntu/Kubuntu.  My #1 machine has 2GB of fast memory and it runs great!  I usually run in Kubuntu but I think I will load up Xubuntu and give it a try.

---

