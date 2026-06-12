---
title: "How to switch OS on dual-boot Mac?"
date: 2006-12-14
forum: Apple PPC Users
---

### Post by handylinux on 2006-12-14
I've just recently begun to experiment with Ubuntu 6.10, which I've installed on an iBook G4 along with OS X. One thing I've been wondering is if there's a quick, convenient way to switch between OS X and Ubuntu. 

If I just start up the iBook (or restart from Ubuntu), it starts into OS X, which is what is set in its firmware. But to switch from OS X to Ubuntu is a hassle, since OS X doesn't recognize the Ubuntu partition as a bootable System, so it can't be set in the Startup Disk preference pane.

So to start in Ubuntu I've been pressing the option key during startup, which presents a list of possible startup volumes, from which I can select the Ubuntu partition and then click the Continue button. This works, but is rather tedious; the computer takes a while to be sure of the list (even if there're only two possibilities), and then I have to maneuver the cursor (which at this point is rather unwieldy, just like it is in Ubuntu) to the button and click, then wait some more for Ubuntu to start up.

I just tried another method, which is easier and worked fine, that many Ubuntu users might not know about, so I thought I'd share. There's a little-known startup keyboard shortcut, apparently not officially documented (I couldn't find it just now on the [Apple support site]("http://docs.info.apple.com/article.html?artnum=75459")) but mentioned in third-party books: If you press the D key during startup, the computer is forced to start from the first partition on the hard drive. I've used this as a quick way to start up in Mac OS 9 on a Mac where I have 9 and X installed on separate partitions -- with 9 on the *first* partition, so this will work. It's quick, and also has the advantage that I don't have to go to the Startup Disk control panel in OS 9 to restart to OS X, since no firmware change has been made.

In setting up this iBook, following advice I saw somewhere I installed Ubuntu in the first partition (presumably something to do with the yaboot utility?). So I tried pressing D when I booted the iBook just now, and presto! it started in Ubuntu right away, with no tedious wait. So it's now this simple: Press D when I want to start in Ubuntu, press nothing when I want to start in OS X.

I don't know if this shortcut will also work on the new Intel Macs (some of the startup shortcuts have been changed), but it'd certainly be worth a try. It does depend, of course, on Ubuntu being installed in the *first* partition.

If anyone has any further information to add to this subject, I'd be very interested.

---

### Post by linear on 2006-12-14
From what you described, you don't get a yaboot menu. Did you ever get one?

Read [this]("https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot"), especially the section at the bottom ("You lost the yaboot menu!").

---

### Post by Tipo on 2006-12-14
Yeah, when dual booting, Ubuntu usually installs yaboot. Check out the link that **linear** left.

---

### Post by handylinux on 2006-12-15
> **linear said:**
> From what you described, you don't get a yaboot menu. Did you ever get one?

Read [this]("https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot"), especially the section at the bottom ("You lost the yaboot menu!").

Hmm. Well, I know little about all this as yet, but so far as I can tell, I've always seen the "yaboot menu" (v.1.3.13) during Ubuntu startup. I've tried working with it once or twice, just to see where the commands lead, but haven't learned much.

I also see, after two screens of yaboot text, two lines of white type on a black screen:

> [   30.275229] PCI: Cannot allocate resource region 0 of device 0001:10:18:0
[   30.275253] PCI: Cannot allocate resource region 0 of device 0001:10:19:0

Then the computer proceeds into starting Ubuntu. This has been the process on the two Macs where I've installed Ubuntu, an iBook G4 and an iBook G3.

After experimentation, I've determined the following:

1) My "tip" will be useful only for those like me who work primarily in OS X but want to start into Ubuntu now and then. With OS X selected in Startup Disk, you can use the D key during startup to boot into Ubuntu -- IF Ubuntu is installed on the first partition -- then restart back into OS X without the D key. As noted in my initial post, this is a lot more convenient than using the option-key startup method (#3 below) to select an OS. This was the point of my post: to alert Ubuntu/Mac users about this D key trick, which as I said is not well-documented.

2) If the firmware setting for OS X is erased by resetting the PRAM, the computer will simply boot into the first partition. This is useful if you work primarily in Ubuntu, AND Ubuntu was installed in the first partition; then if you want to use OS X occasionally, simply press x in the yaboot menu. Then when you restart from OS X, you'll return to the yaboot menu, which boots automatically into Ubuntu. If while in OS X you set OS X in the Startup Disk preference pane, return to #1 above.

3) Another way to switch from one OS to the other, without setting anything in firmware, is to press the option key during startup. The document linked above is a little confused about what happens then, but on my iBook both OS X and Linux (penguin icon) appear when I do this. (I gather the Linux partition might not appear on older Macs; I don't have one set up at the moment to try.) However I can see no reason to do this if you understand #s 1 & 2 above.

4) If OS X is installed on the first partition and Ubuntu on the second, the D key trick in #1 won't work to get you into Ubuntu; you'll have to use the option key method -- assuming the Linux partition shows up. So far as I can figure out, there's no way to set the computer to boot into Ubuntu automatically if OS X is on the first partition.

I tried working with the instructions in the linked document to see if yaboot could be configured to bypass the various text screens and go directly to the Ubuntu startup screen, but couldn't figure out if that was possible. Is it? If that is possible, then of course the only way to get back to OS X would be the option key startup method.

(While experimenting with "Setting which OS yaboot automatically loads" I found that if I press ctrl-alt[option]-F1 to get a terminal screen, the two mystery error lines above appear again at the top of it. They do not appear, however, if I open a Terminal window in the regular Ubuntu GUI. ??)

---

### Post by linear on 2006-12-16
> **handylinux said:**
> 1) My "tip" will be useful only for those like me who work primarily in OS X but want to start into Ubuntu now and then. With OS X selected in Startup Disk, you can use the D key during startup to boot into Ubuntu -- IF Ubuntu is installed on the first partition -- then restart back into OS X without the D key. As noted in my initial post, this is a lot more convenient than using the option-key startup method (#3 below) to select an OS. This was the point of my post: to alert Ubuntu/Mac users about this D key trick, which as I said is not well-documented.

2) If the firmware setting for OS X is erased by resetting the PRAM, the computer will simply boot into the first partition. This is useful if you work primarily in Ubuntu, AND Ubuntu was installed in the first partition; then if you want to use OS X occasionally, simply press x in the yaboot menu. Then when you restart from OS X, you'll return to the yaboot menu, which boots automatically into Ubuntu. If while in OS X you set OS X in the Startup Disk preference pane, return to #1 above.

If this method works for you and you're happy with it, that's fine, but I don't see the advantage over setting OS X as the default in yaboot.conf and pressing "l" at the yaboot menu when you want Ubuntu.

---

### Post by handylinux on 2006-12-17
> **linear said:**
> If this method works for you and you're happy with it, that's fine, but I don't see the advantage over setting OS X as the default in yaboot.conf and pressing "l" at the yaboot menu when you want Ubuntu.

Simpler and quicker:

1) "Setting OS X as the default in yaboot" requires a bunch of command-line shenanigans, unnecessary with my method. As a Mac user, I'll do that stuff if I have to, but would rather not.

2) Haven't done it myself, but I gather that if one has set OS X as the default in yaboot, each OS X startup will be preceded by the yaboot menu screens? Why bother? Just set OS X as startup in OS X Startup Disk, and boot directly into OS X like a regular Mac.

3) To boot in Ubuntu, simply press D during startup, yaboot menus will appear, and Linux will start up automatically, no need to press "l" or do anything else.

4) To return to OS X, just restart, no need to do anything else, no yaboot menus, the computer just starts in OS X like a regular Mac.

Again, all this requires is that Linux be installed on the first partition -- which I gather yaboot requires anyway (otherwise the only way to get to Linux would be the tedious option-key startup).

---

### Post by calum on 2006-12-23
> **handylinux said:**
> I just tried another method, which is easier and worked fine, that many Ubuntu users might not know about, so I thought I'd share. There's a little-known startup keyboard shortcut, apparently not officially documented (I couldn't find it just now on the [Apple support site]("http://docs.info.apple.com/article.html?artnum=75459")) but mentioned in third-party books: If you press the D key during startup, the computer is forced to start from the first partition on the hard drive. I've used this as a quick way to start up in Mac OS 9 on a Mac where I have 9 and X installed on separate partitions -- with 9 on the *first* partition, so this will work. It's quick, and also has the advantage that I don't have to go to the Startup Disk control panel in OS 9 to restart to OS X, since no firmware change has been made.

Note that the 'D' shortcut is really intended to boot a Mac into diagnostic test mode (if the install DVD is present), so I don't know how coincidental it is that this also works for booting Ubuntu.  It certainly may not work for everyone, depending on their particular installation.

---

### Post by handylinux on 2006-12-23
> **calum said:**
> Note that the 'D' shortcut is really intended to boot a Mac into diagnostic test mode (if the install DVD is present), so I don't know how coincidental it is that this also works for booting Ubuntu.  It certainly may not work for everyone, depending on their particular installation.

Ah, not exactly. It will work for everyone using Ubuntu on a recent (New World ROM) **PowerPC** Mac. It may not work on an Old World ROM PPC Mac, but my impression is they can't boot directly into Linux anyway? This forum is for PPC Mac Ubuntu users, so that's who I was addressing here.

Anyway, pressing D during startup to access the Apple Hardware Test is **only for Intel Macs**; on PPC Macs you must press the option key during startup, which will give a screen where you can select your startup System, one of which (if the appropriate Install CD/DVD or Apple Hardware Test CD is inserted) will be the Apple Hardware Test.

As I wrote in the initial post: "I don't know if this shortcut will also work on the new Intel Macs (some of the startup shortcuts have been changed), but it'd certainly be worth a try."

I've since located the Apple article on [Startup key combinations for Intel-based Macs]("http://docs.info.apple.com/article.html?artnum=303124"), where indeed "Press D during startup" is listed as "Start up in Apple Hardware Test (AHT), if the Install DVD 1 is in the computer." Which is what I thought I remembered.

Whether pressing D will force startup from the first partition on an Intel Mac I don't know, as I don't have an Intel Mac to experiment with. In any case, I gather that installing/using Ubuntu/Linux on Intel Macs is a whole other affair -- with its own set of problems and solutions -- than using it on PPC Macs.

---

