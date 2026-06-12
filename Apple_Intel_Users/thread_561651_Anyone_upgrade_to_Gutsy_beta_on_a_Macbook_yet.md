---
title: "Anyone upgrade to Gutsy beta on a Macbook yet?"
date: 2007-09-27
forum: Apple Intel Users
---

### Post by dmber on 2007-09-27
Any stories?  Successes?  Failures?

Thanks.  I'm pretty happy with what I've got going with Feisty on my Macbook 1.83 core duo at this point, so I'm nervous to upgrade.

---

### Post by cyberdork33 on 2007-09-27
> **dmber said:**
> Any stories?  Successes?  Failures?
Thanks.  I'm pretty happy with what I've got going with Feisty on my Macbook 1.83 core duo at this point, so I'm nervous to upgrade.

I have been running Gutsy on my iMac for awhile now, and it is pretty stable. I think that there may be an issue with wifi still on the Macbook, but I don't have one to test.

---

### Post by A_Lyle on 2007-10-01
Not upgrade exactly - I just installed Gutsy beta on my Macbook in order to play with UME (BTW I installed Kubuntu since I'm used to using KDE at work).

Issues so far:

* Screen is currently the standard 4:3 aspect ratio - not sure where I need to configure the driver to get widescreen support

* No wireless - had to plug in ethernet to download the UME stuff I wanted :(

* Touchpad is hypersensitive, and tapping some keys causes cursor "bounce"

I only installed it yesterday, though, so I probably just need to work on the setup a bit more...

---

### Post by Zelut on 2007-10-01
I've been running Gutsy since Tribe 2 in full production.  No show stoppers, all is well.  There are a few nice hardware based improvements for the macbook in Ubuntu 7.10.  I am now running the beta release.

---

### Post by oneoverzero on 2007-10-01
There is a minor issue with the wifi...  I can get mine working, I just have to open up the term and manually select the device, and network every time.  Other than that it's pretty good.

---

### Post by ivesjd on 2007-10-12
Installed Gusty RC today on a first gen macbook. So far everything works. The only thing is that scroll goes back and forward pages in firefox.

---

### Post by wdo_will on 2007-10-12
I'm running Gutsy on a Santa Rosa MacBook Pro... no real problems, except, when I first installed it, all of my hardware worked perfectly, and then some of it stopped working (sound and wifi I believe) after I did a major update via apt.  I need to re-install them this weekend.

---

### Post by dmber on 2007-10-12
that's a firefox thing.

about:config something or other.

it's in the Macbook wiki.

---

### Post by Loki1989 on 2007-10-13
I go talmost every thing installed within an hour or two of connected directically to the internet and searching around the net and now I have a post out for wireless and blue tooth.

[http://ubuntuforums.org/showthread.php?p=3524556#post3524556](http://ubuntuforums.org/showthread.php?p=3524556#post3524556)

---

### Post by mustang on 2007-10-13
How is the battery life?

---

### Post by vh1 on 2007-10-14
I am very impressed here. I just popped in the gutsy RC CD and and the install didn't have any problems on my macbook (except for wifi, and in turn the installer alerting you that it wouldn't be selecting security updates due to no internet connection)

even when you unplug the power supply and the screen dims, it has does a fancy fade through the various brightness steps. but doesn't turn the display off when you turn the brightness down all the way

battery applet reports ~2:30 remaining without anything done to a base install

---

### Post by mustang on 2007-10-14
> **vh1 said:**
> battery applet reports ~2:30 remaining without anything done to a base install

That's still really disappointing. :( I would exchange all other improvements for OSX equivalent battery life.

Oh well. Thanks for reporting your observations.

---

### Post by quannum on 2007-10-15
> **oneoverzero said:**
> There is a minor issue with the wifi...  I can get mine working, I just have to open up the term and manually select the device, and network every time.  Other than that it's pretty good.

I don't have wifi on my MBP with 11n atheros card. Where's a good place to start for info on getting it working?

UPDATE: I followed the instructions... that was easy!

---

### Post by tetonedge on 2007-10-15
anybody have external monitor working with gusty on MBP and fglrx? All i get is a black screen on both. I also still haven't gotten suspend to work using gusy either.

---

### Post by dark_harmonics on 2007-10-15
i have dual XGL sessions and compiz running with my MBP. You might want to start with the aticonfig command. Try aticonfig --help.

Run dual sessions you just use the dual display commands: like this

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak
sudo aticonfig --initial=dual-head --screen-layout=rightof      [ you can subsititue leftof above or below as per your preference ]

Head over to this post for the startxgl.sh script to start two xgl sessions (gusty does say it runs XGL by default but it doesnt start two sessions):  [http://ubuntuforums.org/showthread.php?t=378281](http://ubuntuforums.org/showthread.php?t=378281)
Log out and in and you have dual xgl sessions which means two cubes! The bad thing is that they are actually two seperate desktops as far as your computer is concerned so you cant move things from one to the other.

For that you need big desktop. I dont like that but alot of people do and so they should check this post for that:

[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

And yes all this still applies to gusty. It works well on my testing MBP.

---

### Post by dmber on 2007-10-15
so...i'm thinking i'm just going to wait until i know for sure that my wireless will work like it does in Feisty.  is that a stupid thing to do?  if it works out of the box for me in Feisty, will i have a lot of trouble getting it to work in Gutsy?

---

### Post by cyberdork33 on 2007-10-15
> **dmber said:**
> so...i'm thinking i'm just going to wait until i know for sure that my wireless will work like it does in Feisty.  is that a stupid thing to do?  if it works out of the box for me in Feisty, will i have a lot of trouble getting it to work in Gutsy?
Shouldn't... and if you do, then that is a major bug.

---

### Post by quannum on 2007-10-16
> **dmber said:**
> so...i'm thinking i'm just going to wait until i know for sure that my wireless will work like it does in Feisty.  is that a stupid thing to do?  if it works out of the box for me in Feisty, will i have a lot of trouble getting it to work in Gutsy?

I have an MBP with the 11n adaptor and although it didn't work out of the box, it was trivial getting it to work - download madwifi, make, make install. FWIW Gutsy is an awesome upgrade.

---

### Post by cyberdork33 on 2007-10-16
> **quannum said:**
> I have an MBP with the 11n adaptor and although it didn't work out of the box, it was trivial getting it to work - download madwifi, make, make install. FWIW Gutsy is an awesome upgrade.He is on one of the Macbooks that had Wi-Fi working out of the box on feisty though. None of the Macbook Pros did that.

---

### Post by tetonedge on 2007-10-17
thanks dark_harmonics i will try that, I was wondering if on your mpb you were using a the dvi - vga adapter, as it seems i can do this with straight dvi, but when i use a vga monitor, both screens are black and never come up. Thanks

Also anybody have suspend yet?

---

### Post by dmber on 2007-10-18
ok, the Gutsy Live CD recognized my wireless.

will my X.org file (with my changes to my trackpad and whatnot) survive the upgrade?

---

### Post by cyberdork33 on 2007-10-19
> **dmber said:**
> ok, the Gutsy Live CD recognized my wireless.

will my X.org file (with my changes to my trackpad and whatnot) survive the upgrade?
I would make a copy of the synaptic options and save them to a thumbdrive or something. Then you can add them back to the new xorg.conf if needed.

---

### Post by dmber on 2007-10-19
i got your message too late.  they all survived the upgrade, though.

---

### Post by dark_harmonics on 2007-10-19
> **tetonedge said:**
> thanks dark_harmonics i will try that, I was wondering if on your mpb you were using a the dvi - vga adapter, as it seems i can do this with straight dvi, but when i use a vga monitor, both screens are black and never come up. Thanks

Also anybody have suspend yet?

I use the straight DVI. I'm sorry i dont have any experience with the vga output on the MBP... Hope what i linked you to helps though...

---

