---
title: "HELP - Ubuntu 15.04 on Macbook Pro 12,1 (Early 2015 13&quot; Retina) - No grub menu"
date: 2015-04-15
forum: Apple Hardware Users
---

### Post by HXn on 2015-04-15
Hey all, thanks in advance for the help.

I installed Ubuntu 15.04 beta2 fine on a new Macbook Pro 12,1 following these instructions (they're both pretty much the same):

[https://help.ubuntu.com/community/MacBookPro11-1/Saucy](https://help.ubuntu.com/community/MacBookPro11-1/Saucy)
[http://www.makeuseof.com/tag/install-linux-macbook-pro/](http://www.makeuseof.com/tag/install-linux-macbook-pro/)

(The footnote [here]("http://ubuntuforums.org/showthread.php?t=2270831") is the reason for 15.04)

Ubuntu boots fine, but *I do not see a grub menu*, and so cannot boot back into OSX. I believe the OSX partitions are fine, as they weren't touched during Ubuntu install (other than installing grub onto /dev/sda1) and they appear fine in Disks.

I have tried both:

1. Changing the boot order in efibootmgr to 80,0 to no avail
2. Changing to GRUB_DEFAULT=4 in /etc/default/grub (see #8 under "Installation" [here]("https://help.ubuntu.com/community/MacBookPro11-1/Saucy")) to no avail.

At the very beginning of startup, I get a blank screen followed by a "Booting in insecure mode", then a purplish screen that has a small glitchy rectangle in the top left corner, then the Ubuntu splash screen / login.

Any help would be greatly appreciated, thank you!

*UPDATE: Looks like I can boot in OSX by holding down Alt on power up and selecting the Macintosh HD disk. The no grub menu still persists, but if this is how I have to use it, it's better than nothing.

---

### Post by Gabor_Hornyak on 2015-05-16
One of my colleagues had the same issue. The problem is that grub didn't detect OS X so he doesn't show the boot menu.
Check this post how to enforce the boot menu of grub: [http://askubuntu.com/questions/16042/how-to-get-to-the-grub-menu-at-boot-time](http://askubuntu.com/questions/16042/how-to-get-to-the-grub-menu-at-boot-time).

---

### Post by rican-linux on 2015-05-16
I am having the same issues. according to the **[Mactel install guide]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation")** you need to install rEFit so you partitions can sync. I did that and it did not work. rEFit did not load on reboot. If anyone has advice I would love to hear it.

---

### Post by raywang2 on 2015-06-02
Hi

The reason why you can not see the grub menu is because  you hide the menu

comment out the lines start with "GRUB_HIDDEN", and set the time out. and run "sudo update-grub" when you finish editing, then reboot. you will get the grub menu

---

