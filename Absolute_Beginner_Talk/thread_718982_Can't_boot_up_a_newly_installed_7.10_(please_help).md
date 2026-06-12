---
title: "Can't boot up a newly installed 7.10 (please help)"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by woodsonoversoul on 2008-03-08
I've been wrestling with this for a few months now (search my user name) and here's my problem. I'm tring to install 7.10 on my sister's new Compaq Presario with
AMD Athlon 64 X2 Dual-Core Mobile Technology TK-55; 1.8GHz
1024MB DDR2 SDRAM
Nvidia GeForce Go 6100 (UMA) with up to 288MB total available graphics memory and
Up to 1600MHz system bus running at AC/DC Mode 35 watt, Laptop. It hangs when trying to load the hardware drivers. It used to say the buffer was full when trying to load the drivers and it used to fade to white. What more information do you guys need to help me get this running? Thanks

---

### Post by freelinuxhelp on 2008-03-08
Can you not boot from the LiveCD or can you not boot after installtion?

---

### Post by woodsonoversoul on 2008-03-08
both

---

### Post by freelinuxhelp on 2008-03-08
Have you tried safe graphics mode?
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by woodsonoversoul on 2008-03-08
When I select "Safe Graphics Mode" from the boot disk it also freezes while loading the hardware drivers saying," error receiving uevent message: No buffer space available". It then trys to set up the system clock but freezes.

---

### Post by woodsonoversoul on 2008-03-08
Alright, since I've already got the disk in there, I'm going to do a fresh install

---

### Post by woodsonoversoul on 2008-03-08
Actually, never mind. I've attempted to install 7 or 8 systems on this laptop and the thought of blindly doing it again is kind of nausiating. Is there anyone out there with any ideas?

---

### Post by halitech on 2008-03-08
are you always trying the 64bit versions or the 32bit versions?

---

### Post by woodsonoversoul on 2008-03-08
I originally tried with the Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM) version and that worked for a few weeks. When that started going to a white screen, I realized that the laptop was a 64 bit and my past several attempts have been with that version

---

### Post by halitech on 2008-03-08
even with a 64bit machine, 32bit should work fine and normally has more software available for it then 64 bit. So you did have it installed and working at one point? is there any other OS on this machine at this point?

---

### Post by woodsonoversoul on 2008-03-08
Yes I did have it working with the 32 bit and no there is no other OS installed. Should I try for re-installation with the 32 bit version?

---

### Post by halitech on 2008-03-08
do you have any other installation cds? (ie Windows, fedora, mandriva?) I'm wondering if it is actually an Ubuntu issue or if you possibly have some hard ware issues going on

---

### Post by Mr.Macdonald on 2008-03-08
If the CD won't boot then i am guessing that you haven't installed it

If you can't get the CD to boot then check your BIOS and enable CD boot

If you really want to bash up the computer get a Knoppix and reformat everything BUT that will probably mess other stuff up.


Just giving ideas. I suggest the formating if all else fails and you have no files on the comp that you want

---

### Post by woodsonoversoul on 2008-03-08
Not layng around. If I download one, which do you recommend for super simple operation for my 20 year old sister?

---

### Post by woodsonoversoul on 2008-03-08
I liked the way mint looked and gOS. I've tried to install them both but I think I got white screens with them too. Vista ran fine

---

### Post by halitech on 2008-03-08
Do you have or have access to even an old windows install cd? something like 95, 98 or even heaven forbid ME? I would just like to rule out the hardware before we go looking at the software anymore.

---

### Post by Duck2006 on 2008-03-08
> even heaven forbid ME

One of the worst ever.

---

### Post by halitech on 2008-03-08
from my limited use of vista, I'm not sure which is worse, vista or ME  :-k

---

### Post by woodsonoversoul on 2008-03-08
No i sure don't. She (my sister) would love to have windows back on it, but I wasn't really sure how with "Genuine Advantage" and all that.

---

### Post by halitech on 2008-03-08
anything pre windows XP doesn't have Genuine Windows crap to it ;)

---

### Post by woodsonoversoul on 2008-03-08
Well, all the same, I don't have anything like that laying around...

---

### Post by woodsonoversoul on 2008-03-08
I don't really see anything pre XP "available" online

---

### Post by halitech on 2008-03-08
bummer .... 

not sure what to suggest at this point. maybe try just booting the gparted cd and see what that does.

---

### Post by Duck2006 on 2008-03-08
> **halitech said:**
> from my limited use of vista, I'm not sure which is worse, vista or ME  :-k

Never tried vista and never will.

> woodsonoversoul  	
No i sure don't. She (my sister) would love to have windows back on it, but I wasn't really sure how with "Genuine Advantage" and all that

Use the live cd of gparted and format the drive back to fat32 or ntfs.

---

### Post by halitech on 2008-03-08
> **woodsonoversoul said:**
> I don't really see anything pre XP "available" online

they are there if you know where to look ;)

---

### Post by woodsonoversoul on 2008-03-08
what is "gparted"?

---

### Post by halitech on 2008-03-08
> **Duck2006 said:**
> Never tried vista and never will.
.

we have it at work to support customers, personally I will never load it on any system that I own, would rather toss all my computers out the window then install that resource, bug ridden security risk M$ calls an OS

---

### Post by Duck2006 on 2008-03-08
It is a program to format and partition your drives. More on the web site.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by halitech on 2008-03-08
> **woodsonoversoul said:**
> what is "gparted"?

its a utility cd for creating partitions

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by Duck2006 on 2008-03-08
> **halitech said:**
> we have it at work to support customers, personally I will never load it on any system that I own, would rather toss all my computers out the window then install that resource, bug ridden security risk M$ calls an OS

Must be bad then.

The other partition program is pmagic

[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

I find this one better than gparted, just because it has more utility on it.

---

### Post by halitech on 2008-03-08
> **Duck2006 said:**
> Must be bad then.


thankfully since I have discovered Ubuntu (and open source in general) I don't have to worry about installing anything M$ on my systems :D

---

### Post by pbpersson on 2008-03-08
Let me throw some ideas out here

It sounds like you have some operating systems that work on here and some that do not

Right now, boot from the 32-bit version of Ubuntu.  Does it still work?  If so, it is **not** just a plain and simple hardware failure where something used to work and is now broken.

Now.....here is a very unscientific test.  Boot from the 32-bit CD and watch the screen carefully.  It will go through a bunch of steps like after the power on self test and the motherboard flash screen - it might say "booting from CD" or "loading GRUB" or "loading Linux Kernel" or whatever.  On the 32-bit version, how long does the CD light blink?  Then load the 64-bit version and see if after the screen turns to white, the CD light keeps blinking.  That would indicate to me the OS is still alive and well, it just cannot communicate with the monitor.

If it used to work with the 32-bit version and then went to all white, did rebooting the maching from the hard drive momentarily fix it?  Did it still work at that point when booting from the CD?  If so, that would indicate that something changed with the configuration on the hard drive.  Did you install some game or application that perhaps changed the video settings?

I would recommend trying my steps above and if you are convinced it is a graphics setting difference between 32-bit and 64-bit versions, re-install the 32-bit version and save a copy of all your video configuration files.  Then when the screen goes white again in the 32-bit mode, boot into the recovery console and see what changed in those files and you will know how to fix it....maybe

Just some thoughts off the top of my head.......


Phil

---

### Post by bill516 on 2008-03-08
Woodsonoversoul:

You say that a 32 bit Linux ran fine for "some weeks" and then went "white screen"?  You had Vista on this box and it worked?  Very flaky indeed.

Seems to me that the first thing you have to do to eliminate hardware/Bios problems is to get something -- anything -- to boot from the CD drive.  First check your BIOS settings and make sure the CD drive is your first boot alternative.

Let's not trust any downloaded iso just yet.   We need a commercially prepared bootable disk that is "known good" to test your machine.  Let me suggest you go to a site such as Distrowatch and you purchase a commercially prepared Knoppix live CD.  If you can, take your new disk to a friend and boot it using that person's CD drive.  If it boots there, it should boot for you.

If it boots in your firiend's machine but not in yours you have a fundamental problem, probably in your Bios.  At that point you may want to visit Biosman.com for help, though laptops are more difficult than desktops if you have to swap a Bios chip.  We'll assume you do not need to do that and that you pass this test.

Next step, assunming the Knoppix live CD boots is to just play with it a bit so that you get comfortable.  You now know the Knoppix CD boots and you know something of how Knoppix is going to run.

Next, we want to attempt to put Knoppix on that har-drive.  We'll let it use and reformat the entire drive, especially since it would appear that we cannot trust whatever formatting has been done.  Best to sweep clean, as several people have suggested.  So let's do that. 

When you do the install indicate that you want to use the entire hard drive and let the install disk format the disk as well.  Let's not get fancy, all we want to do is to reformat that drive,  install something and have it boot.  Any clean 32 bit system should do that, be it Windows (which you appear not to have) or Linux.  (I am suggesting Knoppix because it is a handy emergency live CD to have around no matter what you run.)  In any event you should arrive at a point where you have a reformatted hard drive with a clean Linux installation that you know works, because you booted it as a live disk on your CD.

So, install, take a deep breath and reboot the machine.  If your hardware is good and your software is properly installed this sucker is going to boot.

No boot?  Look right at that hard drive and consider two things:  (a) they do not cost much; (b) on laptops in particular it is an absolutely simple plug system.  Remove the cover, pull out the old drive, plug in the new drive and go.

Let's assume you boot.  (We need a happy ending here somewhere!)

You say you had something running once upon a time and then it went to "white screen?"  Hmmm, perhaps a video failure?   let's test for heat-based corruption and the like.  If that puppy boots and you have a running Knoppix system  turn off any power management and let the machine run ... and run ... and run.  We do not want to break it but we do want to see if your machine  misbehaves when it gets warm and perhaps goes to the infamous "white screen" that is driving you bonkers, as it would me.  72 hours might tell you something.  I am guessing that if it acts up you are going to see something that indicates what is happening.  Do hope you get some error messages before it goes white.  If it does I would look at your graphics card or circuits.  Next guess, memory chips overheating and behaving badly.  But I am guessing, which is not what you need.

So  let's assume none of that happens and you have a perfectly happy little laptop cheerfully running Knoppix.  Hooray!

OK, so we have a good install and all is well.  (We hope!)

At that point you can read Distrowatch for distro reviews and pick one that you think Sis would enjoy using.  Kubuntu is very nice and the Ubuntu forums are terrific, in my experience.

This may not work, but it is how I would attack the problem.  In effect, first rule out hardware problems, then rule out disk problems and then test from there.

Hope this helps and my apologies if it does not.

---

### Post by sgt.splatters on 2008-03-08
I had the same problem with Gutsy Server 64bit, but when I booted the LiveCD of Gutsy Desktop 32bit it installed no problem...

---

### Post by woodsonoversoul on 2008-03-08
Thanks everyone. I'm going to play with these for a while and let you know how it turns out :)

---

### Post by woodsonoversoul on 2008-03-18
Alright! I can boot up through the latest puppy linux. What should I disable (and how) to help Ubuntu boot up?

---

### Post by woodsonoversoul on 2008-03-18
Bump. Any ideas on what I could edit to help Ubuntu 7.10 boot up?

---

### Post by woodsonoversoul on 2008-03-18
Anyone?

---

### Post by woodsonoversoul on 2008-03-18
I'm reading through the boot options and kind of nervous about turning any of these things off

---

