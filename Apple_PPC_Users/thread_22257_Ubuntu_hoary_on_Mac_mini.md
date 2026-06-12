---
title: "Ubuntu hoary on Mac mini"
date: 2005-03-26
forum: Apple PPC Users
---

### Post by agravain on 2005-03-26
I put together a webpage with my kernel .config and xorg.conf for Mac mini plus a kernel with working sound.
 
 Note that sound doesn't work with the official (stable and unstable) kernels as of yet. A kernel for mac mini with working sound (and the patch) can be downloaded from my webpage (as a debian package, easy to install).
 
 With this kernel I have everything working perfectly (or so I think) except wireless and bluetooth. I don't know how to test the bluetooth support, maybe it works for all I know.
 
 The webpage: [http://www.pvv.org/~perchrh/macmini/](http://www.pvv.org/~perchrh/macmini/)

---

### Post by skassam on 2005-03-28
What is the performance like on your mac mini? I have a powerbook G4 1.5GHz and OSX runs great. I imagine ubuntu must fly.

---

### Post by Achille on 2005-03-28
Thank you very much for your kernel for the mac mini.

The sound is here, but most applications (like totem or rhythmbox) still don't work, because they complain that /dev/dsp is missing. What should I do?

How did you proceed to compile your own kernel? I tried to do exactly the same some days ago, but I didn't success. Thank you for your explanations.

---

### Post by agravain on 2005-03-28
[QUOTE=skassam]What is the performance like on your mac mini? I have a powerbook G4 1.5GHz and OSX runs great. I imagine ubuntu must fly.[/QUOTE]
I haven't done any serious tests, but the responsiveness and number-crunching ability of the mini seems to be significantly better than my old system, an Amd Duron 1.6Ghz with 512MB sdram133. 
It does fly, except when reading or writing much to the harddrive (4200 RPM), but I was surprised how fast the drive was, I had expected it to be slower.

I don't really have any basis for comparing OSX and Linux performance on the mini as of yet. I could maybe run some tests if I got some pointers to what tests are meaningful and good for benchmarking mini OSX and mini Linux.

---

### Post by agravain on 2005-03-28
[QUOTE=Achille]Thank you very much for your kernel for the mac mini.

The sound is here, but most applications (like totem or rhythmbox) still don't work, because they complain that /dev/dsp is missing. What should I do? [/QUOTE]
You should configure your applications to use Alsa for sound instead of OSS.

[QUOTE=Achille]
How did you proceed to compile your own kernel? I tried to do exactly the same some days ago, but I didn't success. Thank you for your explanations.[/QUOTE]
I installed the make-kpkg package, and ran make-kpkg --initrd --revision <my revision-number> buildpackage in the directory where my kernel source and configuration was.

I uploade a 2.6.11-6 kernel with support for Alsa OSS-emulation, so that OSS-using applications works.

---

### Post by skassam on 2005-03-28
I am actually more interested in the feel rather than hard benchmarks. You answered that question. Thanks!

---

### Post by mips on 2005-03-29
Why dont you Mini users upgrade to 7200RPM drives ?! You will get much better performance. If I was going to buy a Mini I would get the cheapest system and upgrade it with non-apple parts.

Check these links:

[http://www.hitachigst.com/portal/site/en/?epi_menuItemID=ec03cadee7c6fb5deb4703e3aac4f0a0&epi_menuID=edf693c2139b099056fb11f0aac4f0a0&epi_baseMenuID=3d0cb215112b6934ab937c27aac4f0a0](http://www.hitachigst.com/portal/site/en/?epi_menuItemID=ec03cadee7c6fb5deb4703e3aac4f0a0&epi_menuID=edf693c2139b099056fb11f0aac4f0a0&epi_baseMenuID=3d0cb215112b6934ab937c27aac4f0a0)
[http://www.hitachigst.com/portal/site/en/?epi_menuItemID=c8c3966a526cfb5deb4703e3aac4f0a0&epi_menuID=edf693c2139b099056fb11f0aac4f0a0&epi_baseMenuID=3d0cb215112b6934ab937c27aac4f0a0](http://www.hitachigst.com/portal/site/en/?epi_menuItemID=c8c3966a526cfb5deb4703e3aac4f0a0&epi_menuID=edf693c2139b099056fb11f0aac4f0a0&epi_baseMenuID=3d0cb215112b6934ab937c27aac4f0a0)

[www.alienware.com/product_detail_pages/](www.alienware.com/product_detail_pages/) mj-12m_5500/PDFs/Why7200MobileHDDs.pdf

---

### Post by agravain on 2005-03-29
[QUOTE=mips]Why dont you Mini users upgrade to 7200RPM drives ?! You will get much better performance. [/QUOTE]
In my case I don't want a noisier harddrive. The one that comes with the mini is pretty silent. I have enough ram to avoid a lot of disk reads, once cache builds itself up (and it does, I don't ever shut down the mini), so the (relatively) slow disk isn't that much of a problem to me, definetly not worth an increase in noise.

---

### Post by mips on 2005-03-29
> In my case I don't want a noisier harddrive. The one that comes with the mini is pretty silent. 

ok. Will it really be that much noisier ?

Should here my amd64 PC, you will probably freak. Not that quite but working on it with a new CPU heatsink/fan combo & accoustic insulation for the case.

cheers
mips

---

### Post by agravain on 2005-03-29
[QUOTE=mips]ok. Will it really be that much noisier ?[/QUOTE]
No, probably not. But my newfound silence is very soothing, I don't want to loose it. I would sacrifice much in terms of performance to get a silent machine, I think.

---

### Post by HexCore on 2005-03-29
[QUOTE=agravain]I put together a webpage with my kernel .config and xorg.conf for Mac mini plus a kernel with working sound.
 
 Note that sound doesn't work with the official (stable and unstable) kernels as of yet. A kernel for mac mini with working sound (and the patch) can be downloaded from my webpage (as a debian package, easy to install).
 
 With this kernel I have everything working perfectly (or so I think) except wireless and bluetooth. I don't know how to test the bluetooth support, maybe it works for all I know.
 
 The webpage: [http://www.pvv.org/~perchrh/macmini/](http://www.pvv.org/~perchrh/macmini/)[/QUOTE]
Hi !
Thx for the stuff you put on your page.

I tried to usee it with my mac mini to get the sound work, but, due to my low linux skill, I couldn't get anything.

I downloaded the image kernel-image-2.6.11.6_1.0_powerpc.deb you provide on your page, and did :
```
sudo dpkg -i kernel-image-2.6.11.6_1.0_powerpc.deb
``` 
and then a 
```
sudo ybin
``` 
I certainly is something stupid I did or didn't do, but as I am a newbie, I can't get it right.
Can you correct me ?
Thx.
BTW, when I do a uname -sr on my mac mini after a reboot, I get this :
```
Linux 2.6.11.6
``` 
but sound still doesn't work.

---

### Post by agravain on 2005-03-29
[QUOTE=HexCore]
I tried to usee it with my mac mini to get the sound work ...
BTW, when I do a uname -sr on my mac mini after a reboot, I get this :
```
Linux 2.6.11.6
``` 
but sound still doesn't work.[/QUOTE]

Stupid me. I forgot to patch the 2.6.11.6. kernel. You did right. I'll put up a new one in 30 minutes, with working sound. You can use the old one at [http://www.pvv.org/~perchrh/macmini/kernel-image-2.6.11.5_6.0_powerpc.deb](http://www.pvv.org/~perchrh/macmini/kernel-image-2.6.11.5_6.0_powerpc.deb) if you're very eager.

Update: It's out. Check the webpage.

---

### Post by HexCore on 2005-03-29
[QUOTE=agravain]Stupid me. I forgot to patch the 2.6.11.6. kernel. You did right. I'll put up a new one in 30 minutes, with working sound. You can use the old one at [http://www.pvv.org/~perchrh/macmini/kernel-image-2.6.11.5_6.0_powerpc.deb](http://www.pvv.org/~perchrh/macmini/kernel-image-2.6.11.5_6.0_powerpc.deb) if you're very eager.

Update: It's out. Check the webpage.[/QUOTE]
Ok, great thx ;)

The rest of the commands I made are correct ?

---

### Post by agravain on 2005-03-29
[QUOTE=HexCore]Ok, great thx ;)

The rest of the commands I made are correct ?[/QUOTE]
Yes. Let me know how it works out.

---

### Post by HexCore on 2005-03-29
[QUOTE=agravain]Yes. Let me know how it works out.[/QUOTE]
great, I got the sound !!!

In XMMS, when I choose libALSA.so as output plug in, sound doesn't work, with ilbOSS.so, it works perfectly, and with libesdout.so too.

Thx again :)

---

### Post by agravain on 2005-03-30
[QUOTE=HexCore]great, I got the sound !!!
In XMMS, when I choose libALSA.so as output plug in, sound doesn't work, with ilbOSS.so, it works perfectly, and with libesdout.so too.
[/QUOTE]
Works on my system. Remember that alsa mutes the volume by default. Start sudo alsamixer to unmute the sound.
[QUOTE=HexCore]Thx again :)[/QUOTE]
NP

---

### Post by salimma on 2005-03-31
Hello,

I am thinking of getting a Mac mini for use as my file server.. has anyone here tried using Firewire and/or USB2 external drives with it and could confirm what work/don't work?

Many thanks,

- Michel

---

### Post by Emerpus on 2005-04-02
Hello ladies (if any) and gents!

The concept of a Mac Mini running Ubuntu seems really cool to me. Why? Looks, size and very low power consumption in combination with great open source software that will do all I really need. \\:D/ 
However, I'm totally new to both Mac and Linux. :? Taking this into consideration my simple questions is:

How hard is it? :-k 

Since some of the Mac software might also be useful I would prefer a dual boot system. I found this guide to installing dual boot (Debian) Linux on the Mac Mini:
[http://www.sowerbutts.com/linux-mac-mini/](http://www.sowerbutts.com/linux-mac-mini/)
How much does installing Ubunto (dual boot) differ from this guide? (and should I consider orange juice instead of lemon?) :-s

Btw. although I'm a total linux n00b I'm more confident with the hardware side of things so I'm probably going for the cheapest model. Then open the box, throw in a gig of ram and overclock it to the speed of the bigger brother as described here:
[http://www.lbodnar.dsl.pipex.com/macmini/](http://www.lbodnar.dsl.pipex.com/macmini/) 
I might also go for a 7200 rpm HDD if it doesn't strain my budget too much.

Now, such a little Ubunto box would max out on my geek factor scale. But would you assist on walking me through the software install?

---

### Post by agravain on 2005-04-02
> The concept of a Mac Mini running Ubuntu seems really cool to me...How hard is it? :-k 

Not especially hard. The hardest part for a newbie lies in partitioning your drive, I think, the rest is real easy. You should know that there is no driver for the wireless adapter in the mini.
> 
Since some of the Mac software might also be useful I would prefer a dual boot system. I found this guide to installing dual boot (Debian) Linux on the Mac Mini:
[http://www.sowerbutts.com/linux-mac-mini/](http://www.sowerbutts.com/linux-mac-mini/)
How much does installing Ubunto (dual boot) differ from this guide? (and should I consider orange juice instead of lemon?) :-s

It doesn't differ at all, assuming that the ubuntu and debian installers use the same partitioning tool.
The easiest way to set up dualboot, IMHO, is to reinstall OSX, and when in the OSX installer, partition the drive like at that url (merge the fat and hfs+ partition to one large  hfs+ partition, though, there is no need for FAT for interoperability). Then install ubuntu ppc from a bootable cd.
> 
Btw. although I'm a total linux n00b I'm more confident with the hardware side of things so I'm probably going for the cheapest model. Then open the box, throw in a gig of ram and overclock it to the speed of the bigger brother as described here:
[http://www.lbodnar.dsl.pipex.com/macmini/](http://www.lbodnar.dsl.pipex.com/macmini/) 
I might also go for a 7200 rpm HDD if it doesn't strain my budget too much.

Sounds good, but you might want to consider if the drive makes the case too hot, resulting in an unstable system (depends on the actual drive, obviously).

---

### Post by Emerpus on 2005-04-02
Thanks agravain. :grin:  I'll start saving my pennies for a Mac Mini and try it.

One more question though: I read in another thread in here that it may be a problem to get Skype to work on a Mac with Ubuntu/Linux ppc. Does Skype work for you?

---

### Post by agravain on 2005-04-03
[QUOTE=Emerpus]I read in another thread in here that it may be a problem to get Skype to work on a Mac with Ubuntu/Linux ppc. Does Skype work for you?[/QUOTE]
Yes, Skype doesn't release binaries for Linux ppc. They could if they wanted to, wouldn't be too hard, as they support OSX and use QT for gui, so maybe they'll release a Linux ppc version if they got enough requests.

You can use gnomemeeting instead of Skype on Linux.

---

### Post by Emerpus on 2005-04-03
[QUOTE=agravain]Yes, Skype doesn't release binaries for Linux ppc. They could if they wanted to, wouldn't be too hard, as they support OSX and use QT for gui, so maybe they'll release a Linux ppc version if they got enough requests.

You can use gnomemeeting instead of Skype on Linux.[/QUOTE]

Hmm, ok. I'll write them an email. ;) 
I don't care a lot about missing driver support for the Wifi/Bluetooth unit since I'm not going to buy that anyway but Skype is a small app I'm using quite a lot (also for Skypeout). Of course I could use it on OSX in a dual boot system but I would definitely prefer to have it working with Ubuntu also since I should think I would be working in Ubuntu most of the time.

I don't suppose gnomemeeting is compatible with Skype (so I can call my friends/family who uses Skype)?

Any other apps with poor support for Linux ppc compared to Linux x86?

---

### Post by djfake on 2005-04-17
[QUOTE=agravain] [http://www.pvv.org/~perchrh/macmini/kernel-image-2.6.11.5_6.0_powerpc.deb](http://www.pvv.org/~perchrh/macmini/kernel-image-2.6.11.5_6.0_powerpc.deb) if you're very eager.

Update: It's out. Check the webpage.[/QUOTE]


sorry for the n00b question, but howto apply the patch? also, do I need the .config and where does that go?

thanx
c

---

### Post by agravain on 2005-04-17
[QUOTE=djfake]sorry for the n00b question, but howto apply the patch? also, do I need the .config and where does that go?[/QUOTE]
Check out [http://www.digitalhermit.com/linux/Kernel-Build-HOWTO.html](http://www.digitalhermit.com/linux/Kernel-Build-HOWTO.html) for answers to your questions.

Sounds like you're better off installing the kernel-image, though, read the section named "kernel-image for ubuntu/debian" at my page.

---

### Post by dietrying on 2005-04-23
Hi there,

i've got problems with my ubuntu konfogurations after installing the sound-patched kernel (wich works great!). So I'm not able to use my dsl internet coonection: modprobe pppoe says there is no pppoe. When i try pppoeconf, it finds the ethernet but is not able to find the dsl-modem. When I installed ubuntu hoary, this was no problem, i don't know why this happens........

any idea what i am doing wrong?

the second Problem is, that i'm not able to get the 3 button emultion work, wich would be very nice......normal ubuntu installation has it configured automaticaly in....perhaps ubuntu disables this feature when starting and installing it with 2 button mouse? I really ask myself how to get this to work, because i'm not good in kernel patching/ compilation :roll: i tried it 2 times and didn't got it right  ](*,)  

every help or answer would be nice......

greetings - David

---

### Post by ubuntu_demon on 2005-04-23
[quote=Emerpus]
I might also go for a 7200 rpm HDD if it doesn't strain my budget too much.
[/quote]
 I'm going to buy a mac-mini for my dad. As far as I know there aren't drives available  bigger than 80 gb and therefor the buying it with an 80 gb from an apple store seems to be the best choice. Or do you guys suggest a different harddrive ?

---

### Post by agravain on 2005-04-23
[QUOTE=demon666_nl]I'm going to buy a mac-mini for my dad. As far as I know there aren't drives available  bigger than 80 gb and therefor the buying it with an 80 gb from an apple store seems to be the best choice. Or do you guys suggest a different harddrive ?[/QUOTE]
I haven't seen any >80GB 2.5inch IDE drives for sale either. 
That leaves only the speed/noise tradeoff. Do you want a silent, slighty slow drive, or do you want a fast, slighty noisier drive? That's the question you should ask yourself. 
The 80GB drive from apple isn't that slow. I've only noticed that it's slower than the one in my PC (7200RPM) when I'm deleting large amount of data.

---

### Post by dietrying on 2005-04-27
anyone who got playing encrypted dvd's working on the mac mini. My problem is, that i've libdvdcss2 installed (from marillat), and kaffeine finds it......but I#m not able to play encrypted dvds. totem xine says, that the dvd maybe is encrypted, and libdvdcss is not installed. I also tried 2 other versions of libdvdcss....no effect. Does anyone have an idea?

---

### Post by agravain on 2005-05-08
[QUOTE=dietrying]anyone who got playing encrypted dvd's working on the mac mini. My problem is, that i've libdvdcss2 installed (from marillat), and kaffeine finds it......but I#m not able to play encrypted dvds. [/QUOTE]
Yes, I have encrypted dvds working. I just installed the libdvdcss and then everything was ok. 
In Mac OS X you are asked what dvd-region you are in when you first start dvd-player (hardware setting). If you haven't done this, then that might be the reason. 
I use xine and mplayer to play dvds on Linux without any problems.

---

### Post by ivanh on 2005-05-12
[QUOTE=agravain]Yes, I have encrypted dvds working. I just installed the libdvdcss and then everything was ok. 
In Mac OS X you are asked what dvd-region you are in when you first start dvd-player (hardware setting). If you haven't done this, then that might be the reason. 
I use xine and mplayer to play dvds on Linux without any problems.[/QUOTE]
 has anybody gotten the modem working on ubuntu, 'cause i'd like to run it as a dialin server :-p?

---

