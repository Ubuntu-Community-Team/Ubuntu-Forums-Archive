---
title: "Making a bootable USB stick"
date: 2009-11-28
forum: Apple Hardware Users
---

### Post by tarat on 2009-11-28
I don't have any CDs laying around and am too lazy to go buy some, so I thought I'd try using my USB key to install Linux on my laptop. I'm using these instructions: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I've gotten to step 7 no problem, but since then it has been well over two hours and terminal is still giving me a continuous stream of gibberish, mostly question marks. Is there anyone else here who has successfully moved the iso to the USB who can tell me how long it takes?

---

### Post by linuxopjemac on 2009-11-29
Booting from USB is not supported by Apple. It's very hard. Maybe it's possible if you partition if you follow the folloing link:

[http://rentzsch.com/tidbits/intelbasedMacBootIncompatibility](http://rentzsch.com/tidbits/intelbasedMacBootIncompatibility)

In a nutshell, you need to partition the USB stick with GPT.

---

### Post by tom4everitt on 2009-11-29
I've never had any problem booting from a usb on my macs.

Can you give me some details on what exactly you do when you run the dd command (explained in step 7).

---

### Post by tarat on 2009-11-29
Ah, I gave up and found a blank DVD somewhere. 
I was just trying to get it onto the stick so I could put it in my (windows) laptop.
Thanks anyway!

---

