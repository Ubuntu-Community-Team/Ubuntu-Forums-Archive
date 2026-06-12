---
title: "Issues with Splash Screen on Boot PowerBook G4?"
date: 2011-09-05
forum: Apple Hardware Users
---

### Post by yokohama1970 on 2011-09-05
Are you a PowerBook G4 1.5/1.67 15.2" Ubuntu 2.6.32-33-powerpc user?
Have you had issues with the "Black Screen" before login, which never goes away, just displays a lot of color arrays?

In order to bypass this:

Power down using power button for 5-10 seconds.

Press Power Button to start up.

Let Yaboot Stage 1 proceed (l=linux, c=cdrom

At Yaboot Stage 2 type:  /boot/vmlinux stuff (return button)


Login as normal.

In your >_ (Terminal)

First:

See 1st Attached Screenshot Below (su -l)

Then:

See 2nd Attached Screenshot Below (Back Up /etc/yaboot.conf)

Then:

See 3rd Attached Screenshot Below (Edit /etc/yaboot.conf)

**This is my actual /etc/yaboot.conf edit**

Then: 

See 4th Attached Screenshot Below (To Save Changes to /etc/yaboot.conf)

Last:

See 5th Attached Screenshot Below (Reboot)

I know this topic has been covered before. But, I believe it should be shared again. Just to clarify, this works on a PowerBook G4 15.2"/1.67/Backlit KB/2gb SDRam/128 ATI Radeon Apple Model A1106.

I know this topic has been posted, replied & covered for G3 iMac, Pismo & G4 Towers, iBook, TiBook,Cube, etc. Just offering guided help for other PowerBook G4 users of the same Model.

Remember you created a /etc/yaboot.conf.backup configuration.

If other users have other settings for "nosplash or quiet splash" /etc/yaboot.conf on Ubuntu 10.04.3 PowerPC. please share that with us. I am curious, too.

Thank You

---

### Post by rsavage on 2011-09-06
yokohama1970, let me first say it's great that you've posted this up to help others.  I have a few queries though:

> **yokohama1970 said:**
> At Yaboot Stage 2 type:  /boot/vmlinux stuff (return button)


Did you mean to say this?  "stuff" seems a bit vague?  I've never had a problem with the splash screen, but from reading other posts it seems a lot of people type "Linux nosplash" at this point.  Does this not work?

> **yokohama1970 said:**
> See 1st Attached Screenshot Below (su -l)


People may run into difficulty with your "su -l" command.  This I think logs you in as root, but on a standard ubuntu there is no root password.  Since you have used "sudo" before every command it is unnecessary to use "su -l".

I'd be interested if you could get the splash screen working using other yaboot parameters.  Try either or both of "radeon.modeset=0" and "video=radeonfb:1024x768-24@60" (or whatever resolution you use).

---

### Post by yokohama1970 on 2011-09-07
Thank You for taking the time to reply. Honestly, I just posted what worked for my PBG4 on 10.04.3 PowerPC. 

Someone posted the /boot/vmlinux stuff suggestion in either xubuntu or lubuntu forum section. I decided to give it a try & it works flawlessly. It is a Verbose Boot Screen without any Splash. It always leads into the Login for Ubuntu. Same with Shutdown, Verbose Screen without any Splash. 

I found that even with "video=ofonly nofb", etc.. I would consistently wind up with the multi-colored/blank screen until Login.

Are you an Ubuntu PowerPC user? If so, would you be able to share your Yaboot/OF settings?

Nice chatting with you.

---

### Post by rsavage on 2011-09-09
Hi again, yes I'm a powerpc user.  I been trying to put together a single post with a lot of the known fixes on.  This I hope will make it easier for people to install ubuntu.  That is why I was quite interested in your thread!  It is really hard to get feedback so I'm grateful for your reply.

I have a g4 ibook with a radeon card, but I haven't had any problems with the splash screen.  When I ran maverick or lucid I used radeon.modeset=0 to turn off kms.  This increased the 3d performance of my particular card.  Then I had to setup an xorg.conf file to make sure I was using EXA (otherwise I had choppy scrolling in firefox).  I did a few other tweaks in there too.

Can you confirm if typing "Linux nosplash" turns off the troublesome splash screen?  This is what I have written in my guide at the moment.  If you could test out the other commands I gave in the previous post I'd be really grateful.

Thanks

---

### Post by yokohama1970 on 2011-09-11
Linux nosplash actually executes the same Verbose Boot Screen as /boot/vmlinux stuff. So, both of those commands work. As for Xorg.conf edit, that would depend on which ATI Video Card each version has installed? It is entirely possible that your Xorg.conf edit may work on any ATI Video Card, since PowerPC boot is dependent on Open Firmware (OF)?

Your Xorg.conf edits have helped with Mozilla Firefox scrolling? Any others?

Currently, I am trying to install a Canon Pixma MX340. Unfortunately, the Linux Drivers from Canon are "cnijfilter-mx340series-3.30-1-i386-deb". As I expected, i386 (Intel). I will try again using Static IP & Wi-Fi. Worst case, I will FTP files from Ubuntu to my MacBookPro & print that way. Patience is a must for any Linux Distro User, but particularly required for Linux PowerPC users. Please, reach out for assistance. 

If we have lost anyone in this discussion, I apologize. I am including a great Apple/Mac Resource Link at the end. 

Basically, All variants of the Linux Kernel, whether Gnome or KDE perform exceptionally well considering the age of various hardware,from numerous vendors/manufacturers. The Open-Source world has an amazing amount of talented, good-natured members. They contribute, revise & assist so many of us (end-users) without hesitation. For their humble, helpful & honest desire to raise awareness with regards to Open-Source, this end-user gratefully says Thank You.

[http://www.everymac.com/]("http://www.everymac.com/")

---

### Post by yokohama1970 on 2011-09-11
One more thing.

Out of the numerous nosplash options. I would stick to Linux nosplash or /boot/vmlinux stuff. Those two choices are consistent. Hope that helps.

Peace Out

---

### Post by rsavage on 2011-09-11
Thanks for the info on the splash screen.  Much appreciated.

The only other thing I do to my xorg.conf on my ibook is adjust the gart size (to 16).  The best thing to do is install glxgears and have a play.  I also use the 3d screensavers to test. If you get something that says "software rasterizer" in glxgears then you need to turn off kms using radeon.modeset=0.  This affected my firefox scrolling until I set exa.  In natty, exa doesn't work so well, but I don't have the choppy scrolling problem with xaa so that's alright.  Are you following?!

I don't know anything about printing, but could you compile your driver?  A quick google search revealed canon provide source code [http://support-au.canon.com.au/P/search?model=PIXMA+MX340&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-au.canon.com.au/P/search?model=PIXMA+MX340&menu=download&filter=0&tagname=g_os&g_os=Linux)

---

### Post by rsavage on 2011-09-11
Also, what about a newer version of ubuntu?  Does that have the printer driver in already [http://ubuntuforums.org/showthread.php?t=1720599](http://ubuntuforums.org/showthread.php?t=1720599) ?

---

### Post by rsavage on 2011-09-12
I did have a quick go at building the printer driver package for you. There is some binary blob (libcnnet.so) that causes an error though.

[http://en.gentoo-wiki.com/wiki/Canon_Pixma_Series](http://en.gentoo-wiki.com/wiki/Canon_Pixma_Series)

I'm afraid I know nothing about printing in ubuntu......

---

### Post by yokohama1970 on 2011-09-12
I appreciate your research & time spent looking for Canon Pixma Drivers. Everything is for i386 or AMD64 Architecture, though.

I will just set it up as a Network Printer using CUPS. If no go, no printing using PowerBook G4 Ubuntu PowerPC. 

I would like to add that in my opinion, KTorrent is much better than Vuze (Azureus), when using a Linux Distro. Exactly the opposite of Mac OS. Any opinions about BitTorrent Clients?

By the way which Adobe Flash alternative have you found to work the best? Nothing I am running seems to work. Ironically, I just read that Abode has developed & released Flash for iOS Devices. Check out the sticker price for Server Clients! Holy f'in ....!!

[http://www.slashgear.com/adobe-finally-brings-flash-support-to-ios-devices-09178463/]("http://www.slashgear.com/adobe-finally-brings-flash-support-to-ios-devices-09178463/")

---

### Post by rsavage on 2011-09-12
Pretty much my entire linux knowledge is contained in this thread [http://ubuntuforums.org/showthread.php?t=1798792](http://ubuntuforums.org/showthread.php?t=1798792)!  (I've yet to incorporate your advice into it)

For youtube there are like a gazillion ways and everyone seems to have there personal opinion on what is best.  Myself, I don't think you'll beat the firefox extension FlashVideoReplacer.  Youtube is a phenomenon that has passed me by though and I rarely use it. 

For general flash there is Gnash.  You may want to install/compile the latest version.

I've also got good at finding the rtmp streams using wireshark so I can bypass flash for things like radio/tv streaming.

Basically, I can live without flash so I don't use any alternatives!  The only thing I miss is audio/video clips on news sites.

Sorry don't use torrent stuff either!

---

### Post by yokohama1970 on 2011-09-12
Thank You for the link. Not having Flash, I agree is missed when viewing sites with embedded video. I will try your suggestion. Gnash has not worked at all. I along with many others are anxiously awaiting HTML5 mainstream as a Flash killer.

Also, I tried Linux nosplash-powerpc during Stage 2 Boot for a successful Verbose Boot.

---

