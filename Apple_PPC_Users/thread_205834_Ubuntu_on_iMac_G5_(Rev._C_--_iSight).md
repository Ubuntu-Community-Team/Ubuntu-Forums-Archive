---
title: "Ubuntu on iMac G5 (Rev. C -- iSight)?"
date: 2006-06-29
forum: Apple PPC Users
---

### Post by rwwall on 2006-06-29
Hi everyone!

I tried installing a beta version of Dapper on my iMac G5 (I have the last G5 version, the one w/ built-in iSight) a couple of months ago, and it failed to boot up the installation disk (fans went crazy and I got a message I can't remember). Before I spend time downloading and burning another CD image, does anyone know whether any progress has been made on supporting the iMac G5? Should I go ahead and give it another go?

~ rwwall

---

### Post by iAlexander on 2006-07-01
I've tried it with the non-beta of Dapper and have ad a similar problem. I get to yaboot up and do a hit enter. I wait the the screen goes black so te i reboot and type "live video=ofonly" and the it gets to the loading screen but the colous are all wierd. Everything it tries loads says ok but then the last item says failed really quickly and then the screen goes black and stays black. Any ideas?

---

### Post by mattl on 2006-07-02
I have it running on a Rev B.. been running quite happily for about 4 months.

---

### Post by imran on 2006-07-04
hi guys.. 

I am not new to linux especially when it comes to installing linux and new softwares to make linux box do wat I want 

Now, I have this the least supported imac g5 20 inch model which does not boot any live CD or installation CD .. btw g5  is 64 bit processor.. to mention a few distros that I have tried are ubuntu 5.10/6.06, gentoo 06, yellow dog 4.1, debian 3.1 r2 (apr-06) .. the only little succes was with yellowdog which boots the command prompt complaining about "no root partition found or something like that and i dont care abt this distro anymore coz I want a live session first to play with my imac first before really busting my data etc" .. the other success was with ubuntu dapper upto the point where all services are started with no human colors untill frozen in the end before even starting an X server..

my request to anyone reading this at any time any where with any experience with imac g5 20 inch or a linux expert with some time is "if I cant boot a single rescue/live or installation CD how am I going to get rid of mac os x" .. and the answer I require is :

1- Do I need to modify an installation iso image of ubuntu or yellowdog and put a kernel (which I dont know so if you know a patched kernel that boots would be nice to know) which works with these machines and its entry in yaboot.conf OR

2- there are some HIDDEN parameters to be passed to kernel on boot like nol3 (no lever 3 cache) or disabling sound or video driver is ATI and resolution is supposed to be 1280x1024 etc .. 

As I have not even be able to boot linux on this machine I dont have any idea wat its going to be after booting.. I just cant believe how companies use open technology developed/mentained by people and then change them in to propriety, mess abt with standards just to make money.. and then dont even dare to give just a fraction back to comunity .. look at sony (ps2 linux), apple (freebsd), just to mention two of the bigest disgrace .. and both of them are the first to put any kind of DRM restrictions/technologies on people.. anyway I think I have had enough of my anger out.. i need to cool down (will just get some ice cubes and put them in to my underwear) ...

I hope I get linux on my imac some day.. and even If someone can get me some info on openbsd for this .. I dont mind..

take care (believe me spent days (not hours) now searching for some solution)

---

### Post by rwwall on 2006-07-06
Thank you for your post, imran. I found it very informative.

One of the problems with this situation, as I see it, is that there isn't a lot of impetus for people to create a solution. Rev. A and B iMac G5s, and Intel iMacs, work okay. It's just our little unfortunate revision that has problems :(.

I'm going to be passing this computer on to my mother in a month or so and, while I would love it to be able to dual-boot Mac OS X and Ubuntu, I doubt that I'm going to be able to do that with a reasonable amount of user-friendliness any time soon. Since the computer's not going to be mine, I'm not going to be able to look for a solution, and don't have much of a reason to try :(.

Oh well, on the bright side, I'm replacing the iMac with a MacBook Pro :grin:

---

### Post by nicoduck on 2006-07-09
hi,

i have a quite similar problem
i tried out he dapper cd, but i got always a blackscreen after a while (not with the option video=ofonly, there was first a ubuntu logo with wrong colours, and then the black screen)
my fans started after a while and stopped only when i restarted my mac.
i tried then the breezy cd and got some other errors:
[http://vthadden.de/live.JPG](http://vthadden.de/live.JPG) - Parameter: Live
[http://vthadden.de/live-powerpc.JPG](http://vthadden.de/live-powerpc.JPG) -  Parameter: Live-powerpc
[http://vthadden.de/live-powerpc64.JPG](http://vthadden.de/live-powerpc64.JPG) -  Parameter: Live-powerpc64
the first errors are the same but a differe parameter (maybe is live a similar for live-powerpc)
i tried the option video=ofonly here too, but nothing hase changed, same error.
What dows the release keys to continue mean?
i didn't push any key, i had no time to typo "mac-boot" because the error appeared the same time as the message to type it in.
Can anybody help?
thanks
nico

---

### Post by phersotty on 2006-08-01
> **imran said:**
> hi guys.. 

Now, I have this the least supported imac g5 20 inch model which does not boot any live CD or installation CD .. btw g5  is 64 bit processor.. to mention a few distros that I have tried are ubuntu 5.10/6.06, gentoo 06, yellow dog 4.1, debian 3.1 r2 (apr-06) .. 

This is just a shot in the dark, but have you tried an AMD 64 distro??  I've never had a Mac with a 64 bit but I have installed linux on an old G3 and on a Mac mini ppc just before they switched to Intel. You probably have more linux experience than I do so you might already if that would work or not.  What I am thinking of is some sort of hybrid where you use yaboot to load an AMD 64 distro.  Really though I have no clue if that would work.  It could be like saying pour some water in your car instead of gasoline and see if it runs.  The only other idea I can think of is using an emulator linux inside the Mac os but it might be more of a stunt than a practical solution.   :confused: ](*,) :-k

---

### Post by Torrance on 2006-08-01
I have a rev A 17inch iMac G5, and I can't get Ubuntu 6.06 installed... and that's a near-universal complaint. With 5.10, we simply had to disable the ESD sound server with a few tricky work-arounds, although now not even that works. For us, it is an issue with the ALSA sound server, and this is acknowledged. Even if the sound can be bypassed it means that the fans are on full because thermal management hasn't been enabled in the kernel.

Could the ALSA system also be the problem with the rev C? I haven't heard of many successful rev Bs either...

(However, openSUSE works fine on my system, just minus sound... even the fans are controlled)

---

### Post by avtolle on 2006-08-02
Ok, first of all: as all of you have likely already read, there are issues with the 6.06 install. Best bet, read the various threads in this forum; if you wish to try, please download and install the alternate install ppc iso; it uses the text installer we became accustomed to in earlier versions. Now, as it seems most of you know, there is a problem with the graphics on boot; there are some workarounds from the terminal to edit the Xorg config file; if you can get it installed, upgrades to the latest kernels seem to have helped some of the issues; the fans on G5s continue to be a problem, but it seems that at least some have had good luck after upgrading to the latest kernel, which is not on the iso. Sorry for the rambling nature of this, but wanted to put out some general information while I had some time.

---

### Post by avtolle on 2006-08-04
A short note: have you tried to install the powerpc-64 kernel (for single G5) or the powerpc-64smp kernel (for dual processor G5)? Just a thought.

---

