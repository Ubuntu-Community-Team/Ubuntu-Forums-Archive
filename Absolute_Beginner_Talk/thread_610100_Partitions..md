---
title: "Partitions."
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by ajdude101 on 2007-11-11
Hi, how would I go about making a partition?I am using Ubuntu and want to have like a 30 GB partition for Ubuntu and 50 for everything else. Thanks.:):popcorn:

---

### Post by DutyDuty on 2007-11-11
Are you running Ubuntu right now? The Live CD makes a partition for you.

---

### Post by OA-5599 on 2007-11-11
install gparted:

```
sudo apt-get install gparted
```

you find it under:

system - administration - partition editor

---

### Post by ajdude101 on 2007-11-11
k installing right now

---

### Post by ajdude101 on 2007-11-11
gparted doesn't give me any options to make a partition :confused: Ubuntu is such a headache.

---

### Post by schauerlich on 2007-11-11
What current partitions do you have?

---

### Post by Sorivenul on 2007-11-11
You may want to be more specific with what you want to do with your partitions.  To install Ubuntu you will need one partition for the OS, and one for swap.

Do you already have another operating system on the disk, or are you starting from an empty disk?

Once we know these things we can begin to guide you through using GParted to partition your disk.

---

### Post by ajdude101 on 2007-11-11
um it says ext3, extended, and linux-swap. Sorry I am a complete noob :(

---

### Post by ajdude101 on 2007-11-11
Okay. I want this old computer to have Vista on it. My disc isn't bootable, so I figured I would put Ubuntu on my comp and then install Vista. Get it? :)

---

### Post by Sorivenul on 2007-11-11
While it's possible to install Vista after Ubuntu, any post in the forums would say install Vista first.  Installing Vista after Ubuntu causes boot headaches at the very least.  I don't personally use Windows (OSX/Ubuntu/Sabayon user here), so as for installing the Windows OS I'm rather useless.   If you decide to keep it a pure Linux machine, I'm all for it.  Good luck to you, either way.

---

### Post by scruffybeard on 2007-11-11
> **ajdude101 said:**
> Okay. I want this old computer to have Vista on it. My disc isn't bootable, so I figured I would put Ubuntu on my comp and then install Vista. Get it? :)

It's been my experiance with Vista that trying to make an old computer run it is like trying to convince a Buick to drive across the Atlantic. 

That aside, what were you hoping to gain by installing Ubuntu? I don't personally know of a way to install Vista from within Ubuntu, and if your Vista disc isn't going to boot, I think you may have bigger issues.

---

### Post by ajdude101 on 2007-11-11
I installed Vista on this machine once, but then I got a new computer so I formatted the HD so I can use it in the new computer. Long story. Anyway, I got the Vista installer working, but it says something like I need a partition. I will get a pic  up.

---

### Post by ajdude101 on 2007-11-11
[IMG]http://i28.photobucket.com/albums/c225/ajdude101/Screenshot-1.png[/IMG]

---

### Post by scruffybeard on 2007-11-11
Why is your Windows disc not bootable.

---

### Post by scruffybeard on 2007-11-11
Better question, how did you install Vista before?

---

### Post by justsomedude on 2007-11-11
Are you trying to set up a virtual machine? :confused:

---

### Post by ajdude101 on 2007-11-11
*hint* torrent :o. I have the full version but it is for 64 bit. I installed it before because I had XP before.

---

### Post by ntu on 2007-11-12
> **ajdude101 said:**
> gparted doesn't give me any options to make a partition

? So what options has it given you?

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
well you dont have any room left to make a partition right

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
so your going to have to make room by resizeing one of your existing partions then make the new one
gparted is a good program you shouldn't have a problem i had my dog install linux on my computer useing gparted for a pit there no afence  shes a really smart dog but i dont wanna put her on tv 
i am afrad it will leaded to drug problems later in life you know how child-actors.

---

### Post by Harpoon on 2007-11-12
If you are trying to repartition using gparted from within a working ubuntu system, and you only have one disk, it is not possible.

For gparted to delete/create/resize/etc the disk you are working on ***cannot be mounted***.  So, if your operating system is on that disk, you cannot unmount it.  There are two solutions:  you can try using an ubuntu live cd;  you can download the gparted live cd, burn it to a cd, and boot into that.  The second is preferable because the cd is great for rescue work.

---

