---
title: "Install 6.10 now or wait for 7.04"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by OneSeventeen on 2007-04-11
I have an HP zv6000 laptop that used to run only Ubuntu Breezy Badger.  (I used Ubuntu for about 6 months to a year as my primary OS)  Then I upgraded to Dapper Drake and could never get my wifi card working again, so I went back to windows.  (I got a new job and didn't have the time to get it working)

So now that I'm slowly learning to separate home life from work life, I was wondering if it would be worth jumping back into Ubuntu via 6.10, or should I just wait until 7.04 since I've gone without Ubuntu for at least 6 months now.

Also, has anyone tried installing 7.04 beta on a laptop?  (Preferrably a zv6000? :D )  I just don't want to go through 30 minutes of wifi troubleshooting just to get the chance at an internet connection in my office.

(I've used ndiswrapper, network manager, and a few other scripts and none seemed to do the trick this last go around...)

---

### Post by joethenoob on 2007-04-11
I've got 7.04 running on a Dell Latitude C400 and using a Proxim 8470-FC for my wireless. Other than a few really big update downloads, I haven't had any problems since the jump from 6.10. I hope it stays that way. Feisty is good, feisty is wise.

---

### Post by jem7v on 2007-04-11
My advice would be to wait 8 days and install Feisty.  It's supposed to have much better support for Wifi out of the box than 6.10.  Why not try the Feisty LiveCD when it comes out?  That might give you an idea whether or not it'll work well on your laptop without having to install it to find out.

---

### Post by igknighted on 2007-04-11
I would try both the live CDs to see if you can get it to work.  If it doesn't and you refuse to fight with it, try using SAM Linux or Mepis, they support many more wifi cards OOTB.

---

### Post by annda on 2007-04-11
do you have integrated wireless? if not, the card is problematic, not the laptop.

i'm very happy with feisty on my samsung x11. but i have standard integrated intel wifi, so that's not an issue.

here's a link to a detailed review of feisty on an HP laptop (but not zv6000):
[http://cpbotha.net/2007/04/10/a-critical-look-at-ubuntu-feisty-beta-on-an-hp-nc8430-laptop/](http://cpbotha.net/2007/04/10/a-critical-look-at-ubuntu-feisty-beta-on-an-hp-nc8430-laptop/)

---

### Post by badduck on 2007-04-19
I tried to install 7.04 on my Dell Latitude C400 with the boot CD, but it didnt work.

It boots, and I end up at the screen where I choose "start or install....."

I choose the "start and install...." and then it starts and freezes. The CD stops, and it is all black.

I tried the CD on antoher computer, and it worked there.

I would appreciate if someone with a Dell Latitude C400 could help me with this issue.

Maybe the dude with "5 cups of ubuntu" knows how to solve this problem :)

---

### Post by igknighted on 2007-04-19
> **badduck said:**
> I tried to install 7.04 on my Dell Latitude C400 with the boot CD, but it didnt work.

It boots, and I end up at the screen where I choose "start or install....."

I choose the "start and install...." and then it starts and freezes. The CD stops, and it is all black.

I tried the CD on antoher computer, and it worked there.

I would appreciate if someone with a Dell Latitude C400 could help me with this issue.

Maybe the dude with "5 cups of ubuntu" knows how to solve this problem :)

Sounds like a graphics card issue... any idea what card is in there?  If it is ATI you may need to try the alternate CD to get it booting, the LiveCD is notoriously bad at recognizing ATI cards and applying the proper driver.

---

### Post by badduck on 2007-04-19
oh, I see.

The graphic chip is a intel i830.

I will try with the alternative CD.

I just felt little strange, because I have read about many users that have installed older versions of ubuntu without any problems.

Well, I usually dont use linux but when I read about the release of ubuntu and how good it is supposed to be, I really like it when I tried it at the other computer :)

---

### Post by igknighted on 2007-04-19
> **badduck said:**
> oh, I see.

The graphic chip is a intel i830.

I will try with the alternative CD.

I just felt little strange, because I have read about many users that have installed older versions of ubuntu without any problems.

Well, I usually dont use linux but when I read about the release of ubuntu and how good it is supposed to be, I really like it when I tried it at the other computer :)

If you just want to test and not install the AlternateCD is not what you want, it is only the installer.  If you are 100% sure the CD is good, post a bug report on the problem.  You might want to try the edgy liveCD for now, then if you decide to install you can upgrade to Feisty.

---

### Post by OneSeventeen on 2007-04-20
Thanks for the tips guys, I just burned my Feisty CD and am going to take it home today.

We upgraded an old P3/Windows 98 box here at work to Ubuntu 7.04 and I forgot how cool linux was!

Other than having to force the screen resolution to 1024x768 (for the sake of the flat panel/video card) the install went insanely smoothly and in a matter of minutes after the install we had a webserver and drupal up and running.

Awesome job and it feels way more responsive than the previous version.  (at least on this machine)

Anyway I'll start a new thread with my experiences on the zv6000

---

### Post by antistar. on 2007-05-03
I had the same issue on my Latitude C400. However installing 7.04 with the Alternate CD worked out just fine.  I still haven't figured out what the problem was with the standard install CD though...maybe a resource allocation issue? Oh well. All's well that ends well...:)

---

