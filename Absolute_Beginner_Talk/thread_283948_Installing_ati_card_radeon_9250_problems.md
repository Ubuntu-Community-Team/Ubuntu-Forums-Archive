---
title: "Installing ati card radeon 9250 problems"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by KYhillbilly2006 on 2006-10-24
I am trying to get a Radeon 9250 agp card to work.  I keep getting that my X server is not configured right when I boot up computer.  I got the drivers installed and ran the aticonfig but still my X server is not configured right.  

What do I need to do to make it right?

---

### Post by john.nicholls on 2006-10-25
Have you tried running 
sudo dpkg-reconfigure xserver-xorg
and selecting the ati driver?

John

---

### Post by zman58 on 2006-11-03
I have been trying an ATI 9250 card "Diamond Stealth Radeon 9250". It seems to work well using the ATI driver with everything except BZFlag, where it can lock up my desktop hard, requiring a manual power down to recover. Athlon 2600 system.

On another system, an IBM Thinkpad T40 with a Radeon Mobility 9000, everything is working flawlessly, including BZFlag. I expected the 9250 to perform slightly better, but have been disappointed so far. I have tried the fglrx proprietary driver also, which came up without 3D working. Blah!

I get pretty much the same with Mepis 6.0 as with UBUNTU Dapper. BZFLAG just seems to take my system out with the ATI 9250 in place. Perhaps I'll just have to go back to the Nvidie GE force 4 MX440, which seemed to work reasonably well with the nvidia driver.

---

### Post by theicyj on 2006-11-03
I have had great success using the ati driver installation guide at [http://wiki.cchtml.com/index.php/Ubuntu]("http://wiki.cchtml.com/index.php/Ubuntu").  Worked for both a Radeon 9000 and 9250.  Maybe worth a look.

---

### Post by jimbro on 2007-10-19
Have you tried to adjust XORG.CONF?

I recently had this same problem with a Dell Optiplex that wouldn't let me boot into Ubuntu.  I took a look at the eror log and and noticed the PCI slot was misreported.  When I plugged those numbers into the correct part 
of xorg.conf--voila up comes Ubuntu pretty as you please

Sure hope this helps you

---

### Post by PPAAUULL on 2007-10-19
THIS CARD IS A PAIN IN THE BUTT!!!!

I have spent months trying to get it to work and as of yet haven't gotten it working. I can tell you that if you want 3D effects, they are out of the question and games don't preform. You also can't use the fglrx driver in the repos in 7.04

---

### Post by oedenfield on 2007-11-13
I'll second the distaste in my mouth for my ATI Radeon 9250 video card and Ubuntu.  I've tried it with Ubuntu Feisty and now with Gutsy and also with Linux Mint Cassandra KDE Community and had the best luck with Linux Mint. Mint used an old release of Beryl and it had much better support for the card as far as the 3D graphics goes ("visual effects").  Most of the visuals worked like a charm...   when Mint it's self wanted to use the driver that they worked in (about 30% of the time it would use some other driver that didn't do the graphics..  and this was with no changing by myself.. this all happened on it's own before any tweaking on my part).  *Linux Mint is derived from Ubuntu*

I've posted a few times here in the official Ubuntu forms and in the Linux Mint forums with little or no help from anyone really wanting to help solve this problem.  Guess there aren't too many of us out there with the Radeon 9250.

I'm just dealing without the fancy graphics.  In Feisty I installed the driver from ATI and noticed a HUGH slow down in performance..  made me think I was using Windows.

One of these days I'll have Ubuntu on a faster machine with better graphcis..  until then I'm enjoying the many other benefits to using Ubuntu.

(yep..  given up on Radeon 9250)

---

### Post by eldepeche on 2007-11-13
The Radeon 9250 is pretty well-supported by the free "radeon" driver, and I think ATI dropped support for it in their proprietary driver. Try changing the driver to radeon in xorg.conf .

---

