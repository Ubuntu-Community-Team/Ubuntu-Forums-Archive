---
title: "NUT and Belkin F6C550-AVR UPS"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by Silverfox on 2007-09-28
Seems I'm not the only one having this problem. My exact situation is described here:

[http://ubuntuforums.org/showthread.php?t=128648](http://ubuntuforums.org/showthread.php?t=128648)

Although that thread is 18 months old, it hasn't been answered or updated so I have no idea if he found a solution. So I thought I'd try over here. The problem seems to be defining PORT=/dev/usb??????. I don't know near enough about how to define access to a USB port, can someone point me in the right direction?

Ubuntu 6.06.1 LTS AMD64 LAMP server install (no desktop), NUT 2.03 (although the latest stable release on the NUT pages seems to be 2.2.0) as well as the NUT-USB and NUT-DEV packages.


lsusb reveals the following:

```

$ lsusb -t
Bus#  2
`-Dev#   1 Vendor 0x0000 Product 0x0000
Bus#  1
`-Dev#   1 Vendor 0x0000 Product 0x0000
  `-Dev#   4 Vendor 0x050d Product 0x0551
$ lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 050d:0551 Belkin Components
Bus 001 Device 001: ID 0000:0000

```

So the hardware seems to be alive. None of the man pages for ups.conf, upsdrvctrl, nutupsdrv or newhidups give an example of what the port information should look like (although the ups.conf man does state the a value for PORT is "Required", the only examle they give is of a serial connection)

My hardware is listed on the Network UPS Tool site as supported by usbhid-ups, but when I use that with the DRIVER= option in ups.conf I get a "file not found" error. I used Aptitude to install both NUT and the NUT-UPS packages.

I've been beating my head against this problem for the better part of 12 hours, I went to be last night hoping for some divine inspiration this morning, but I can't think of anything else to try. I'm about to give up and just leave it using the UPS in "stoopid" mode, unless one of you fine folks can help me discover what I tripped over, I feel like I've fallen, and I can't get up.:lolflag:

Thanks in advance for any help you can send my way.

---

### Post by SpiritIsReality on 2007-09-28
howdy
first thing, I don't know how to do this. that said...
in advanced search, keywords nut ups, search titles only, last 6 months, found
[http://ubuntuforums.org/showthread.php?t=514891&highlight=nut+ups](http://ubuntuforums.org/showthread.php?t=514891&highlight=nut+ups)
Fraoch might be able to help you.  maybe post at that thread?
trails

---

### Post by Silverfox on 2007-09-28
Thanks for the reply fmat, I had read that thread, the link he posted to "monkeyblog" is dead. I have no idea how to "install from source", which it would seem I need to be able to do to install the latest version of NUT. I'll pm Fraoch and see if he can give me some direction. I'm hesitant to attempt installing anything from source (never done it, intimidated as hell), but I guess this project is as good as any for learning how that works, eh?
:popcorn:
I'll make some popcorn and give it a whirl, when I have a day I can devote to it. Thanks again.

---

### Post by SpiritIsReality on 2007-09-28
ya, I haven't done much of installing from source.
just a couple of insignificant ones to get an idea of how it goes.
long since left behind in the dust of reinstalls.

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

[https://help.ubuntu.com/7.04/add-applications/C/install-file.html](https://help.ubuntu.com/7.04/add-applications/C/install-file.html)
4,5 and 9 here
[http://ubuntuforums.org/showthread.php?t=232059](http://ubuntuforums.org/showthread.php?t=232059)
[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)
item 12 in the opening post here. 
[http://ubuntuforums.org/showthread.php?t=142716](http://ubuntuforums.org/showthread.php?t=142716)

[http://www.google.ca/search?hl=en&q=linux+ubuntu+%22installing+packages+from+source%22&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=linux+ubuntu+%22installing+packages+from+source%22&btnG=Search&meta=)
[http://www.google.ca/search?hl=en&q=site%3Aubuntu.com+%22compiling+software%22&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntu.com+%22compiling+software%22&btnG=Search&meta=)
[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+%22compiling+software%22&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+%22compiling+software%22&btnG=Search&meta=)

you could check out Free Linux Books Online 
[http://ubuntuforums.org/showthread.php?t=484846](http://ubuntuforums.org/showthread.php?t=484846)
trails

---

