---
title: "Trying to install ubuntu to ext HD--error"
date: 2011-01-31
forum: Apple Hardware Users
---

### Post by este.el.paz on 2011-01-31
Folks:

I'm an Apple GUI type person, rank newbie to the world of Linux and looking for something to carry my iBook and iMac G4's into the future whenever Tiger is no longer able to surf the web, etc.  I got an Ubuntu 10.10 .iso for PPC burned to DVD and got it to boot up in my iBook G4 with the intention of installing it on a partition in an ext HD.  But, when choosing the "Partition manually" approach rather than the "erase whole disk" method and then selecting the dev/sda when I click "install" I get an error window--"no root file system" . . . "no root file system is defined.  Please correct this from the partitioning menu."  Couldn't find the "partitioning menu."  Tried a couple of times.  I got the feeling that the install has to take place on the HD that the DVD is booted in . . . is that correct or should I pick the "erase whole disk" while the FW ext HD is turned on and then can I select the ext HD partition that I've set up for Ubuntu to run on and try to boot from with FW, etc?

I'm not ready to turn the laptop into a totally Ubuntu unit, running it in test mode showed a few problems, no wireless, and the program "GParted" crashed twice when I opened it; and the display doesn't show up in the iMac . . . it doesn't seem like it's ready for prime time in the PPC.  But, how can I find out if I can install the Ubun10 DVD on an ext HD or only on the internal HD?  I've seen many experienced computer guys on the main Apple forums saying they don't recommend partitioning the int HD, so I'm not ready to go that route as long as Tiger is still working just fine.  But, I'd like to play around with the Linux approach in the meantime to get experience with it, etc.  But, so far I'm stuck at the "no root file system defined" error.

Any suggestions?  I've also got a Lubuntu .iso burned to CD but that doesn't seem to boot in the iBook and again I don't want to partition the int HD to install anything there, but I'm looking to try that option as well.  Thanks.

e.e.p.

---

### Post by pindar on 2011-01-31
Booting from a mac without touching the internal disk (I assume that's what you want; less verbiage and more relevant information would have been nice) is a mythical beast. Some people say they have it working, but most seem to despair at one moment. I have never been able to make it work; what I have (on a mac mini intel) is a small "boot" partition on my internal HD; the linux installation proper is on an external HD. In your case, there are 2 factors which make everything more difficult:

[LIST=1]
[*]Your disk appears to be firewire, not usb. Firewire support in linux is not quite perfect (I found an external fw disk to be somewhat flaky under linux; worked perfectly under os x).
[*]You're using ppc, which has been abandoned by Apple for a number of years and is not officially supported under ubuntu any longer. It's now a community project. It is a wonderful effort, but there's not much development going on, only adaptation of the main code base, so your comment "it doesn't seem like it's ready for prime time in the PPC" is a bit off - I assume ppc will eventually just die when most older ppc machines have been retired.
[/LIST]

The main problem on ppc machines is the bootloader. It's called yaboot, it's a bit capricious, more difficult to configure than grub, and there's far less information readily available on the net. So if you're a linux noob, all of this may make it a bit difficult for you and you may have to rethink what you want to do in order to test ubuntu on your macs.

---

### Post by linuxopjemac on 2011-01-31
It should be possible:
[http://mac.linux.be/content/installing-ubuntu-910-karmic-external-fw-drive-mac-g4-ppc-0](http://mac.linux.be/content/installing-ubuntu-910-karmic-external-fw-drive-mac-g4-ppc-0)

---

### Post by este.el.paz on 2011-01-31
Gents:

Thanks kindly for the reply to both of you.  Pindar, what you have said seems to be what I've found so far in reading in a few forums in terms of the general non-support for ppc and in terms of hitting the wall on the "no root file" error; and, um, "less verbiage" . . . on a forum, OK . . . didn't exactly know how to frame the question . . . .

But, linuxopjemac . . . thanks for the link to what you went through to get it working; I also have been to your mintppc site and I've got the debian squeeze set up to try so I'll be along on that in awhile if I can figure out how to get it to ext HD.  

But, back to your post which was thorough, however, a bit different than the 10.10 procedure . . . no questions on the install, and then the main question I have for you is: do I want the "erase whole disk" button and then will the various partitions show up that I can choose so that the "whole disk" will be just for one of the smaller partitions?  Or, do I need the "manually partition" button to have the various HD's show up? in which case I'm back to the error window.  I'm just wondering if the "erase whole disk" choice is for the internal HD I'm booted in or if it will give me the list of attached HD's to pick from?

e.e.p.

---

### Post by este.el.paz on 2011-02-02
Folks:

Still hoping for a bit more detail in terms of the choice between "erase whole disk" button and the "partition manually" buttons in terms of trying to get Ubuntu 10.10 for ppc installed on an Ext HD without touching or effecting my int. HD??

Should this post be re-posted or re-labeled as "ppc" or would that make no difference in terms of if or when the question is engaged?

Thanks,

e.e.p.

---

