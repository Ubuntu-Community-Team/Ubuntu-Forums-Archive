---
title: "CD disappeared"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by Gary Nored on 2006-05-03
I was having trouble with sound, and finally decided to give up and re-install afresh. But alas, now I have no cd drive (I had two). The system has a vague memory of their previous existence in that the file browser shows them but says "desktop configuration unknown."

How can I get these drives back?

---

### Post by ComplexNumber on 2006-05-03
> But alas, now I have no cd drive (I had two).
just to clarify, how do you know?

---

### Post by Gary Nored on 2006-05-03
Just guessing, really. Here is what I observe.

1. Machine wouldn't boot from cd, though bios was set properly. 
2. Then, there's the message in the file browser. 
3. If I insert an audio cd and try to open or play it, the system responds with 'drive empty' error. 
4. When I go to the Systems menu and list the disks, it shows 3 hard drives, only the first of which is 'known.' The others are 'unknown.' this seems suspicious, since the system has 1 hard drive and 2 cds. 
5. When i run the eject command I get the following response: 
gary@Mozart:~$ eject
eject: tried to use `/dev/hdd' as device name but it is no block device
eject: unable to find or open device for: `cdrom'
gary@Mozart:~$

Does any of this help?

---

