---
title: "hardware REscan?"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by garnertr on 2006-02-12
Is there an app in KUBUNTU that can rescan my hardware and reupdate my settings?

I have a DVD-RW drive that is not recognized (ie, put dvd or music cd in drive, nothing happens).

I was just curious if I can force Ubuntu to rescan my hardware... thanks

---

### Post by genuchelu on 2008-02-14
same problem here... I have the ATI remote wonder (not the IF version), and it worked fine with the live CD, but once I've isntalled ubuntu, it didn't work anymore...and I i don't ahve any clue on how to even approach the problem.

---

### Post by Tatty on 2008-02-14
Im not sure about there being a hardware rescan option, But if you post threads about your problems on the forum, there is usually someone who can help you out.

Have you tried searching the forums?  there are usually other people having similar problems

---

### Post by genuchelu on 2008-02-14
I looked at a few threads of people having issues with the ATI remote wonder, but not the problem I was having. What I don't understand, is why it worked before, and now it doesnt.  So I know that is SHOULD work, but it doesn't... any way that I can diagnose the problem? there was a terminal command that displays all devices.. whats that command..then I can see if its at least detected..

---

### Post by Sinkingships7 on 2008-02-14
i have the same problem. switched cd/dvd drive yesterday and my old one still shows up under places -> computer, but so does my new one. ubuntu isn't seeing my new one as my default or something because no virtual machine software has been able to detect it.

---

### Post by Tatty on 2008-02-14
> **genuchelu said:**
> there was a terminal command that displays all devices.. whats that command..then I can see if its at least detected..

lsusb will show you all the usb devices

lspci will show you all the pci devices.

Im afraid i dont know much about the ATI remote wonder, it might be worth starting a new thread with "ati remote wonder" in the title, hopefully someone who knows about it will spot it and be able to help you out.

---

### Post by genuchelu on 2008-02-14
> **Tatty said:**
> lsusb will show you all the usb devices

lspci will show you all the pci devices.

Im afraid i dont know much about the ATI remote wonder, it might be worth starting a new thread with "ati remote wonder" in the title, hopefully someone who knows about it will spot it and be able to help you out.

thx.. it turns out that my received is detected as:

```
Bus 002 Device 010: ID 0bc7:0004 X10 Wireless Technology, Inc. X10 Receiver

```

whats the next thing as to why it wouldn't function?

---

