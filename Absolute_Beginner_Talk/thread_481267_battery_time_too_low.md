---
title: "battery time too low"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by babymechanic on 2007-06-22
hello i am a newbie i was using ubuntu 6.10 but 7.04 came out quite soon so i shifted to 7.04
my problem is that the battery time has reduced a lot.  i get only about 1 hr  on 7.04 where as i used to get more than xp(2hrs) on ubuntu 6.10 my machine config is

1. intel centrino duo 1.7 ghz
2. 1 gb ram
3. geforce go 7400
4. 100 gb hdd
5. i dont know much about the battery its the one i got by default in my machine
6. intel wireless pro wifi 

i use ubuntu for music,movies, programming . i have installed beryl,mysql and use wifi very frequently

---

### Post by 5-HT on 2007-06-22
laptop_mode and CPU frequency scaling (conservative governor) could help a lot. Display brightness is a major factor as well.

---

### Post by reset3x on 2007-06-22
> **babymechanic said:**
> hello i am a newbie i was using ubuntu 6.10 but 7.04 came out quite soon so i shifted to 7.04
my problem is that the battery time has reduced a lot.  i get only about 1 hr  on 7.04 where as i used to get more than xp(2hrs) on ubuntu 6.10 my machine config is

1. intel centrino duo 1.7 ghz
2. 1 gb ram
3. geforce go 7400
4. 100 gb hdd
5. i dont know much about the battery its the one i got by default in my machine
6. intel wireless pro wifi 

i use ubuntu for music,movies, programming . i have installed beryl,mysql and use wifi very frequently

I'm getting horrible battery life myself.....The kernel that will come with Gutsy in October is supposed have a patch to fix this....

---

### Post by babymechanic on 2007-06-23
thanks i tried cpu scaling and found out that my processor was running at full speed and i have changed the governer and now its running at 800mhz so i guess that should increase my battery time thanks:p

---

### Post by 5-HT on 2007-06-23
That'll definitely help you out. Another thing would be laptop_mode, which (among other things) will spin down the hard disk quite aggressively and enable a large write cache. It may get annoying because you can have some pauses for a second while trying to read/write to the disk, but it'll save quite a bit of power.

cheers,

---

### Post by babymechanic on 2007-06-23
i dont know i read in few of the forums that it puts quite a bit of strain on the harddisk

---

### Post by jcronkhite on 2007-06-23
Can anyone else confirm that this puts extra strain on the drive?  If not, I'd be interested in implementing this mode for my laptop.  Thanks!

---

### Post by crav on 2007-06-23
The battery time on my laptop has significantly improved, when I'm wired net and screen at lowest brightness, I last almost twice as long as I did with XP. Some of your stuff like Beryl that isn't really necessary causes the proc to work more, which takes more battery, try running without these things and see if the battery time increases

---

### Post by 5-HT on 2007-06-23
> **jcronkhite said:**
> Can anyone else confirm that this puts extra strain on the drive?  If not, I'd be interested in implementing this mode for my laptop.  Thanks!

Haven't heard that, but I'd be interested in knowing. I've been using laptop_mode for quite a while now.

---

### Post by octoberdan on 2007-06-23
You might also want to investigate, atleast for fun fun as it may not yet be a viable option for you, tickless kernels. Some fun recreational reading!

---

### Post by 5-HT on 2007-06-23
> **octoberdan said:**
> ...tickless kernels...
Available in >= 2.6.21 for those interested

---

### Post by babymechanic on 2007-06-24
for intel machines try this site maybe it could help you in saving more battery power
[http://linuxpowertop.org/](http://linuxpowertop.org/)

---

