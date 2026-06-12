---
title: "Brand New to Ubuntu"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by dtrot55 on 2007-09-28
Well i am brand new to this os and i have chosen to download Unbuntu-7.04-amd64 version.  I know about the whole software and driver issue with 64, but currently i am using WinXP 64 with really no issues.  I have avoided Linux stuff over the years cause I knew finding drivers would be brutal.  But now i am going to start doing some stuff and would want a more stable and reliable OS.  So right now i am asking if anyone could help me find drivers for my stuff....so far i have found Video Card (Gforce 6600 gs) and sound card (Sound Blaster X-Fi Platinum)....still looking for my mobo which is the TForce 6100-939.

The chipset is North bridge: Nvidia Geforce 6100 South Bridge: Nvidia nForce 410.
and i cant remember if those would come with the ethernet drivers so heres the ethernet model:
PHY:RTLL8201BL/RTL8201 CL

Any help would me much appriciated. If i can get everything to work..i would prob migrate over to Ubuntu and dump Windows for good.

THANKS!

dan

---

### Post by finer recliner on 2007-09-28
burn the install disc and boot from it (it acts as a live disc). play around with it and see what works and what doesn't and go from there.

test things like internet, video playback, sound playback...etc

---

### Post by nickpaton on 2007-09-28
I have an AMD64 PC and have chosen to use the 32bit version of Feisty (and every distro before that!).

There are many posts around about 64 versus 32 bit, such as [this one]("http://ubuntuforums.org/showthread.php?t=560935"), but for me 32 bit is slightly easier with more working programs "out of the box", and no real discernible decrease in speed.

As FR says, it really is that easy now - I've installed Ubuntu on loads of PC's, laptops with and without wireless etc etc and most of the time it all just works
I would say that as someone starting out you will probably end up reinstalling loads of times, but this will help familiarize you with how it all works.

Also have a look at the [Psychocats site]("http://www.psychocats.net/ubuntu/index.php"), which is excellent and will help you with installation and loading programs etc etc.

And don't be afraid to ask, but also use the forum search facility,since many of your queries could already have been answered. 

Good luck and welcome to Ubuntu and the forums!

---

### Post by overdrank on 2007-09-28
> **nickpaton said:**
> I have an AMD64 PC and have chosen to use the 32bit version of Feisty (and every distro before that!).

There are many posts around about 64 versus 32 bit, such as [this one]("http://ubuntuforums.org/showthread.php?t=560935"), but IMHO I've chosen to go with 32 bit.

Good luck!

Great point, let the users decide if he/she wants 64 0r 32 bit. If you have any more questions on the 64 bit this is a good place to ask, 
[http://ubuntuforums.org/forumdisplay.php?f=134](http://ubuntuforums.org/forumdisplay.php?f=134)
Good luck!

---

### Post by pdlethbridge on 2007-09-28
The very first thing you should do is when installing the OS, create a home partition to put all your files and settings, so when you have to reinstall, all your settings are in the home directory on that extra partition. Try to stay away from downloading too much stuff. Keep your OS as simple as it is new. As you get acquainted with the OS, test things out, and test new things.

---

### Post by nickpaton on 2007-09-28
@ Overdrank - sorry M8 - I altered my post after you did yours!

However I totally agree with what you say too.

---

### Post by Perfect Storm on 2007-09-28
There might be a problem with the soundcard X-Fi , as far as I know  (correct me if I'm wrong) the linux drivers is still in beta and havn't been added yet.
I'm getting a Sound Blaster® X-Fi Xtreme Music PCI-Soundkarte to play around the beta driver soon.

---

### Post by Perfect Storm on 2007-09-28
Here's the beta driver to the sound card: [http://opensource.creative.com/soundcard.html](http://opensource.creative.com/soundcard.html)
Save it to your Desktop;
```
cd ~/Desktop
tar zxfv XFiDrv_Linux_US-1.04.tar.gz
cd XFiDrv_Linux_US-1.04
chmod +x installer
sudo sh installer
```

if **sudo sh installer** doesn't work try **sudo ./installer**

NOTE 1: You need kernel headers to do this;
```
sudo aptitude install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
```

NOTE2: It's still in beta stage and close source.

---

### Post by rsambuca on 2007-09-28
> **nickpaton said:**
> I have an AMD64 PC and have chosen to use the 32bit version of Feisty (and every distro before that!).

There are many posts around about 64 versus 32 bit, such as [this one]("http://ubuntuforums.org/showthread.php?t=560935"), but for me 32 bit is slightly easier with more working programs "out of the box", and no real discernible decrease in speed.


If you have chosen to use the 32bit versions for "every distro", then how can you possibly be qualified to say that "for me 32bit is slightly easier..."

---

### Post by CaptainInsaneO on 2007-09-28
Because to choose something, you must have an option. To have an option, you must have two or more things to choose from. I'm guessing he's probably tried the 64bit in the past and decided the 32bit was better for what he needed and has never looked back.

---

### Post by overdrank on 2007-09-28
rsambuca & CaptainInsaneO you both have valid points but lets not get off the topic and just give the op the information and let him/her choose what is best for them. :)

---

### Post by rsambuca on 2007-09-28
> **CaptainInsaneO said:**
> Because to choose something, you must have an option. To have an option, you must have two or more things to choose from. I'm guessing he's probably tried the 64bit in the past and decided the 32bit was better for what he needed and has never looked back.

But he is giving advice based on outdated, incorrect information, which should be addressed.

---

### Post by Perfect Storm on 2007-09-28
Lets keep on topic folks :KS
(The 64-bit version is now matured enough to be used, I'm going to use 64-bit version when I get my new PC 64bit).

---

### Post by dtrot55 on 2007-09-28
Thanks guys for the help....i did burn the cd and play a little with the OS. Tried installing but failed miserably.  I don't want to give up yet though.... I cleared off my 2nd partiton to make it a clean partition for Ubuntu.  So when i get back from work ill try again.  But i did find out that i need codecs for mp3's and i need to try out that beta sound card driver.  I guess my biggest question is going to be, once I get this working somewhat..how can i integrate bootcamp to use stuff like photoshop and play games in linux? Or would any of you reccomend somthing else?  Cause what I would like to do is make my computer a linux main with a second OS of XP so that if i need somthing still in XP i can just boot to it.  

can anyone recomend any books or anything to help this <--- noob (hehe) learn some linux without having to keep bothering you very helpful people. 

Thanks!!

Dan

---

### Post by overdrank on 2007-09-28
> **dtrot55 said:**
> Thanks guys for the help....i did burn the cd and play a little with the OS. Tried installing but failed miserably.  I don't want to give up yet though.... I cleared off my 2nd partiton to make it a clean partition for Ubuntu.  So when i get back from work ill try again.  But i did find out that i need codecs for mp3's and i need to try out that beta sound card driver.  I guess my biggest question is going to be, once I get this working somewhat..how can i integrate bootcamp to use stuff like photoshop and play games in linux? Or would any of you reccomend somthing else?  Cause what I would like to do is make my computer a linux main with a second OS of XP so that if i need somthing still in XP i can just boot to it.  

can anyone recomend any books or anything to help this <--- noob (hehe) learn some linux without having to keep bothering you very helpful people. 

Thanks!!

Dan

Hi and welcome, well there is some good reading here
[http://ubuntuforums.org/showthread.php?t=232059](http://ubuntuforums.org/showthread.php?t=232059)
And you can find some info and the codecs and restricted formats here
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
I cant help with boot camp but I am sure you will find info in the forums.
And lastly for books I used Ubuntu Hacks,The official Ubuntu Book. Good luck!
:guitar:

---

### Post by Perfect Storm on 2007-09-28
Note that the sound driver only works for 64-bit systems (don't blam linux, blame creative ;) )
There might be a 32-bit driver later.

---

### Post by dtrot55 on 2007-09-28
yeah i know what you mean by the whole 32 vs 64...but really ive only had one issue with that and it was a piece of software i can deal without.  But most of what ive seen is most 32 bit software works with winxp64...now i dont know the difference with Linux so i dont know if linux is more picky about that or not.  But from what ive been reading 64 bit ubuntu is the way to go

---

### Post by CaptainInsaneO on 2007-09-28
64bit is backwards compatible with 32bit.

Meaning most - if not all - 32 bit software should work on 64bit.

---

### Post by dtrot55 on 2007-09-28
> **CaptainInsaneO said:**
> 64bit is backwards compatible with 32bit.

Meaning most - if not all - 32 bit software should work on 64bit.

I concur.  Like i said ive only really ran into one piece of software that didnt want to work in its 32 bit form.

---

### Post by dtrot55 on 2007-09-28
Well ive been reading alot and think im understanding a little better...but could someone kinda fine tune for me how i would use like photoshop or most programs that would work under windows...cause i am a graphic designer and i have tried gimpshop and its nowhere near photoshop.  I have been told that i would have to use bootcamp or somthing like that... Also i am a avid video game player.  So any ideas on getting games to work in Ubuntu to would help greatly.

Thanks!

dan

---

### Post by nickpaton on 2007-09-28
> **rsambuca said:**
> But he is giving advice based on outdated, incorrect information, which should be addressed.

Not wanting to go off topic again, so last time!
@Rsambuca - apologies to you and everyone else, but I did once try 64bit and gave up.

However as AI has now pointed out, 64bit is now sufficiently mature and on that basis I will try it again V soon.

Your advise and comments are much appreciated - that's what I like about this place - I guess we can leave it at that and continue to assist Dtrot55

---

### Post by Perfect Storm on 2007-09-29
> **dtrot55 said:**
> Well ive been reading alot and think im understanding a little better...but could someone kinda fine tune for me how i would use like photoshop or most programs that would work under windows...cause i am a graphic designer and i have tried gimpshop and its nowhere near photoshop.  I have been told that i would have to use bootcamp or somthing like that... Also i am a avid video game player.  So any ideas on getting games to work in Ubuntu to would help greatly.

Thanks!

dan

As far as I know only photoshop 7 is currently working with [Crossover](http://www.codeweavers.com/products/cxoffice/) or you can try wine if you don't want to pay (requires tweaking and such sometimes); [http://gaming.gwos.org/doku.php/wine:winestuff](http://gaming.gwos.org/doku.php/wine:winestuff) - a good guide (alot reading).
Alternative check out if Pixel is sufficient for you; [http://www.kanzelsberger.com/pixel/?page_id=12](http://www.kanzelsberger.com/pixel/?page_id=12) (not free either - $29)

For win games check wine or cedega: [http://transgaming.com/](http://transgaming.com/) (cost a monthly fee - $5)
Note that only the very populare win games will properly works and you have to wait a awhile before new populare games will work on these applications. Another option is trying out and play the "few" native games. If you're into FPS you're in luck. All quakes an UT is native on linux.
But I would advise you to dual boot with windows until you're are settle with the linux world - There's a world to diffrent between the two.

---

### Post by dptxp on 2007-09-29
> **dtrot55 said:**
> I concur.  Like i said ive only really ran into one piece of software that didnt want to work in its 32 bit form.

Soon we will see more and more pieces that shall not be in 32 bit form. 
They will refuse to run in 32 bit OS. All new CPUs by AMD and INTEL
are now 64 bit.

---

