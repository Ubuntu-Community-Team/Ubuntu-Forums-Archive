---
title: "Lots of problems: Freezing, paritioning, videocard driver"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by Henaro on 2007-08-03
Hey everyone~

I've been having a lot of problems lately.  

It all started when I tried to combine two partitions.  When I put in the gparted live CD my monitor came up with a big red OUT OF RANGE box in the middle.  So I hit CTRL ALT and F2.  I went through it's forcevideo script and selected the ATI driver it had listed.  Long story short it gave me all sorts of errors and I eventually said "screw it I'm not in the mood for this today".  So now I restart my computer and go onto ubuntu.  It started up unusually slow.  And I was then greeted by this thing:

[http://img457.imageshack.us/img457/7899/fdupwm6.png]("http://img457.imageshack.us/img457/7899/fdupwm6.png")

Then it went back to the normal login screen.  I've had my graphics driver and themes set up for a long time and I've never seen this before.  I use fglrx and Beryl (because it works and I'm too lazy to upgrade to Compiz Fusion) along with XGL.  I then log in and hit alt and F2 to start beryl.  Then I open firefox and the whole screen flickers to the same image above.  But then firefox loads normally.  And then I open xchat and bam everything freezes.  So I hit the power button.  Then I come back onto my ubuntu install and I'm greeted with the same ugly picture and repeat the process of freezing up my computer.  I have a feeling that my system is still trying to load the video card driver that was on the gparted live CD.  

Does anyone know what the deal with this is?

---

### Post by Midahed on 2007-08-03
Not sure how much I can help, but seeing nobody else is having a go....

First, I'd not worry about the rubbish that gets displayed on the reboot following a video-related crash.  I've seen the same thing and my PC is working fine.  If I run gparted off a CD or even if I'm running X under the SystemRescueCD I find that I get a splash of that sort of corrupted display as the system shuts down.  I then see the same corrupted screen (just for a second) as the system boots up the next time (provided I don't power it off).  It's as though something is left in a video buffer and is carried into the next system boot.  On my system it's only shown for a second and doesn't affect the system in any other way.

As far as your freezes are concerned, I'm not sure what to suggest.  Is it just xchat that causes the problem or do you get the same thing with other apps eventually?  What happens if you boot the live CD in safe mode?  Does it behave better then?  Have you set your monitor to just run in a single resolution or does it have an 'auto' setting where it will try to adapt to whatever the graphics card is throwing at it?  If I have video problems I usually put mine into auto mode until I can find out the source of the problem.

**[EDIT]**  By the way, the slow loading problem after the crash might be because Ubuntu decided to run fsck on your root partition (because the file system wasn't closed cleanly).  

Mike

---

