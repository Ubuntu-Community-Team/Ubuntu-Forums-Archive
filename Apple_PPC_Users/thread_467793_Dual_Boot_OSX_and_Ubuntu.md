---
title: "Dual Boot OSX and Ubuntu"
date: 2007-06-08
forum: Apple PPC Users
---

### Post by czechman86 on 2007-06-08
I have just recently partitioned my HD to allow for a 15 gig Ubuntu system. I have 65 for OSX and 15 for Ubuntu. I have successfully installed Ubuntu, but cannot boot into it. Instead, when I start my computer, I am greeted by a screen with a question mark, and then a finder face, from there, the regular OSX boot takes place. How can I make it, so that I have a choice of which OS I would like to boot into.
Thank You!

---

### Post by 3rdalbum on 2007-06-08
Try this for older Macs:

Boot into Open-Firmware by holding down "Command-Option-O-F" as you turn on the computer.

At the OF command-line, type: "boot hd:1,yaboot" and press Return.

If this gives you an error message, try incrementing the digit that's in the command.

If all goes well, you will be taken to a screen with white text on a black background. Pressing Return again should boot Ubuntu.

Once Ubuntu is booted, you can type "sudo ybin" into the terminal and hopefully that will properly install the bootloader.

----------
For newer Macs, you can try holding down the Option key on startup, and choosing the Linux penguin logo when given the option.

---

### Post by jrlohr on 2007-06-08
from OSX run these two commands and post the results

sudo pdisk -l

nvram boot-device

---

### Post by czechman86 on 2007-06-09
I discovered what the problem was, and that is that i installed ubuntu wrong. i need to find a guide on how to partition the system correctly without OSX getting to out of hand.

---

