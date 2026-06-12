---
title: "Macbook 3.1 dual monitor to TV issues!!!"
date: 2010-10-05
forum: Apple Hardware Users
---

### Post by 31632531 on 2010-10-05
HI!

I've got Ubuntu 10.04 installed on a white Macbook 3.1 fully updated.

My second monitor (which is a tv) is displaying in black and white only ...it is fuzzy and jittery and also seems to be doubled and mis-aligned on the screen.

I've been trying to troubleshoot this all night ...I've tried xrandr config options/xinerama configs/creating xorg file and messing about with it/reinstall with tv plugged in during install.  None of these seem to have any positive affect.

In my googling I've found a bug report: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/116207](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/116207)

I guess all I need to know now is the sad truth that I'm dealing with a 3 year old bug here?? Can any one confirm/deny that?

I'm open to trying anything here...I really want to make the full switch away from OSX this dual monitor thing is the second last step (the last step involves using some digidesign hardware as a sound card) to doing everything the same on both OS's.

At least just tell me there's no hope so I can sleep :P

---

### Post by 31632531 on 2010-10-05
oh!

attempting an upgrade to the rc of 10.10 just to see if it's something that has gotten fixed in the release..will report back

---

### Post by 31632531 on 2010-10-05
update:

So 10.10 doesn't change anything

However, it does make a difference what desktop background i use..

Solid colors tend to be more stable on the second display (tv)

Could it be a bit depth issue?

---

### Post by jwhendy on 2010-10-07
What kind of connection are you using? I can confirm that on a 2,1 MacBook I get static when using my mini-DVI -> S-Video adapter to my TV. I'd love to get this resolved as well but have not yet. I'll do some digging and get back to you. 

What adapter/port are you trying to use?

---

### Post by 31632531 on 2010-10-08
> **jwhendy said:**
> What kind of connection are you using? I can confirm that on a 2,1 MacBook I get static when using my mini-DVI -> S-Video adapter to my TV. I'd love to get this resolved as well but have not yet. I'll do some digging and get back to you. 

What adapter/port are you trying to use?

I'm using the same adapter/port as you only instead of s-video I'm using the RCA out from the same adapter (my tv is older than yours apparently)

I've tried everything I know and googled this problem from every way I could imagine, I think it's that big that I've got posted in my earlier post there.

I doubt it will ever be fixed seeing as these Macbooks are too old to be developed for.  I suspect it's a issue with hardware compatibility.

But please post back here if you do find a way!!! I'll keep trying and post any updates here as well.

---

### Post by jwhendy on 2010-10-08
I'll give it a whirl this weekend if I get a chance. I can use an RCA cord on my TV, too. It's not that new! Definitely has a fat a** and is no flatscreen :)

I googled around and found references to being out of sync perhaps or perhaps at the wrong refresh rate. I'll try some things out and get back to you. I also would like this functionality as anytime I want to watch something on my TV with the computer I have to reboot into OS X. I spend almost all my time on Linux so that's annoying.

---

### Post by 31632531 on 2010-10-08
I've tried messing with the sync/refresh rate; if you want to mess with it xrandr is necissary.

I would suggest for ease of configuration grandr front-end after doing command-line stuff all night I needed a GUI to regain sanity.

It's so funny that I've got the exact same scenario, I use XMBC from my OSX which is only one of two reasons I even still have it installed (pro-tools being the other)

Anyhow I'm away for the weekend but I'll try some more next week.

---

### Post by Pimterry on 2010-10-09
I too am having this problem right now, and I'd be *very* interested in any solution people can come up with! I've been mucking about with xrandr for quite a bit now, just trying to force various things, and I'm not making much progress...

---

### Post by 31632531 on 2010-10-28
Excerpt from [Macbook 3.1 Ubuntu Install]("https://help.ubuntu.com/community/MacBook3-1/Intrepid") page.

> External Monitor
The external monitor works out of the box, you have to set it up via System > Preferences > Screen Resolution. In order to have desktop effects (Compiz) work correctly on the external monitor, the laptop monitor must be turned off. To do this, click on the field that says "laptop" in the display properties dialog.

If you don't need desktop effetcs, you can configure your external monitor to extend the desktop of your MacBook. Confirm to use a virtual screen resolution, when the configuration dialog asks about it.


There had been some issues with using a dualhead configuration on the MacBook. At the moment it is not guaranteed to work. Here are some hints, that can help you make it work anyway:

switch off desktop effects, if not done automatically
reduce the resolution of your external monitor
check in /etc/X11/xorg.conf, if the virtual resolution was detected correct. Example: The MacBook resolution is 1280x800; your external monitor resolution is 1680x1050. With the external monitor left or right of the MacBook, the virtual resolution would be 2960x1050. If you hook up an external monitor with a higher resolution than 1680x1050, e.g. 1920x1200, the menu item System > Preferences > Screen Resolution might not give you the option to choose the resolution 1920x1200 for your external monitor. You have to manually edit the /etc/X11/xorg.conf file and change the virtual resolution appropriately, e.g. horizontal: 1920 + 1280 = 3200; vertical: max(1200,800) = 1200. So the virtual resolution would be 3200x1200. Restarting the xserver will now give you the option to choose the higher resolution.

---

### Post by 31632531 on 2010-11-13
Any progress from anyone?

---

### Post by Deathhunt on 2011-05-01
I've been looking to fix this for a while... I want to make the switch from osx but My main use for this computer is a media center. If i can't get the TV out to work I'm stuck in mac land... it's getting boring here.

I'm on 11.04 and here is what happens when I plug in... My lap top screen goes black and resizes just like osx dose when i plug in the dvi. This is new. But the end results are the same scrolling black and white bars. just cant get it to sync up.

any ideas?

---

### Post by gordonbenjamin on 2011-07-17
Good people, I just created an account on Ubuntu simply to be able to respond to this very thread.  I too was having issues with Macbook dual monitor, while connected to a TV via RCA using mini-DVI adapter, appearing only in black and white with jittery lines and "fuzz" on the screen...also googled it and found no resolution.  After playing with various settings on my own, I've discovered a fix that worked for me and I hope it will work for you folks also.  When dual monitor is connected, open System Preferences > Displays...and on the setting controls located on the 2nd monitor you have a couple of drop-down menus on the right side of the window...the first one is titled "Refresh Rate."  Mine was set automatically to 50 Hertz (PAL)...clicked drop-down bar and noticed a second option, 60 Hertz (NTSC)...selected this refresh rate and bata-bing...color and correct display on the TV.  Very excited to have this working now, at first I thought it was a problem with the TV I was using, but when it happened on the 2nd TV I tried I knew it was my computer.  Now I'm watching movies in perfect picture.  Hope this works for y'all too.  Cheers!

---

### Post by jwhendy on 2011-07-18
**@gordonbenjamin**

What you describe sounds suspiciously like the method for setting the refresh rate in *Mac OS X* (System Preferences -> Displays), not Ubuntu or any Linux variant. Are you, indeed, describing the procedure you used to watch video from a Macbook via an external monitor while booted into the *Linux* operating system?

---

### Post by 31632531 on 2011-08-14
I agree with jwhendy.

Furthermore I have already tried using different refresh rates to no avail.  This of course was more of a futile excursion because the televisions in North America are set to use 60Hz if using an analogue single. This is by default based on the A/C power system we run under.  Interestingly enough this is why television in North America is delivered at 30 frames a second.  The basic technology of the refresh rate (60Hz) and the delievery of the frame rate (30 fps) which needs to be rendered on an interlaced screen (lines 1,3,5,.... are refreshed in one cycle then 2,4,6... in the next).

---

