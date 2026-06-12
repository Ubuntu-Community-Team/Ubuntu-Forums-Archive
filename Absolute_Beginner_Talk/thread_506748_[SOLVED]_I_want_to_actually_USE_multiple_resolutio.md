---
title: "[SOLVED] I want to actually USE multiple resolutions"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by anewguy on 2007-07-22
I have my Gateway MX3215 running at a 1024x768 resolution.  If it helps any in this question, the laptop uses a Via S3G Unichrome PRO IGP and I have installed the Openchrome 2D and 3D drivers (I'm running 7.04).  I have 3 resolutions in my xorg.conf:  1024x786  800x600  640x400.  

What I cannot for the life of me figure out is how to get any resolution other than 1024x768 working by switching it via system/preferences/screen resolution.  Everytime I try that it appears that 1 of the frequencies or something is off, because it just makes a mess of the screen that I can't read, so I let it time out back to 1024x768.  I followed the instructions for running a config of xserver-org, selected via, gave it the memory I have allocated in the bios, and chose my 3 resolutions.

Can anyone tell me how to actually get the ability to swtich resolutions on the fly via the system/preferences/screen resolution? 

Thank you!:)

---

### Post by splintercellguy on 2007-07-22
You might have to do:

sudo dpkg-reconfigure xserver-xorg

Be sure to do this before doing the above:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

This is so you have a backup of your xorg.conf in case something goes wrong.

---

### Post by anewguy on 2007-07-22
> **splintercellguy said:**
> You might have to do:

sudo dpkg-reconfigure xserver-xorg

Be sure to do this before doing the above:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

This is so you have a backup of your xorg.conf in case something goes wrong.

That's what I did to reconfigure xorg.  As noted above, that still didn't work.:)

---

### Post by crjackson on 2007-07-22
Good luck on getting any help.  Look at my thread below and ALL the responses.  I have the same problem but on a different system/setup.

[http://ubuntuforums.org/showthread.php?t=490702]("http://ubuntuforums.org/showthread.php?t=490702")

---

### Post by anewguy on 2007-07-22
I have checked the OpenChrome Via drive options for xorg.conf, and cannot find anything that references this.  I am sure that in most (if not all) of these cases, the problem is in trying to figure out what horizontal frequencies and vertical refresh to use in what combination to make this work.  Unfortunately, I don't have a clue on how to go about trying to figure this out.  Is there any how-to somewhere on horizontal/vertical combinations so you can actually use multiple resolutions?:)

---

### Post by anewguy on 2007-07-23
bump.

I know that if I really lower the vertical refresh setting in the device section of my xorg.conf, I get only 640x480, so I figure there must be some combination of vertical refresh rate and resolution for each resolution I want - can anybody tell me how to figure this out for a laptop 14" wxga lcd screen? Is there a way to define a different set of frequencies for each resolution on a mode line in the xorg.conf file?:confused:

I'd really like this to work, and it would greatly enhance my understanding.:)

---

### Post by pyros on 2007-07-23
> **anewguy said:**
> bump.

I know that if I really lower the vertical refresh setting in the device section of my xorg.conf, I get only 640x480, so I figure there must be some combination of vertical refresh rate and resolution for each resolution I want - can anybody tell me how to figure this out for a laptop 14" wxga lcd screen? Is there a way to define a different set of frequencies for each resolution on a mode line in the xorg.conf file?:confused:

I'd really like this to work, and it would greatly enhance my understanding.:)

if you contact the manufacturer of your laptop, or check with whatever online documentation they offer, you should be able to find what the proper refresh rates are for the various resolutions. Keep in mind though, LCDs, unlike CRTs are more limited to what resolutions they can physically display.

---

### Post by anewguy on 2007-07-23
> **pyros said:**
> if you contact the manufacturer of your laptop, or check with whatever online documentation they offer, you should be able to find what the proper refresh rates are for the various resolutions. Keep in mind though, LCDs, unlike CRTs are more limited to what resolutions they can physically display.

Thanks!  I've checked the documentation, both on my PC and on Gateway's web site, but I haven't actually contacted them yet.  I'll get off to that right now!  Thanks!:)

---

### Post by anewguy on 2007-07-24
Well, no reply from Gateway yet.  I also checked this site 

[http://en.opensuse.org/VIA#Activate_MPEG2_and_3D_hardware_acceleration]("http://en.opensuse.org/VIA#Activate_MPEG2_and_3D_hardware_acceleration")

and tried some of the stuff there for multiple frequencies for the various resolutions.  This still doesn't work on my laptop.  Anyone have ANY ideas on this?:)

---

### Post by crjackson on 2007-08-23
> **anewguy said:**
> Well, no reply from Gateway yet.  I also checked this site 

[http://en.opensuse.org/VIA#Activate_MPEG2_and_3D_hardware_acceleration]("http://en.opensuse.org/VIA#Activate_MPEG2_and_3D_hardware_acceleration")

and tried some of the stuff there for multiple frequencies for the various resolutions.  This still doesn't work on my laptop.  Anyone have ANY ideas on this?:)

Did you ever get this resolved.  I'm just about ready to tackle an install on my laptop (tried it before - wiped it after no success).

Learning more on the desktops every day and now I'd like to properly go U on my laptop too...

---

### Post by anewguy on 2007-08-24
No, never got a solution.  Gateway never responded to my request for the freq/refresh needed for each resolution.  Without that, I don't see anyway to specify the multiple resolutions and actually have them all work.  I have only been able to get 1 setting to work.

Best of luck with yours.:)

---

### Post by crjackson on 2007-08-24
I would be happy to get the 1200x800 working.  I don't use the laptop for anything but business and that's the only res I use.  I can click on that res. as MANY are available, but if I change to anything other than 1024x768 the screen gets garbled/corrupt like the freqs. are wrong.  I don't know the proper setting for this eMachines M6809 (Gateway) so I don't have a clue as to where to start.

---

### Post by anewguy on 2007-08-24
Did you add that resolution to your xorg.conf file?  Do you have horz and vert refresh rates specified in xorg.conf?  Perhaps you could just post your xorg.conf file here and we can take a look at it.:)

---

### Post by mysticmatrix on 2007-08-24
Well refresh rate are concerned with your MONITOR, not the graphics card.
Most probably you can google search "<your monitor model> specs" to find out refresh rates, supported resolutions, etc.

---

### Post by anewguy on 2007-08-24
> **mysticmatrix said:**
> Well refresh rate are concerned with your MONITOR, not the graphics card.
Most probably you can google search "<your monitor model> specs" to find out refresh rates, supported resolutions, etc.

Yes, the rates refer to the monitor.  Hence why it is in the monitor section of xorg.conf.  You can define your video up the wazzo but you still need the monitor section defined correctly as well.  But the 2 do go hand in hand,  that's why in my initial response included the driver for the video controller.   The IGP in my laptop is using an "iffy" driver but the best that can be found.  It has it's own restrictions, and some of those restrictions can effect what you are allowed for resolution, regardless of the "monitor".  This holds true for any video card/monitor combination.  Sometimes the video adapter can do more than the monitor can support, sometimes it's the opposite and the card can't generate everything the monitor is capable of.  They go hand in hand and have to be considered together.  Additionally, following this thread, you will see 2 things:

(1)  it's a laptop using the LCD
(2) Gateway has not replied to questions about the various freqs versus resolutions possible on the LCD. 

If you know the answers to those questions, please provide them.  If you have found those specs via a Google search - please provide them.  I had already done MANY searches via Yahoo and Google and found nothing before I ever created this post.

---

### Post by crjackson on 2007-08-24
Try here [http://ubuntuforums.org/showthread.php?t=32495&highlight=fglrx+8.14.13]("http://ubuntuforums.org/showthread.php?t=32495&highlight=fglrx+8.14.13") and here [http://www.notebookforums.com/showthread.php?t=110502]("http://www.notebookforums.com/showthread.php?t=110502")

I'm going to try again in a week or so.  Maybe between the two of us working on it, we can find a solution.

---

### Post by anewguy on 2007-08-24
I just finished up another support chat with Gateway, only to be faced with this:

- your motherboard is made by Arima
- we have no contact information for them

Great.  They sell a laptop with an OEM motherboard and then don't have contact information for that manufacturer?

---

### Post by crjackson on 2007-08-24
> **anewguy said:**
> I just finished up another support chat with Gateway, only to be faced with this:

- your motherboard is made by Arima
- we have no contact information for them

Great.  They sell a laptop with an OEM motherboard and then don't have contact information for that manufacturer?

I wouldn't worry about that.  It's the LCD and Video we are concerned with.

---

### Post by anewguy on 2007-08-25
Well, the thing is, I think the entire laptop was made by them.  In addition, the video is an integrated processor on that motherboard.  I have sent a request to them to see if they can help.  Gateway doesn't have a clue what I'm talking about when I email or chat with them.

---

### Post by crjackson on 2007-08-25
Okay, this may or may not help you but I got mine working with very little effort.

The applet that is used for selecting the screen resolution gave me all my resolutions.  The problem is that when I selected my needed resolution of 1280x800 the screen when all garbled and it couldn't be read.

All I did was edit the xorg.conf file and added the resolution in front of EVERY resolution line entry in the file.  I did the ctrl+alt+backspace and BANG!  It worked perfectly and screen is crisp at correct resolution.

I did NOT install any ATI drivers, only the default installed drivers SO FAR!...

I´ve go to get my wireless working next then I&#314;l tackle 3D acceleration. 

Have you had any luck so far?

---

### Post by anewguy on 2007-08-26
Yeah, I've already got my multiple resolutions set in xorg.conf, but will only let me use the first one.  Any of the other resolutions result in an unreadable screen.  I know that if I play with the frequencies I have been able to make other resolutions work 1 at a time, but I don't know the exact frequencies I need to specify on the mode lines so each will be accessable without needing to re-do xorg.conf and restarting the x server.

Glad you got yours working the way you wanted.  I have my high resolution, I just can't switch to one of the others.:)

---

### Post by anewguy on 2007-10-21
No response from Gateway on teh vert/horiz ranges and resolutions for this laptop.  Since no solution appears available, I will marked this thread closed.

---

### Post by crjackson on 2007-10-21
> **anewguy said:**
> No response from Gateway on teh vert/horiz ranges and resolutions for this laptop.  Since no solution appears available, I will marked this thread closed.

Hey anewguy, have you tried gutsy?  It did everything properly from the 1st boot.  Both LiveCD and fresh install.  Gutsy did kill my wireless but I'm working on that one now.

---

