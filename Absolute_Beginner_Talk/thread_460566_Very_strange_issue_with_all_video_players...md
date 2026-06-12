---
title: "Very strange issue with all video players.."
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by khardbored on 2007-05-31
Hi guys, another total Ubby newb here. I'm having issues with pretty much all video players included with this distro. I've also tried a few others that I grabbed form synaptic, including VLC. The problem is this...

I can play a movie just fine. Any movie, any format. But the second I move the players window or click on any of the players options, the pictures goes away. It's still there, playing the movie with the sound. The only way to get the picture back is to actually move the window. But even then the picture sometimes only shows for a brief second and I have to keep moving the window around until the picture comes back. It's not a major issue, but an annoyance. Anyone have any ideas? This is a used laptop I'm using, but im pretty sure its ussing intel i810...

Thanks a bunch guys!!!

---

### Post by Shazaam on 2007-05-31
Ahh the old shared memory trick. Can you add more ram to your laptop? Might help. Or, you can try (if you haven't already) the Legacy or proprietary video drivers.

---

### Post by khardbored on 2007-05-31
> **Shazaam said:**
> Ahh the old shared memory trick. Can you add more ram to your laptop? Might help. Or, you can try (if you haven't already) the Legacy or proprietary video drivers.

I just did an lspci and I believe I was wrong about my video card.
This is the relevant copy from the output

GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)

Not sure if that will make a difference, but in synaptic when I search for intel it says I have the 810 driver installed, is this sufficient or should I try something else? Also, ram upgrade is out of the question for the time being.

---

### Post by elpichi on 2007-05-31
i have the same exact problem, i don't have a permanent way to fix it but for now i just switch between workspaces and it returns the image until i click or move the application again :(

---

### Post by khardbored on 2007-05-31
Which card are you using? Have tried the aforementioned suggestion of legacy drivers?

I'm determined to get this problem fixed!

---

### Post by oiler920 on 2007-05-31
Try increasing your swap partition size to say 1GB (1024mb). I had this problem occasionally when running Windows XP Pro (the big mem hog ;)), but it went away with Ubuntu. Yay!

---

### Post by khardbored on 2007-05-31
I don't have any unallocated space at the moment. Not sure what I could use to increase my swapfile partition without data loss- thoughts?

---

### Post by Shazaam on 2007-05-31
Some have used thumb drives for /swap.

---

