---
title: "Please Help Fix Annoying Problem - Please Please Please :)"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by luckylucky on 2007-10-23
I've posted a thread before and also replied to a similar thread, but both threads (see below) got buried and no one posted anything helpful... so am hoping that this will resurect the issue, and hopefully some smart person will be able to help :KS

On my laptop (Averatec 1050-EB1 which I've been joyfully using Ubuntu since version 4.x) I have had numerous ubuntu installs, but I've never experience screen flicker until now with 7.10.  I have an intel 855 video card, which I believe is supposed to be 1280x800 but I can only get a max of 1280x768 now (which might be the reason for the screen flicker).  I've tried reconfiguring xorg and have tried everything I can think of to get rid of the seriously annoying screen flicker, but I am totally stumped.  **[COLOR="Red"]Apparently other people are experiencing the same problem, so perhaps this should be looked at for a fix[/COLOR]**.

Here are the links to the other threads on the subject thus far:

[http://ubuntuforums.org/showthread.php?t=586950](http://ubuntuforums.org/showthread.php?t=586950)
[http://ubuntuforums.org/showthread.php?t=579565](http://ubuntuforums.org/showthread.php?t=579565)

I really really really hope that someone can figure this out.  I will be checking back here a few times today for correspondences.  Thank you in advance for any assistance on this matter!

LuckyLucky :cool:

---

### Post by jdfreshwater on 2007-10-23
Have you tried the Screen and Resolution configuration to try and change the refresh rate?  That may be the real problem.

---

### Post by kellemes on 2007-10-23
Can you please post..

/etc/X11/xorg.conf
/var/log/Xorg.0.log

Please post them between [CODE]-tags.

---

### Post by overdrank on 2007-10-23
Hi and I installed 7.10 on a system last night with the  i810 and after the installation I went straight to synaptic manager and searched for intel. I then installed everything that I could that had details for the intel drivers. I do not have that machine up and running now but from memory it was the 915 resolution and another intel driver. Hope this helps and if you need exactly what I installed I will get the system up and running and post the info. :KS

---

### Post by luckylucky on 2007-10-23
> **kellemes said:**
> Can you please post..

/etc/X11/xorg.conf
/var/log/Xorg.0.log

Please post them between [CODE]-tags.


I've attached them both (copied & pasted) into a single text document (please see attached).  Thanks for helping!

---

### Post by luckylucky on 2007-10-23
> **jdfreshwater said:**
> Have you tried the Screen and Resolution configuration to try and change the refresh rate?  That may be the real problem.

Yes, I tried the GUI in system > admin > screen & graphics and I've changed it up to 60 hz from 30.  Those were the only 2 options, and they both flicker.  Thanks for helping!

---

### Post by luckylucky on 2007-10-23
> **overdrank said:**
> Hi and I installed 7.10 on a system last night with the  i810 and after the installation I went straight to synaptic manager and searched for intel. I then installed everything that I could that had details for the intel drivers. I do not have that machine up and running now but from memory it was the 915 resolution and another intel driver. Hope this helps and if you need exactly what I installed I will get the system up and running and post the info. :KS

Thanks for your try.  I've installed 915resolution, though it didn't seem necessary.  I wrote a [howto]("http://ubuntuforums.org/showthread.php?t=225092") on the subject long time ago; I'm saying this to FYI that I know what I am doing with 915resolution, and that it wasn't the magic bullet for this particular issue.

Again, thanks for trying... 

[COLOR="Magenta"][COLOR="Red"]**Still looking for more suggestions... anyone have any ideas**[/COLOR][/COLOR]? ](*,)

---

### Post by overdrank on 2007-10-23
> **luckylucky said:**
> Thanks for your try.  I've installed 915resolution, though it didn't seem necessary.  I wrote a [howto]("http://ubuntuforums.org/showthread.php?t=225092") on the subject long time ago; I'm saying this to FYI that I know what I am doing with 915resolution, and that it wasn't the magic bullet for this particular issue.

Again, thanks for trying... 

[COLOR="Magenta"][COLOR="Red"]**Still looking for more suggestions... anyone have any ideas**[/COLOR][/COLOR]? ](*,)

Ok great and I did not mean to sound demeaning and anyway  just trying to help and good luck! :KS

---

### Post by luckylucky on 2007-10-23
> **overdrank said:**
> Ok great and I did not mean to sound demeaning and anyway  just trying to help and good luck! :KS

Sorry if you read any "tone" in my reply.  I didn't interpret your post as demeaning or anything at all.  I am very grateful that you have attempted to assist.  I said that simply to augment that I've tried 915resolution properly so that someone doesn't think that I'm a noobie that doesn't know what I'm doing and thus keep trying to go down that road.  Overdrank, sorry for any miscommunication.  I respected your post.  Thank you.

---

### Post by overdrank on 2007-10-23
> **luckylucky said:**
> Sorry if you read any "tone" in my reply.  I didn't interpret your post as demeaning or anything at all.  I am very grateful that you have attempted to assist.  I said that simply to augment that I've tried 915resolution properly so that someone doesn't think that I'm a noobie that doesn't know what I'm doing and thus keep trying to go down that road.  Overdrank, sorry for any miscommunication.  I respected your post.  Thank you.

Not at all a problem, just did not want to put the impression out there. :guitar:

---

### Post by ItsMitsHere on 2007-10-23
I think for LCD screens having resolution higher then 1024X786 refresh rate is supposed to be more then 60 Hz. 75 if possible though i am not sure about it...just in case if it works!!!

---

### Post by kellemes on 2007-10-23
Well, can't help you really.. only advice to ask google a lot! Your /var/log/Xorg.0.log shows a couple of error-messages that may lead you to the answer..
For example **intel(0): Unable to read from DVOI2C_E Slave 112** seems to be suggesting  a bug in the inteldriver.. but I'm just not able to pinpoint the problem here..

---

### Post by detroitrockcity on 2007-10-23
I too had an issue with the Intel chipset. However, I was able to correct the flicker by adjusting resolution and refresh rate. It took some experimentation, but it did "correct". I am going to play around a little more  with updating the drivers.

---

### Post by luckylucky on 2007-10-23
Hmmm... now venturing into somewhat unfamiliar territory... how would you suggest I go about changing refresh rates to something higher than the 60 available to me?

---

### Post by bessie31 on 2008-02-12
this is a bug in the intel driver package. there is a patch available here:
[http://folk.ntnu.no/spreeman/deb/ubuntu/gutsy/xserver-xorg-video-intel/](http://folk.ntnu.no/spreeman/deb/ubuntu/gutsy/xserver-xorg-video-intel/)
download the .deb file and run it to install

look for driver version 2.2 here:
[https://launchpad.net/ubuntu/hardy/+source/xserver-xorg-video-intel/2:2.2.0.90-2ubuntu1](https://launchpad.net/ubuntu/hardy/+source/xserver-xorg-video-intel/2:2.2.0.90-2ubuntu1)

but that requires a more difficult install and i have not tried it and i am not sure if the fix is even in that. i think it is.

---

### Post by bessie31 on 2008-02-12
fyi everybody:
the refresh rate is 30 hz.. .even when it says 60.  in simple terms the driver gets incorrect info from the video bios and is unable to set the refresh rate properly

---

### Post by bessie31 on 2008-02-19
oh i forgot:

im not sure about the 2.2 but for the 2.1 driver i linked above

from:

[http://folk.ntnu.no/spreeman/deb/ubuntu/gutsy/xserver-xorg-video-intel/](http://folk.ntnu.no/spreeman/deb/ubuntu/gutsy/xserver-xorg-video-intel/)

after you install it, you also need to edit your xorg.conf file and add 
"Option  "ModeDebug" "true"
to the Device section

to do this you can open terminal and type gksudo gedit /etc/X11/xorg.conf

there you will find a section named "Device" with all the intel 855 description and stuff. you can't miss it. just add that line at the end of that section.

---

### Post by bodhi.zazen on 2008-02-19
> **luckylucky said:**
> I've posted a thread before and also replied to a similar thread, but both threads (see below) got buried and no one posted anything helpful... so am hoping that this will resurect the issue, and hopefully some smart person will be able to help :KS

On my laptop (Averatec 1050-EB1 which I've been joyfully using Ubuntu since version 4.x) I have had numerous ubuntu installs, but I've never experience screen flicker until now with 7.10.  I have an intel 855 video card, which I believe is supposed to be 1280x800 but I can only get a max of 1280x768 now (which might be the reason for the screen flicker).  I've tried reconfiguring xorg and have tried everything I can think of to get rid of the seriously annoying screen flicker, but I am totally stumped.  **[COLOR="Red"]Apparently other people are experiencing the same problem, so perhaps this should be looked at for a fix[/COLOR]**.

Here are the links to the other threads on the subject thus far:

[http://ubuntuforums.org/showthread.php?t=586950](http://ubuntuforums.org/showthread.php?t=586950)
[http://ubuntuforums.org/showthread.php?t=579565](http://ubuntuforums.org/showthread.php?t=579565)

I really really really hope that someone can figure this out.  I will be checking back here a few times today for correspondences.  Thank you in advance for any assistance on this matter!

LuckyLucky :cool:

1. Please Help Fix Annoying Problem - Please Please Please use a better description of your problem / question in the title of your threads.

2. if "**[COLOR="Red"]Apparently other people are experiencing the same problem, so perhaps this should be looked at for a fix[/COLOR]**" you should file a bug report:

How to : [http://ubuntuforums.org/showthread.php?t=284595](http://ubuntuforums.org/showthread.php?t=284595)

---

