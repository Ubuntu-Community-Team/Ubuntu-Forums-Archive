---
title: "Power Macintosh G3 (beige desktop)"
date: 2007-01-29
forum: Apple PPC Users
---

### Post by Jakevn on 2007-01-29
Hello. I recently acquired 10 Power Mac G3 (beige desktops) with the following specs: 300mhz, 64mb RAM, 3gig HD. (Just a rough estimate.)  

 I want to install Linux and run a server from it. (Server only takes 12-24mb RAM)

The servers will be for an MMORPG and each G3 will host an individual zone. It's for internal testing only and I don't need it to handle any more than 3 clients per machine. 

 These machines have no OS installed and when they are booted it will simply show a white floppy disk with a question mark in the middle of it. I have never worked with these machines before so I'm not sure how to get it to boot to CD. I burned Ubuntu 6.06 server using DiskUtility on my iMac but it will not boot to CD. I tried holding down C, and also tried CMD-Option-Shift-Delete with no luck. 

Any help would be much appreciated. Thank you. :)



Forgot to add, are there any lightweight shells out there that would run on these machines?

---

### Post by 3rdalbum on 2007-01-29
On the beige Macintoshes, the Open Firmware won't boot Linux directly. You could try getting Mac OS 8 and installing that, so you can run BootX (the Mac program that can boot Linux). Or use another Mac to put Miboot (included with BootX) onto a floppy.

---

