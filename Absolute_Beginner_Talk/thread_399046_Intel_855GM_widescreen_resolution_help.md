---
title: "Intel 855GM widescreen resolution help"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by 55kjsmith on 2007-04-01
Newbie here. Just installed Edgy Eft on a Sony VGN-T270P laptop. Only problem is with video resolution. Native res is 1280x768, but the highest res available is 1024x768. After some research I found out that a program called 915resolution might help. Here is the output

Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 855GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $29f
Mode Table Entries: 39

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel
Mode 7c : 1280x768, 8 bits/pixel
Mode 7d : 1280x768, 16 bits/pixel
Mode 7e : 1280x768, 32 bits/pixel



How do I get mode 7e?

---

### Post by ramjet_1953 on 2007-04-02
Try this link, that I submitted some time ago:

[http://www.ubuntuforums.org/showthread.php?t=351647&highlight=915resolution+painless](http://www.ubuntuforums.org/showthread.php?t=351647&highlight=915resolution+painless)

I have found on several occasions that choosing a 32 bit colour depth doesn't work.
I would initiall try patching MODE 30 to 1280 X 768 with 24 bit depth. ie:

code:
[COLOR="Red"]sudo 915resolution  30 1280 768 24[/COLOR]

Don't forget to also modify your /etc/default/915resolution file to comply with the above.

Just follow the how-to and see how you go.

Regards,
Roger :cool:

---

### Post by 55kjsmith on 2007-04-02
Not sure what I did, but video is now working. I just rebooted and it came back up. Thanks for the help.

---

