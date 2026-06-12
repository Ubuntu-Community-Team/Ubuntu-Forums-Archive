---
title: "[SOLVED] Can I hibernate both partitions in a dual boot?"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by sab0403 on 2007-06-21
at the same time, even?

Running Feisty and WinXP.

---

### Post by deadgobby on 2007-06-21
I want to say no, but your question is not detailed for a correct answer. What are you trying to do?

---

### Post by sab0403 on 2007-06-21
Ok, sorry.

I have WinXP in one partition, and Ubuntu 7.04 in another (plus the swap, of course). I'm dual booting, but I find the time spent in booting to one OS and then another to be huge (particularly when booting to XP, it takes like three minutes). I'd like to, for instance, boot to XP, hibernate, then boot to Ubuntu, hibernate, and then boot to whichever hibernated OS I'd want to (which would take considerably less time). In essence, to keep my OS's hibernated instead of shut down.

Can I do that? Or will there be boot problems / data loss / performance issues? I've read about these things happening, but I don't know if they *always* happen, or if it's something rare, or somewhere in the middle.

---

### Post by deadgobby on 2007-06-21
No you can not do that at this time. You can cut the time on of the time to select to boot up and which OS. Yet you cannot hibernate one or the other. Yet, you can get Ubie to read off your windows partition and see every thing. To give you the heads up. MS does not like to play nice to any OS on the HD. I thought sharing was caring, but MS see it differently. 
Gobby

---

### Post by gn2 on 2007-06-21
> **sab0403 said:**
> 
 I'm dual booting, but I find the time spent in booting to one OS and then another to be huge 

Why not just use VMWare Server (Free edition) and run them at the same time?

---

### Post by sab0403 on 2007-06-21
> **deadgobby said:**
> No you can not do that at this time. You can cut the time on of the time to select to boot up and which OS. Yet you cannot hibernate one or the other. Yet, you can get Ubie to read off your windows partition and see every thing. To give you the heads up. MS does not like to play nice to any OS on the HD. I thought sharing was caring, but MS see it differently. 
Gobby

Oh well. Thanks anyway. Mostly I'm flip-flopping right now because I'm transfering a lot of settings...

---

### Post by sab0403 on 2007-06-21
> **gn2 said:**
> Why not just use VMWare Server (Free edition) and run them at the same time?

Hmm. VMWare Server wasn't even in my plans... can I use with a physical partition like with Workstation?

---

### Post by AtrejuT on 2007-06-21
If you have a newer processor supporting virtual machine extensions you can also use things like qemu+kqemu/kvm/xen with which I managed to boot from an existing partition just like that. Really not a lot of hassle (kvm worked quite nicely in my case, and no recompiling kernel and stuff). However windows then sees a lot of different hardware and wants to be reactivated :-((

---

### Post by gn2 on 2007-06-21
> **sab0403 said:**
> Hmm. VMWare Server wasn't even in my plans... can I use with a physical partition like with Workstation?

After installing VMWare Server, it prompts you to create a store location (folder) for your Virtual PC.
I reckon that could be on any partition, but am not certain about any issues concerning file system compatibility.
When I used it with XP, I had my Ubuntu VM store folder on a separate partition.

(XP now banished and Xubuntu only on my PC/Laptops.)

---

### Post by bren on 2007-06-21
hi sab043

i only hibernated one OS so far (XP) but found that boot to Ubuntu slowed down by factor of 4 if i did this....

don't know why

bren

---

### Post by sab0403 on 2007-06-21
> **AtrejuT said:**
> If you have a newer processor supporting virtual machine extensions you can also use things like qemu+kqemu/kvm/xen with which I managed to boot from an existing partition just like that. Really not a lot of hassle (kvm worked quite nicely in my case, and no recompiling kernel and stuff). However windows then sees a lot of different hardware and wants to be reactivated :-((

Well then... I might try that instead.

How much "newer" does my processor have to be? It's an Intel Centrino (1.82 Ghz), btw...

---

### Post by sab0403 on 2007-06-21
> **bren said:**
> hi sab043

i only hibernated one OS so far (XP) but found that boot to Ubuntu slowed down by factor of 4 if i did this....

don't know why

bren

I already tried to hibernate (just) Ubuntu, but the process is slower than simply shutting down / booting up.

If it's going to be even slower hibernating both... I might as well go with the virtual machine option. Sounds better anyway... :D

---

### Post by dndrich on 2007-07-09
Bren:

Are you able to hibernate Windows XP?  That is what I am trying to do.  I just want to hibernate XP only so that it boots quicker.  I don't need to hibernate Ubuntu, since it boots quickly.  You have been successful bringing XP out of hibernation?  How?

Daniel

---

### Post by bren on 2007-07-10
hi Daniel 

I only did this by mistake so far...... XP set to hibernate automatically after 1 hr on power management options.....Then booted later (1st option is Ubuntu) and forgot about previous xp session.    Am sure you could also do in normal way SHUTDOWN/HIBERNATE so long as your hardware supports it.

However, as others have said above it is slower not faster (to hibernate xp rather than full shutdown)  because Ubuntu then takes 4 (?) times as long as normal to boot up.

I think this may be resolved in future issues of Ubuntu - you could look at the bug/wishlist to find out.

If I boot XP after XP hibernate it recovers no problem as per normal XP hibernate

Bren

---

### Post by dndrich on 2007-07-10
OK, yup, you are right.  I thought I had tried it, but I hadn't.  XP will hibernate and boot back just fine.  This is what I need to do for my family.  They are using the XP partition only, and have no interest in Ubuntu.  I am just using Ubuntu for fun, so I didn't want to mess up their experience.  It will be a hard sell to get them to convert to Ubuntu!

Daniel

---

### Post by sab0403 on 2007-07-10
So I guess the final conclusion would be a big, fat... YES, *but* it will slow everything down. So it's not worth it.

Alright. Thank you all!

---

### Post by bren on 2007-07-11
dndrich

so what you could do is set xp to be the first option when your machine boots....
then if your family has hiberbated xp and they wake it up again they will get what they are expecting...

i think you can search for GRUB in this forum on how to change the order of different OSs at boot time

bren

---

### Post by dndrich on 2007-07-11
Yes, that is what I did in the menu.lst through Ubuntu, and it works just fine.  Thanks!

Daniel

---

### Post by Nigel_C on 2008-04-24
This answer is wrong. You can hibernate both Windows and Linux and resume whichever you like.

You just need to have Grub as your bootloader so that you can still get the choice of which OS to start when powering back on after hibernating Windows.

If you find hibernating Linux too slow with swsusp, try TuxOnIce or maybe uswsusp.

Nigel

---

### Post by meanburrito920 on 2008-04-24
> **Nigel_C said:**
> This answer is wrong. You can hibernate both Windows and Linux and resume whichever you like.

Nigel

Are you certain about that? Because I have heard that there are issues dealing with the fact that Ubuntu does not fully unmount disks upon hibernate, so that when xp is booted and written to Ubuntu thinks the disk has been corrupted. I could be wrong, but I was pretty sure that this was an issue.

---

### Post by Nigel_C on 2008-04-24
You'll only have problems if you're trying to access one or more partitions from both OSes. If you treat them as completely separate installations, there'll be no problem at all. (The original question, AFAIR, only asked about the general idea of hibernating both OSes).

Even if you do want to share data, between OSes, it's not impossible. The key principle is that you don't want to change data on a filesystem that's been mounted and then hibernated. You could, for example, create a partition that was mounted by both OSes provided that it's always unmounted prior to hibernating in both cases.

So if in Ubuntu you have the M$ partition mounted, just unmount it prior to hibernating Ubuntu, and remounted it after resuming. As long as you don't write to the M$ partition that's hibernated, no corruption should occur.

Regards,

Nigel

---

