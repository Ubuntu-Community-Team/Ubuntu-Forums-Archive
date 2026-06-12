---
title: "Macbook 2,1 9.10 dual boot grub problems"
date: 2010-06-25
forum: Apple Hardware Users
---

### Post by david e on 2010-06-25
Ok, so:

I'm using a MacBook 2,1 (summer 2007). I've had a dual boot of Snow Leopard and Karmic Koala without any issues for about six months now, until the other day. What started happening was an issue that a lot of people seem to have with the Grub blinking cursor appearing when it tries to boot and nothing else happening. rEFIt said that the partition tables were synced, and so did gptsync, so I doubt that that's the problem.

Now, what's been happening instead of that for two or three days is that it boots into the grub console. I found a thread that suggested this:
```

find /boot/grub/stage1
root (hd?,?) 
setup (hd0)

```where the question marks are what gets returned by find ((hd0,2) and (hd0,3) for me). I tried this (with both) but nothing changed.. I also tried selecting the kernel manually with
```

kernel /boot/vmlinuz* 

```but it always would panic and crash, and then it was back to square one after a reboot. 

I haven't been able to make any progress and I'm about out of ideas.... can anyone help? Thanks!

---

