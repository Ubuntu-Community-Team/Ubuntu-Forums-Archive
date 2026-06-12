---
title: "Ubuntu 9.04 on MacBook2,1?"
date: 2009-04-25
forum: Apple Hardware Users
---

### Post by Allen McBride on 2009-04-25
I've never used Ubuntu, but I'd like to try installing it on an external drive.  From [this support table]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages#Mactel%20Wiki%20Support%20Matrix"), it looks like Jaunty does not run on MacBook2,1.  Is this something that's likely to change before 9.10 is released?  I'm trying to decide whether to install 8.10 or wait until 9.04 will work on my machine.  Thanks!  --Allen

---

### Post by StooJ on 2009-04-25
The support table hasn't been updated yet (I should really make the appropriate page) but 9.04 works well on my Macbook 2,1.

I haven't fully tested everything (iSight, Microphone etc) because I don't really use them, but wireless, compiz, extra function keys work out of the box. Suspend works for me as well, but hibernate doesn't.

If you are installing Ubuntu on the external drive, remember to install grub on the same external partition as you install the root. (info is on the wiki)

---

### Post by genosupremo on 2009-04-25
Well hello there ubuntu world. I installed ubuntu on my 2.1, which happened to be* the day jaunty came ou*t, knowing almost nothing about what I was doing. I was hoping that some of the bugginess (really erratic brightness, really low sound, trackpad & r-click probs, battery nommage, airport and bluetooth always on..) was because it wasn't ready for 2.1... I mean, I know they're jsut things to fix, but... 

That said, it *works.* Its just not smooth...

Is there a "collation of 2.1/Macbook jaunt bugs" thread? I've yet to find one...

---

### Post by cyberdork33 on 2009-04-25
> **genosupremo said:**
>  Is there a "collation of 2.1/Macbook jaunt bugs" thread? I've yet to find one...Not that I know of, but that would be the idea behind the wiki page they were referring to above... Someone should really start a page for Jaunty.... 


Installing and booting from an external is not straightforward. Most people cannot accomplish this without booting via EFI.  See:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

---

### Post by genosupremo on 2009-04-26
> Someone should really start a page for Jaunty.... 
- Meaning... us? I have no idea how to go about that...

---

### Post by Allen McBride on 2009-04-26
Thanks for the advice and for the warning about grub.  I found bits and pieces about this on the wiki pages, though if you have a specific link I'd appreciate it.  I'm a little confused by the different variants of grub, and by the question of whether Ubuntu installs it for me or whether I'm supposed to install it myself first.  --Allen

---

### Post by bruyninc on 2009-04-27
I have done the upgrade from 8.10 to 9.04 on a Macbook2.1 this weekend. The only real problem I had was with the Xserver: it worked, but slooooowly.... Until I added the following Option to /etc/X11/xorg.conf

Section "Device"
  Identifier    "Configured Video Device"
  Option "AccelMethod" "UXA"
EndSection

Herman

---

### Post by cyberdork33 on 2009-04-27
> **genosupremo said:**
> - Meaning... us? I have no idea how to go about that...Yes. the whole point of a wiki is to get everyone involved maintaining it. you can go to the Intrepid page, and there is an option to create a duplicate in the menu. Do that, then you can start editting away! There are even guidelines for the Mactel Docs:
[https://wiki.ubuntu.com/MactelSupportTeam/DocGuidlines](https://wiki.ubuntu.com/MactelSupportTeam/DocGuidlines)

> **Allen McBride said:**
> Thanks for the advice and for the warning about grub.  I found bits and pieces about this on the wiki pages, though if you have a specific link I'd appreciate it.  I'm a little confused by the different variants of grub, and by the question of whether Ubuntu installs it for me or whether I'm supposed to install it myself first.  --Allen
Ubuntu comes with grub, but for booting from an external, you likely will have to boot with grub-efi. grub-efi is the efi variant of grub2 which is still in heavy development. You'll have to go through the page I linked to for the various details.

---

### Post by bazmonkey on 2009-04-27
> **genosupremo said:**
> Well hello there ubuntu world. I installed ubuntu on my 2.1, which happened to be* the day jaunty came out*, knowing almost nothing about what I was doing.

Hah!  I did the exact same thing (same MacBook, too!)... except I knew what I was doing.  I've used Linux for years on and off, felt like checking out what Ubuntu was up to, had just finished installing Intrepid 32-bit, realized I have a 64-bit CPU, and went to download the 64-bit ISO when I saw the Jaunty links weren't RC anymore.

> That said, it *works.* Its just not smooth...

This is butt-loads better than I've ever seen any distro manage to auto-configure a laptop (and an odd one like a Mac at that).  Seriously.  

Even the "bumps" aren't a big deal.  Problem: Caps Lock key doesn't light up and the Eject button doesn't work.  Solution:  sudo apt-get install pommed.  The buttons worked as-advertised the moment apt-get finished.  That's still pretty smooth as far as problems go: a not-default package.

I don't want to sound all "back in my day..." about it, but looking back at what it used to take to get a Linux box to work, and considering how many of these things would require separate configuration if installed from scratch in another OS, we got it good :-)

Has anyone managed to do anything about the brightness being all crazy?  The buttons worked out of the box, but it just goes randomly up and down and off.

EDIT!!!  Try out "xrandr --output LVDS --set BACKLIGHT_CONTROL combination".  I'm sure there's an appropriate place to put it, but I have it as as GNOME startup program until I find a better way.  

The touchpad two-finger scrolling and 2/3-finger clicking works fine after being set in the preferences.  I installed the latest snapshot of the madwifi drivers for the Airport, but they turned out to work about the same as ath9k, the out-of-box option.

Over the last week I've found wicd seems to connect more reliably for some reason.  Network-manager, for me, drops WEP networks.

The 64-bit flash plugin works nicely; on-screen notifications (like volume adjustment, annoyingly enough) do kick you out of fullscreen.

The low sound is a matter of an adjustment in alsamixer.  Same for the mic and line-out.

I haven't tried iSight or the remote yet, or even looked in to it.

Are y'all using the 32 or 64 bit versions?  I haven't found a single issue with the 64-bit version.  I haven't used Ubuntu or Linux since Edgy, so Jaunty is just plain impressive to me.

---

### Post by genosupremo on 2009-04-28
> Yes...Do that, then you can start editting away!
- Thanks for the pointers! I'm about to drop into my finals though, so it'll end of June before I can contribute time to that. See everyone else there though?...

@ bazmonley
- Nice to see I got lucky =J 

On the brightness front: Transistor 23 over at [this]("http://ubuntuforums.org/showthread.php?t=1137574") piece linked this [informative (?) piece]("https://bugs.launchpad.net/ubuntu/+s...el/+bug/367309") on brightness and the idiosyncrasies therein...

---

