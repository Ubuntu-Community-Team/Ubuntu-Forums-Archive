---
title: "G3 ubuntu ppc install"
date: 2008-05-28
forum: Apple Hardware Users
---

### Post by shillizzle on 2008-05-28
im trying to install the ubuntu-ppc version on this G3 imac (slot-loading, w/ firewire). I can get the instal disk to boot (hold-c at boot) I know that it wont install because of monitor settings so i type "live-nosplash" and it takes me to a built-in shell.  im looking at a prompt that says..
(initramfs)_ 

the list of commands from the help command dont give me any option for install or to boot the live desktop screen. 

Im not sure how else to explain this.. I have read some tutorials but they dont cover this, they all just seem to work for ppl.
Thanks for any advise to a new imac user.
:)

---

### Post by stream303 on 2008-05-28
Be sure to see these two important faqs:

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)
and
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

They are especially important if you are installing Gutsy 7.10 - especially if you are running into the busybox / initramfs issue.  Which version are you trying to install?

How much ram is in your machine?
How large is the hard drive?  Is it original, or a replacement?  Does it currently run the older Mac-OS?

You may want to narrow down your specs as seen here:
[http://www.everymac.com/systems/apple/imac/index-imac.html](http://www.everymac.com/systems/apple/imac/index-imac.html)

Give these a shot, and this will help you narrow down your search and help us help you get up and running...

---

### Post by nitrous9200 on 2008-05-29
If your mac has a VGA port you can plug in an external LCD and complete the setup normally then look [here]("http://ubuntuforums.org/showthread.php?t=405934") to edit the proper files. Then the built in monitor will work.

---

