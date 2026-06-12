---
title: "No Svideo Out on Powerbook G4... :("
date: 2011-09-19
forum: Apple Hardware Users
---

### Post by aleelaiuy on 2011-09-19
Hi!!

Just managed to install Ubuntu 10.10 on a Powerbook G4 15' 1.5Ghz with WifiXtreme - made it work!!  :D
But I'm having a pain with the video card... ATI Mobility 9700 128mb

Can't use the Svideo out to hook it up to the TV set...

Tried updating it to 11.04, didn't solve it and I feel it is way slower now...

Tried sudo apt-get install atitvout

It says it can find de package

Tried Installing additional drivers and it kept applying something for an hour and then I restarted it...

Any available help on those, please?

Thanks!!

---

### Post by rsavage on 2011-09-20
I'll have a stab at this.  Based on the links in this [http://ubuntuforums.org/showthread.php?t=1798792](http://ubuntuforums.org/showthread.php?t=1798792)
 
At second yaboot prompt type
 
Linux video=LVDS-1:d video=S-video:e
 
Setting up an xorg.conf would be the permanet solution [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) .

---

### Post by aleelaiuy on 2012-05-22
Hi Rsavage!

Thanks for the reply!! I actually tried a lot and then gave up on it back then...
Took me sometime to get over it and start trying again!! My PB just sat on my living room shelve for the last 6 months... hheheheh :/

 Well, I've resintalled the ubuntu 10.04 - someone told me it would be better choice for my powerbook...

Anyway, the wi-fi was right-out-of-the-box working... but the s-video is still an issue...
I've tried the Linux video=LVDS-1:d video=S-video:e
but didn't work.

And also tried the xrandr... nothing either... it says:

aleelaiuy@aleelaiuy-laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 854, maximum 2048 x 2048
LVDS connected 1280x854+0+0 (normal left inverted right x axis y axis) 321mm x 214mm
   1280x854       60.0*+
   1280x800       59.8  
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   640x480        59.4  
DVI-0 disconnected (normal left inverted right x axis y axis)
S-video disconnected (normal left inverted right x axis y axis)

Somehow I think the problem is with that disconnected there.... the s-video cable is acctually physicaly conneceted.

Anyways... I'm really new to Linux and also don't quite know the terminal commands, what is xorg.conf etc

I'd really appreciate some help... I still wanna use the ubuntu!

Thank you very much again!

---

### Post by rsavage on 2012-05-22
I may have led you up the garden path with that command (or at least it probably wouldn't of worked on its own).  

Better documentation is here [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ) , although whether it is possible to use the S-video with a radeon card I have no idea.

Hopefully you have found out how to turn KMS off by now.  Have you tried that and just used the GUI monitor detect settings?  Or how about turning KMS fully on?

---

### Post by rsavage on 2012-05-22
My first hit on a google search:

xrandr --output S-video --set load_detection 1

From [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/318184](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/318184)

---

### Post by rsavage on 2012-05-23
Reading the radeon manual again to try and solve a problem I have with kubuntu (xorg crashes when you unminimise firefox), I came across this:
 
       **Option** **"ForceTVOut"** **"**_boolean_**"**
              Enable this option to force TV-out  to  always  be  detected  as
              attached.  The default is **off**

From [http://manpages.ubuntu.com/manpages/oneiric/en/man4/radeon.4.html](http://manpages.ubuntu.com/manpages/oneiric/en/man4/radeon.4.html)
 
More on s-video type stuff here [http://www.thinkwiki.org/wiki/How_to_get_TV-Out_working_on_ATI_graphic_cards](http://www.thinkwiki.org/wiki/How_to_get_TV-Out_working_on_ATI_graphic_cards)

---

### Post by aleelaiuy on 2012-05-23
That's nice!! Thank you very much again!

So, how should I proceed to install this radeon.4.gz?? I'm really new to all this... I'm sorry to be asking you all the time...

Like, I dunno what KMS is...

:(

But I'm decided to learn it! :D

---

### Post by stalkingwolf on 2012-05-23
I had this problem with a dell M6300 just a couple days ago.  Im running Zorin.
The answer i found was none of the external outputs were turned on so to speak.  I have an nvidia card so all it needed was to make sure the additional drivers were activated and then go into the nvidia control panel and configure
the external display.  in about 30 minutes i had both an external monitor and tv running fine.

---

### Post by aleelaiuy on 2012-05-24
[SIZE=4]MADE IT!!![/SIZE]

HA HA HA!!! After days of exhaustive trying I did it!!!

Don't ask me how... I tried so much stuff... But I think it was building a xorg.conf and the installing gxrandr and then using the 
xrandr --output S-video --set load_detection 1

All together i think... Hehhehehe!
Anyways!! Thank you a lot for your patience and help!!!

CheerS!

P.S: I'm even afraid of rebooting this thing now! :D

---

