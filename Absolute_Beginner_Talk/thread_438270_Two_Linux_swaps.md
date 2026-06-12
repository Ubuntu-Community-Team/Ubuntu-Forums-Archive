---
title: "Two Linux swaps?"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by st33med on 2007-05-09
I was trying to get VMware working today when I noticed something strange about my partitions on parted...
```
Disk /dev/sda: 118526MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start     End       Size      Type      File system  Flags
 1      0.03MB    49.4MB    49.3MB    primary   fat16             
 2      49.4MB    100052MB  100003MB  primary   ntfs         boot 
 3      100052MB  117391MB  17339MB   primary   ext3              
 4      117391MB  118526MB  1135MB    extended                    
 6      117391MB  118197MB  806MB     logical   linux-swap        
 5      118197MB  118526MB  329MB     logical   linux-swap        


```
Linux has two swaps now! I'm might have screwed something up when installing... but whatever.
So I thought, "Which is being used?" I scanned parted's help code for something to use. I found something called 'check', which I used on 5 and 6. It told me it couldn't check 6 because it is being used. 5 went all the way through the check with no problems. Now I think I should eliminate 5, but I just want to be sure I'm not crashing the entire computer.

Is it alright to remove partition 5?:confused:

---

### Post by ZeroWing on 2007-05-09
> **st33med said:**
> I was trying to get VMware working today when I noticed something strange about my partitions on parted...
```
Disk /dev/sda: 118526MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start     End       Size      Type      File system  Flags
 1      0.03MB    49.4MB    49.3MB    primary   fat16             
 2      49.4MB    100052MB  100003MB  primary   ntfs         boot 
 3      100052MB  117391MB  17339MB   primary   ext3              
 4      117391MB  118526MB  1135MB    extended                    
 6      117391MB  118197MB  806MB     logical   linux-swap        
 5      118197MB  118526MB  329MB     logical   linux-swap        


```
Linux has two swaps now! I'm might have screwed something up when installing... but whatever.
So I thought, "Which is being used?" I scanned parted's help code for something to use. I found something called 'check', which I used on 5 and 6. It told me it couldn't check 6 because it is being used. 5 went all the way through the check with no problems. Now I think I should eliminate 5, but I just want to be sure I'm not crashing the entire computer.

Is it alright to remove partition 5?:confused:

 Even if you deleted both, and have over about a gig of RAM, then you'll still be okay.

 If you want to keep the swap, though, get rid of 5. It seems very small for a swap, anyways.

 Still, you might want to wait till someone with more Ubuntu experience responds. :)

---

### Post by hyper_ch on 2007-05-09
well, you can have multiple swap partitions... it just totals up the whole swap :)

---

### Post by Billy McCann on 2007-05-09
Eliminating 5 will be fine.  I ran without a swap for a while without even knowing it, though I have a gig of ram.  If it turns out that 5 was the one you're using (which it doesn't look like it is, from what you've said) then switching your system to use the other swap partition is a piece of cake.  

Just report here if you have any problems after removing partition #5.  

The output of the command "free" should indicate that you have available swap after you've deleted #5.  For instance,  here's how mine looks. 

```
billy@earth:~$ free
             total       used       free     shared    buffers     cached
Mem:       1027288     751268     276020          0      29496     338664
-/+ buffers/cache:     383108     644180
Swap:      3421836          0    3421836

```

yeah, yeah.  I have a tremendously, overwhelmingly ridiculously sized swap.  but it's turned on and that's all I'm illustrating.  

If you read a "0" for your total swap, then just post back here and we'll get you squared away.

---

### Post by st33med on 2007-05-09
That's weird.:(  My partition of swap 6 was removed as well...
```
             total       used       free     shared    buffers     cached
Mem:       1026468     414656     611812          0       9800     196400
-/+ buffers/cache:     208456     818012
Swap:            0          0          0

```

But when I checked free before I rebooted, it said that I had memory, though none was being used...

Maybe I don't need it?I have a 1 gig memory card. I always thought it needed iswap because of its need for memory, but that's Windows! :lol: Guess Ubuntu needs much less memory than I thought!

---

### Post by ZeroWing on 2007-05-09
> **st33med said:**
> 
Maybe I don't need it?I have a 1 gig memory card. I always thought it needed iswap because of its need for memory, but that's Windows! :lol: Guess Ubuntu needs much less memory than I thought!

 Unless you're using some virtualization software or heavy games, then you're right, you wont need one.

---

### Post by Billy McCann on 2007-05-10
Well, I'd sleep better with just a little swap, myself.  256MB should be fine, really.  If you want to create one, just do it using whatever software you're accustomed to.  

Then ...
```
sudo swapon <devicename>
```

My swap is /dev/sda3. So I run 'sudo swapon /dev/sda3'.

You'll want to put an entry in /etc/fstab as well.  

Feisty runs off UUID's it seems.  To find swap's UUID ...

```
sudo vol_id <devicename> | grep UUID
```

Then place a line in fstab for it.  Mine looks like this.  

```
# /dev/sda3
UUID=1f6cf072-86f4-404d-89a8-4f647c55db2d none            swap    sw              0       0
```

Let us know if anything is unclear.

---

### Post by Billy McCann on 2007-05-10
Wow.  Lo and behold, I actually used my swap today.  Beryl flipped out and ate up 1.3 Gig of swap at one point.  Glad I had it laying around.

---

