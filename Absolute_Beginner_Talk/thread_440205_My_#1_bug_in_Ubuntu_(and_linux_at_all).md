---
title: "My #1 bug in Ubuntu (and linux at all)"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by garbage_ on 2007-05-11
I am sorry if the title seems a little "anti", but I needed your attention ... :)

I have been with ubuntu on 2 laptops already, since the 5.10 version - always with XP dual-boot.
Since 6.10 went public, and even more with 7.04, I have been scarcely been using windows at all, booting it only to backup my cellphone.

The only thing that makes me somewhat sorry to leave windows is the "screen quality"
what do I mean?
The crisp small fonts that enable me to see alot on my 14.1 widescreen (1280x800) in comparsion to the display in Ubuntu.

I have been trying all kind of solutions that I have found here and all over the web but nothing comes closer :(
(I have used the modified libraries and the xml file from BSD, installed the ms core fonts ...)

Has anyone succeeded in getting a proper resolution?

---

### Post by dstew on 2007-05-11
What is your video card/driver?

---

### Post by rich.bradshaw on 2007-05-11
Why not attach a screen shot?

There should be no problem getting it to look normal!

---

### Post by icechen1 on 2007-05-11
> **garbage_ said:**
> I am sorry if the title seems a little "anti", but I needed your attention ... :)

I have been with ubuntu on 2 laptops already, since the 5.10 version - always with XP dual-boot.
Since 6.10 went public, and even more with 7.04, I have been scarcely been using windows at all, booting it only to backup my cellphone.

The only thing that makes me somewhat sorry to leave windows is the "screen quality"
what do I mean?
The crisp small fonts that enable me to see alot on my 14.1 widescreen (1280x800) in comparsion to the display in Ubuntu.

I have been trying all kind of solutions that I have found here and all over the web but nothing comes closer :(
(I have used the modified libraries and the xml file from BSD, installed the ms core fonts ...)

Has anyone succeeded in getting a proper resolution?
Try 915resolution(find it in synaptic package manager) if you have A [COLOR="Red"]INTEL[/COLOR] VIDEO CARD,Hope this helps!
That solved my problem.

---

### Post by garbage_ on 2007-05-11
rich - I will try to see if I can get a screenshot online ...

dstew - you are right, I have forgotten to post it:
my computer is hp dv2129ea with intel GMA950, 14.1" widescreen 1280x800

thanks for the replies !

---

### Post by icechen1 on 2007-05-11
> **garbage_ said:**
> rich - I will try to see if I can get a screenshot online ...

dstew - you are right, I have forgotten to post it:
my computer is hp dv2129ea with intel GMA950, 14.1" widescreen 1280x800

thanks for the replies !I think you will need 915resolution to fix the problem because it is a INTEL video card.
restart your computer after installing it

---

### Post by Jonne on 2007-05-11
Have you tried enabling font smoothing? It's in the control center, under font. 

or just launch gnome-font-properties.

---

### Post by garbage_ on 2007-05-11
> **Jonne said:**
> Have you tried enabling font smoothing? It's in the control center, under font. 

or just launch gnome-font-properties.

I have enabled the font optimizing for LCD screens with anti aliasing and everything ...

---

### Post by srt4play on 2007-05-11
Are you running 1280x800 or are you having difficulty setting that resolution?

Or are you running your desired resolution and just unhappy with fonts?

---

### Post by Lucifiel on 2007-05-11
Did you try this thread? If not, you should. 

[http://ubuntuforums.org/showthread.php?t=343670](http://ubuntuforums.org/showthread.php?t=343670)

---

### Post by garbage_ on 2007-05-11
> **srt4play said:**
> Are you running 1280x800 or are you having difficulty setting that resolution?

Or are you running your desired resolution and just unhappy with fonts?

I am running at 1280x800 and with enhanced rendering, but still unhappy with the fonts/display.

---

### Post by garbage_ on 2007-05-11
> **Lucifiel said:**
> Did you try this thread? If not, you should. 

[http://ubuntuforums.org/showthread.php?t=343670](http://ubuntuforums.org/showthread.php?t=343670)

yes, I am using this enhancement.

---

### Post by Lucifiel on 2007-05-11
How about these lines of code, then?

You should try adding them into fonts.conf

> <match target='font'>
<edit name='autohint' mode='assign'>
<bool>true</bool>
</edit>
</match>

---

### Post by garbage_ on 2007-05-12
> **Lucifiel said:**
> How about these lines of code, then?

You should try adding them into fonts.conf

Where is this font.conf?

---

### Post by Lucifiel on 2007-05-12
Oh, try this, then!

Press Alt + F2.

A small pop-up window called "Run application" will appear. :)

In that window, type 

> gksudo gedit /home/xxxxxx/.fonts.conf

Please note that xxxx = your username(the one you use to log into Ubuntu). Gksudo gedit will give you temporary root access(like admin access within WinXP) so that you can save the changes you made in fonts.conf :) 

When fonts.conf appears, paste the code I gave you in my previous post but before </fontconfig>. :)

---

### Post by garbage_ on 2007-05-12
> **Lucifiel said:**
> Oh, try this, then!

Press Alt + F2.

A small pop-up window called "Run application" will appear. :)

In that window, type 



Please note that xxxx = your username(the one you use to log into Ubuntu). Gksudo gedit will give you temporary root access(like admin access within WinXP) so that you can save the changes you made in fonts.conf :) 

When fonts.conf appears, paste the code I gave you in my previous post but before </fontconfig>. :)

I did it, logged off and on - still not too much ...

I will keep looking for a solution

Thank you !

---

### Post by Lucifiel on 2007-05-12
> **garbage_ said:**
> I did it, logged off and on - still not too much ...

I will keep looking for a solution

Thank you !

Erm, in order to load the changes to font.conf, you need to restart X.

Close all your windows and then hit Alt+Ctrl+ Backspace.

Sorry I forgot to tell you that.

---

### Post by garbage_ on 2007-05-12
I have restarted X - I don't see any changes, attached is a screenshot.

---

### Post by garbage_ on 2007-05-12
Here I have a screenshot comparing Google in Ubuntu & in XP (under the great VirtualBox)

see the difference ?

---

### Post by Lucifiel on 2007-05-12
Ouch... that looks dreadful!

Have you tried creating a new user profile? And seeing if you still have the same issues? 

System ===> Administration ====> Users and Groups

Then, click on "Add user". :)

Edit: Someone, come in and help this user, please. :P

---

### Post by garbage_ on 2007-05-12
> **Lucifiel said:**
> Ouch... that looks dreadful!

Have you tried creating a new user profile? And seeing if you still have the same issues? 

System ===> Administration ====> Users and Groups

Then, click on "Add user". :)

Edit: Someone, come in and help this user, please. :P

did it - didn't change a thing ...

---

### Post by Lucifiel on 2007-05-13
Okay, just checking. Does your fonts.conf look like this? 

Otherwise, I'm out of ideas. 

> <?xml version="1.0"?><!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>none</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintfull</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
<match target='font'>
<edit name='autohint' mode='assign'>
<bool>true</bool>
</edit>
</match>
</fontconfig>

---

### Post by 3rr0r on 2007-05-13
> **Lucifiel said:**
> Ouch... that looks dreadful!

Have you tried creating a new user profile? And seeing if you still have the same issues? 

System ===> Administration ====> Users and Groups

Then, click on "Add user". :)

Edit: Someone, come in and help this user, please. :P

Can you elaborate on what is dreadful?  I think the ubuntu shot looks better... maybe I'm not seeing what the problem is.

---

### Post by garbage_ on 2007-05-17
3rr0r: the dreadful thing is that the fonts are jagged and not smooth as they are supposed to be.

I think I might have found the problem - I have use the enhanced libraries with a special XML file that was posted here and was imported from FreeBSD - I think the XML file is the problem.
I have installed today a brand new Ubuntu box and used the enhanced libraries WITHOUT the XML file - it looks great !

I will try to see how does it looks with ONLY the XML and afterwards only the enhanced libraries.

I'll report my findings here.

the XML thread:
[http://ubuntuforums.org/showthread.php?t=208396&highlight=xml+font+bsd](http://ubuntuforums.org/showthread.php?t=208396&highlight=xml+font+bsd)

---

### Post by garbage_ on 2007-05-17
removing the XML files solved the problem :)
attached is a screenshot

---

