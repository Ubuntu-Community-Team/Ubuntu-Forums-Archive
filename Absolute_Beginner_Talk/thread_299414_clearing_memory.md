---
title: "clearing memory"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by ckonrad on 2006-11-14
Is there a command or program in linux i can use to clear ram without restarting my computer? It just keeps going up and up and up the longer i use my computer, its not a big deal i am just curious, i dont have an issue with restarting.

Thanks

---

### Post by LLRNR on 2006-11-14
This sounds kind of strange to me. How much RAM do you have ? It is a normal behaviour to fill up only if you have a very low amount of RAM, if not... I don't know, I can only see 2 ways: either you're running some strange apps that "eat up" your memory, either there is something wrong with the memory card(s) itself(themselves). In this latter case, you might try to boot from the Live CD and select the MemTest86+ Memory Test from the Live CD's menu. It's a very useful utility... but hang on, it _will_ take a while. Even if you don't think that there's something physically wrong with your RAM, every now and then it doesn't hurt to do a check, you could never know what's going on. (Take me, for instance: in the past week, BOTH my CD-RW _AND_ my HDD died :()

HTH,

LLRNR

---

### Post by jd65pl on 2006-11-14
The linux kernel is designed to use a lot of ram for buffering and cache. This shouldn't give you any issues, things may happen a little faster if the item is already loaded into the ram.

---

### Post by esaym on 2006-11-14
free ram is wasted ram. this is not windows.

---

### Post by monkieie on 2006-11-14
> **esaym said:**
> free ram is wasted ram. this is not windows.

very right!

Linux (or UNIX for that matter) grabs just about all of the RAM that it can. This is a good thing and - once processes are loaded - increases speed and stability.

---

### Post by ckonrad on 2006-11-21
> **monkieie said:**
> very right!

Linux (or UNIX for that matter) grabs just about all of the RAM that it can. This is a good thing and - once processes are loaded - increases speed and stability.

that isnt really what i have noticed, the longer i leave on my system the more memory is used until the system just locks up when i try to run a program, then i have to restart. So there is definatly some kind of memory leaking process going on. It takes a full day for this to happen, i start out using about 100mb and then i will close all programs and just let it sit all day and when i come home it is using about 600mb ram. I have done the memory test and i havnt found any issues. HOwever one wierd thing, is i have 1 stick of 256 and another stick of 512 and it only shows that i have 629.8mb ram as my base amount, thats is pretty strange isnt it? Even before i use any ram, my base ram is lower than it should be, i should have 768mb of ram, so i have no idea what the issue is. I understand how ram works and that it makes the system faster but when it doesnt free up memory that is needed to run an app and just locks up requiring a restart that is wierd to me. When i was running windows, that never happened on this laptop. I dont need my laptop on all the time and i dont mind restarting but i just found this problem strange, there must be some process with a memory leak running in the background i just cant figure out which one it is. If i could found out i guess i would submit a bug report to them or something,

---

### Post by tribaal on 2006-11-21
Did you run a memtest at startup? If not, stick an Ubuntu CD in your drive, reboot, and select memtest at the very forst prompt.
Let it run for a while (at least 2 passes).

This is the only way to make really sure your physical RAM is ok.

As others said, Linux stuffs up the RAM with disk cache - if you want more info on that check out the link in my signature.

If you -still- notice a problem, well... try to find out which program leaks by comparing memory usage at startup and close to when it fails?

Hope this helps you at all...

- trib'

---

### Post by adam.tropics on 2006-11-21
the difference in reported and physical ram is most likely your video card's shared memory.

---

### Post by ckonrad on 2006-11-21
well i took out the 512 and looked at it and it was sdram and the 256 was ddr  the 256 works better alone than with the 512 i mean my system doesnt lock up at all after i took the 512 out. Both sticks are fine, there just must be some wierd thing going on with the fact that they are different kinds of ram. I am not a technician so i dont know i'll have to look that one up.

---

### Post by wpshooter on 2006-11-21
> **ckonrad said:**
> well i took out the 512 and looked at it and it was sdram and the 256 was ddr  the 256 works better alone than with the 512 i mean my system doesnt lock up at all after i took the 512 out. Both sticks are fine, there just must be some wierd thing going on with the fact that they are different kinds of ram. I am not a technician so i dont know i'll have to look that one up.

Well, problem solved.  Don't mix memory types.  You should check with your motherboard manufactuer and make sure exactly what memory is compatible with your motherboard.  You can probably also find this out from one of the major memory manufacturers.  Some of the memory manufacturers (like I think Kingston) have tools on their websites that will aid you in determining the exact memory you need for any given machine.

Good luck.

---

