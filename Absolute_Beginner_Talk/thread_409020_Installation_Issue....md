---
title: "Installation Issue..."
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by akthomas89 on 2007-04-14
Okay, so I recently got an old laptop (not the one I use currently) that my dad hasn't used in years - one of his old work laptops (An IBM Thinkpad T40, to be specific). As such, it was configured with xp professional and did work related things that I did not want to to do (i.e. attempt to connect to the Reuters server at startup).

So I figured, this is an old laptop, I need to install a new OS anyway, and my only microsoft option would be Windows 98. I'm not really a fan of Microsoft as it is, and with their new anti-piracy policy, running a bootlegged copy of XP does not seem possible. I also dislike the prospect of not having support for my OS. Since Linux is something I've always a curiousity for in the back of my mind, I figure this is a good time to explore that - when I need an OS and have nothing to lose on the laptop.

I downloaded the 6.10 ISO burned it to a disc (properly - when exploring all the files are there, not a single ISO, and when running "startCD" I get some Ubuntu Demo thing, explaining generic things about the OS and open source in general). I put it in my drive and opened the boot list during start up, specifying to boot from the disc drive. the Ubuntu screen comes up, with various F button commands at the bottom and a list of options - something to the effect of "1. start or install  2. start in safe graphics mode  3. check for defects  4. memtest," and a fifth option that I can't recall off the top of my head.

So I decided I want to get the computer up and running, and the sooner the better. So I choose to start/install. In the upper left hand corner, "Loading" in green type appears. So far so good. after about 10 minutes, I'm starting to wonder how long this load takes. After about 20 minutes I decide it may have locked up, and go to restart. I repeat the same steps, and loading appears in the green type again. 20 minutes pass and the screen does not change. I restart again and decide to use the "check for defects" option. This yields the same green loading type, and the same long waiting period with no result.

So I decide it may just be a bad burn, and burn a new disc to use. Same problem. This time I do other things while it's 'loading,' such as watching south park or whatever else. I come back after an hour or so with still no change.

Then I burn a 6.06 LTS disc and try it instead. Same bloody result (or lack thereof)! I think the disc drive may be shot (it's an old laptop and I have not used the disc drive for anything else), so I test this with my Windows 98 disc. This installs without a hitch. Unfortunately I don't want 98 one bit. I reformat the drive again and set up a blank partition. I decide to switch laptops, just to test the Ubuntu disc. On my current laptop (with the boot order changed to load from the cd drive first), the disc does not load at all. The computer goes straight to booting from the HDD. 

So I would like to pose the question, if you have stuck with me through all of this prefacing :) : Am I dumb? Am I doing something wrong? I have friends who use Ubuntu and it installed on multiple machines just fine, yet on my own two it fails to work at all. Is this bad luck?

Any assistance at all would be super awesome. By this point I'm sick of trying, but I really don't want to leave this laptop unused for a reason as super lame as this.

Thanks in advance, and thanks for reading through this whole spiel!

---

### Post by kelbizzle on 2007-04-14
Nah you didn't do anything wrong. It happend to me on my notebook and desktop. I had to use the alternate cd on both. Maybe thats what you need. Get the alt cd and burn it at 1x to be sure it burned correctly.

Edit: Oh yea the alternate cd is not a live cd. It's just an install cd.

---

### Post by akthomas89 on 2007-04-14
Thanks for the quick reply! Where would I find this alternate CD?

---

### Post by jfinkels on 2007-04-14
Hello! I have seen similar things happening when trying to install on very old hardware...do you have a very old laptop? perhaps others will be able to help you with this problem

---

### Post by kelbizzle on 2007-04-14
[http://www.gtlib.gatech.edu/pub/ubuntu-releases/6.10/ubuntu-6.10-alternate-i386.iso](http://www.gtlib.gatech.edu/pub/ubuntu-releases/6.10/ubuntu-6.10-alternate-i386.iso)


EDit: If you need a different version heres where they all reside [http://www.gtlib.gatech.edu/pub/ubuntu-releases/6.10/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/6.10/)

---

### Post by akthomas89 on 2007-04-14
Well, this was the last laptop my dad had before he stopped work at Reuters, which wouldn't have been more than a couple years ago, though I'm sure he had it for multiple years before he left. 2001 at the earliest, as it is designed for XP if I'm not mistaken.

Thanks for the link, I'm going to try right away :D .

---

### Post by D!mon on 2007-04-14
well if it is designed for xp it should run Ubuntu quite smoothly I think.
What kind of video card it has? Btw, it could be worth to wait a little for fiesty release many things are improved there

---

### Post by kelbizzle on 2007-04-14
> **akthomas89 said:**
> Well, this was the last laptop my dad had before he stopped work at Reuters, which wouldn't have been more than a couple years ago, though I'm sure he had it for multiple years before he left. 2001 at the earliest, as it is designed for XP if I'm not mistaken.

Thanks for the link, I'm going to try right away :D .

your welcome. I'll cross my fingers for you.

---

### Post by hyper_ch on 2007-04-14
How much ram have you got?

---

### Post by akthomas89 on 2007-04-14
Without an OS I can't easily check my specifications, however I looked the specs up on cNet and it lists the computer as being powered by a AGP 4x Mobility Radeon 9000. However, it also lists the ha$rd drive as being 80 gigs, when I know for a fact my hard drive is just short of 40 gigs, leading me to believe that that may not be accurate.

EDIT: the computer is listed as having 512 megs of ram.

---

### Post by hyper_ch on 2007-04-14
well, you have enough ram to run the liveCD :) so that shouldn't be the problem. It may well be that the ATI card is the thing that gives you trouble. Generally ATI has more troubles in Linux than nVidia cards as nVidia offers proprietary drivers for linux.

Have you tried running the alternate installation CD yet?

---

### Post by akthomas89 on 2007-04-14
The LiveCD didn't work on either of my laptops either. The startCD.exe said restart your computer and it will restart with linux running from the CD, yet it never did. I'm not too worried about it, as the thinkpad has no OS as it is, so there's nothing to ruin :D .

I'm burning the alternate CD as I write this. Hopefully it's gonna work!

---

### Post by akthomas89 on 2007-04-15
Okay, so I downloaded the ISO for the alternative CD and copied it to a disc. It allows me to get to the boot screen and start the installation process. However, every time it starts installing the base system, there are files that can't be copied.

I made a 2nd and 3rd disc, both which has files that could not be copied in different areas. Would this be a hardware related problem? Or perhaps a problem with the ISO I downloaded? Or a problem with the computer I'm trying to install it on?

---

