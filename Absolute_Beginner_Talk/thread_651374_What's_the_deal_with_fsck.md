---
title: "What's the deal with fsck?"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by Jugney on 2007-12-27
Hi everyone,

I have read a few posts here about the fsck on boot freezing problem. I agree that it's best to leave it on, but what's the point if it always freezing? 

I will disable it for now because I have work to do, but would be happy to bring it back if anyone knows how to make it work without freezing. 

Jugney

---

### Post by taurus on 2007-12-27
It usually freezes because you try to run it with either ntfs or vfat filesystem.

---

### Post by Jugney on 2007-12-27
Interesting. I have a dual boot with Vista, although Vista has its own partition if that makes any difference.

So does fsck simply not work in my scenario? I thought Ubuntu was supposed to be dual-boot friendly, so it seems pointless to keep this utility in the regular boot schedule if it won't work for dual-booters.

---

### Post by taurus on 2007-12-27
I think you misunderstood me.  Dual boot has nothing to do with fsck.  Basically, you want the system to run fsck after 30 times (you can change that value) of your ext3 partitions but you don't need to run fsck for vfat and ntfs filesystems.  It means that the last two digits in /etc/fstab for ntfs filesystem should be 0 0.

Look in your /etc/fstab to see if that's what you have?

---

### Post by Jugney on 2007-12-27
Thanks. How do I access fstab if I can't get into a command prompt even in recovery mode due to it trying to scan my partition?

---

### Post by taurus on 2007-12-27
You can edit /etc/fstab from the LiveCD.  You first need to boot from it.  Then, you have to mount the partition where / is, and then you can either view it or edit it.

Assuming your / is resided on /dev/sda2, you can do something like these from a terminal of the LiveCD.

Applications -> Accessories -> Terminal
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda2 /media/ubuntu
more /media/ubuntu/etc/fstab
```

---

### Post by Jugney on 2007-12-27
Well, it turned out I ijust needed a little patience. I went away for awhile and came back to it, and it actually finished, despite the percentage indicator having been frozen for a couple minutes. It said something like 1.1% uncontinugous, but I was able to boot again just fine. What does 1.1% uncontiguous mean?

---

### Post by rsambuca on 2007-12-27
> **Jugney said:**
> Well, it turned out I ijust needed a little patience. I went away for awhile and came back to it, and it actually finished, despite the percentage indicator having been frozen for a couple minutes. It said something like 1.1% uncontinugous, but I was able to boot again just fine. What does 1.1% uncontiguous mean?

That is like the 'defragmented' terminology from Windows XP.  Having just 1.1% is very good.

---

### Post by Jugney on 2008-01-10
Hello again,

Well, it's coming up again. I guess I neglected to turn off fsck and now I'm stuck again. I let it run overnight and it still didn't budge. As you can see from my above post I was able to get it to finish in the past, but this is really a problem. It's now been almost 24 hours since I've been able to get into ubuntu (I can't boot from a LiveCD because the Gutsy LiveCD doesn't work on my machine).

So I guess I need to repeat the question of this thread - what is the deal with fsck? 

The next time I can manage to get into ubuntu I will definitely disable this feature.

Jugney

---

### Post by Jugney on 2008-01-25
Just wanted to follow up here one more time...I erased all other partitions off my computer and did a clean install of Ubuntu, so now it is the only OS on my computer. FSCK still freezes at a certain percentage. Does anyone have any idea why it would freeze (and I let it run overnight with no progress) now that I know the problem doesn't have to do with NTFS filesystems?

Jugney

---

### Post by nymlord on 2008-03-01
> **Jugney said:**
> Just wanted to follow up here one more time...I erased all other partitions off my computer and did a clean install of Ubuntu, so now it is the only OS on my computer. FSCK still freezes at a certain percentage. Does anyone have any idea why it would freeze (and I let it run overnight with no progress) now that I know the problem doesn't have to do with NTFS filesystems?

Jugney

I am experiencing the exactly same problem and would love to get it solved! im also running a dual boot laptop with original vista, but now ereased vista and its only being used for Ubuntu 7.10. i really need help because im tired of reinstalling the OS every 30 restarts.... 
like he said, whats the deal with fsck ??? :S

---

### Post by expatCM on 2008-03-02
perhaps you want to try AutoFsck to increase the frequency between checks ...
[https://wiki.ubuntu.com/AutoFsck](https://wiki.ubuntu.com/AutoFsck)
no idea if it will address the freezing issue but it does work very well in managing Fsck ...

---

### Post by astrotech226 on 2008-03-02
My laptop was doing this as well, so I turned off the interval counts on the partition itself.

```
sudo tune2fs -i 0 -c 0 /dev/sda1
```

So it will never auto fsck based on mount counts or number of days.  Change your device to match your setup.  What's odd is booting from the LiveCD and doing a manual fsck works fine.

---

### Post by nymlord on 2008-03-05
so i typed in this to the terminal 

sudo tune2fs -i 0 -c 0 /dev/sda1

and that should disable it from running fsck checks after 30 boot ups ?? or am i supposed to do anything more ?

---

