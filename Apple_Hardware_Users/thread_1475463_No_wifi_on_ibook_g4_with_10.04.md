---
title: "No wifi on ibook g4 with 10.04"
date: 2010-05-06
forum: Apple Hardware Users
---

### Post by New Horizon on 2010-05-06
I thought it would be great to update to the latest version of ppc ubuntu on my old ibook g4, so i did just that.  Everything seemed to install correctly, and the broadcom driver was properly detected and downloaded...however...when I connect to my wireless network, I can't get any data flow.  No web pages, no connection to empathy...nothing.  Everything worked so flawlessly in 9.10, and I had just been using the wireless connection before I installed 10.04, so I know the hardware is fine.  

Any thoughts on this folks?

I'm tempted to go back to 9.10 after this experience...

---

### Post by linuxopjemac on 2010-05-07
I heard other people complain about the same issue...
[http://ubuntuforums.org/showthread.php?t=1472613](http://ubuntuforums.org/showthread.php?t=1472613)

I would file a bug report..

The thing that notice is that both the ibook G3 with a classic Airport (orinoco module) and iBook G4 (Broadcom chipset, b43 module) have the problem. It looks like it has nothing to do with the module itself...I don't believe in so much coincidence. I think it has to do with WPA or something. Can you try to connect to a WEP encrypted network, or a completely open network ? Then we know where the problem resides...

---

### Post by BrendanOD on 2010-05-09
I got it working on my ibook g4 with an airport extreme card.

In synaptic software manager add b43-fwcutter.

When it installs allow it to download the right firmware.

The details about the firmware are here:

[http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware)

That's it!

Ain't Linux Great!!!

---

### Post by derciojr on 2010-07-04
Good morning.

Which ibook G4 do you have? I have a G4 800, early 2004. I've used Kubuntu 7.04, no problems. Now, when I try install 10.04, it can't format HD. With 8.04 is the same problem. The HD is fine (both 7.04 and original OSX can format it easyly). I tryed format with 7.04 before install 10.04 with no results. I think the problem is with the s.m.a.r.t. instructions that HD don't support, but I can't disable them in the installer.
Can you help me?

Thanks in advance.

---

