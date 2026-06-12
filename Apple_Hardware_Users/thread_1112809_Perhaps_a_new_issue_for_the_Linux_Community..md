---
title: "Perhaps a new issue for the Linux Community."
date: 2009-04-01
forum: Apple Hardware Users
---

### Post by ihenry00 on 2009-04-01
I have looked EVERYWHERE to try and figure this problem out but it seems nobody has posted anything on my issue.

I am very new to linux and when i say very new i mean i started using it yesterday and i have a dilemma. I have managed to somehow load 8.1 Intrepid onto an imac g3, when i say "load" i mean i have successfully made it through all of the roadblocks and issues paving the path of the ppc. I can boot, reboot, etc. log into the gui and everything seems to be in place no weird colors on screen or anything of that nature, i followed every step i could in installing, booting, editing xorg.conf, editing yaboot. I did it all getting this thing going and finally when all was said and done i was very proud of myself.

So here i am logged into the gui and attempting to update but... nothing will download. So i figure well ill load up firefox and search the net for the "cure." I click firefox a window opens that shows up on the taskbar and begins to load after about 2 seconds the application quits. I then go through the computer trying everything. All of it does this, the only thing i can do is open the file browser. 

Does anybody have any idea why my applications just keep quitting themselves. ALSO i cant access terminal through the GUI i have to ctrl-alt-f2 to get to a command prompt.

---

### Post by ihenry00 on 2009-04-01
*BUMP* Nobody have any ideas what could be causing it?

---

### Post by cyberdork33 on 2009-04-01
1) You should allow a full day before bumping.

2) This is a specific issue with the PowerPC version. I have seen people post about this before. There may be some info at [http://www.ppclinux.info/](http://www.ppclinux.info/)

---

### Post by marshag63 on 2009-04-01
One of the first things to do is change the repositories in your "sources.list" to ubuntu.ports.com  


See this posting:

[http://ubuntuforums.org/showthread.php?t=1084539&highlight=PPC+sources+list](http://ubuntuforums.org/showthread.php?t=1084539&highlight=PPC+sources+list)

Then follow this to add Medibuntu repos (plus add the keyring):

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Install the ppc-codecs

I had the same problem with programs "dying" until I fixed the repos and got the right update track for PPC.

Good luck and let us know how it turns out.

MarshaG.

---

### Post by rodney757 on 2009-04-01
I also just installed the server edition and can't upgrade. If any one has their source list that they could share:).

---

### Post by blackwill86 on 2009-04-02
I'm actually having a similar issue as the original poster on a Powerbook G3 Lombard. Ubuntu 8.10 installed and boots to the desktop fine under GNOME or Xfce... but I cannot launch ANY applications whatsoever. They all begin to load and then close after a second or two.

---

### Post by stream303 on 2009-04-03
8.10 is very problematic with crashing apps for ppc.

At this point, I'd say go back to the 8.04.1 LTS release, or perhaps try again with Jaunty which is coming out soon.  Trying to get 8.10 working might just not be worth the time and effort especially for newcomers to Linux.

OR, I can also recommend Debian, Ubuntu's parent, and as a first attempt the "stable" 5.0 release:

[http://debian.org/distrib/](http://debian.org/distrib/)

---

### Post by blackwill86 on 2009-04-06
As per Stream303's suggestion I tried installing Debian and it works flawlessly. No more crashing apps. In hindsight it might be pertinent to mention I have a dead PRAM battery on this laptop and that may have been causing issues on the Ubuntu install. I was able to adjust the date properly on the Debian install, however any attempts to change the date in 8.10 crashed ALL applets. If I'd manually set the time via terminal that may have gotten me further, but I didn't think to try this at the time. 

Setting the system time via NTP prevents the Debian install from constant lockups and app failures-- I disabled my network adapter a few times to test this and without network connectivity I was experiencing the same kind of failures (less catastrophic) as I was on Ubuntu 8.10

Didn't have time to test out 8.04, but I suspect it would have been more of the same. 

ihenry00, I don't suppose you also have a dead cmos battery?

---

### Post by loyrirk on 2009-04-09
> **blackwill86 said:**
> Didn't have time to test out 8.04, but I suspect it would have been more of the same.

FWIW, I've been using 8.04 on a PowerBook G3 Lombard since 8.04 was released with very few problems.  I've been checking the forums periodically to see other people's experiences with 8.10; due to all the issues with ppc, I've held off on upgrading.  If it ain't broke...

---

### Post by J_Random on 2009-04-18
Good day, everybody!

Well, dear ihenry00, search harder! and you will find :popcorn:
[http://ubuntuforums.org/showthread.php?t=961107&page=2](http://ubuntuforums.org/showthread.php?t=961107&page=2)
I hope this thread would be of assistance.
(I went thru the helluva trouble, installing xubuntu 8.10 on Lombard.)
 
Sincerely yours J_Random

---

### Post by stream303 on 2009-04-18
> **loyrirk said:**
> I've been checking the forums periodically to see other people's experiences with 8.10; due to all the issues with ppc, I've held off on upgrading.  If it ain't broke...

Good point - we have to remember that anything in between LTS releases are essentially a "testing" release only good for 18 months where new ideas and additions are tested on a semi-long basis.  Given that PPC is not exactly officially supported, I think that anyone new to Ubuntu PPC would do well to get their feet wet with an LTS release first - and once past that hurdle, decide if it is worth it to jump into essentially the testing releases.

Strangely enough, Debian actually poses the least amount of up-front problems to the new ppc'er.  You'll still have to deal with some apple quirks, and if Ubuntu for some reason leaves you frustrated on ppc, don't really blame them as it is a um, value-added port. :)

So if Debian works for you getting your feet wet, you can easily make the transition back to Ubuntu if you want since we both share much the same underlying configuration and operations.

Win-win as I like to say. :)

---

