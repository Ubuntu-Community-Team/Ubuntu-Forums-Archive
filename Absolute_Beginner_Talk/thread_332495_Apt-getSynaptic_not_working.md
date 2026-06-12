---
title: "Apt-get/Synaptic not working"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by AndyW on 2007-01-06
When I run sudo apt-get install **** I get this:
```
Reading package lists... Done
Segmentation fault (core dumped)

```

and when I run synaptic it opens for a second then closes. I dont know what is wrong, but lately (today) I have been getting errors at boot up like python unexpectedly closed.

I have done a couple things that could have been the problem. Yesterday I was overclocking my pc and it froze up a couple of times during the boot. Then after I stopped overclocking I had disk errors that it fixed. I also installed lm-sensors which took some boot changes. (minor ones I think)

---

### Post by quartzy on 2007-01-06
what happens when you run apt-get update?

---

### Post by AndyW on 2007-01-06
It updates fine.

---

### Post by ajmorris on 2007-01-06
Segmentation faults are memory access errors. (the program trying to access an area memory that is already being used.) Perhaps try re-installing synaptic.

---

### Post by quartzy on 2007-01-06
It still seg faults after the update? How about after you run a apt-get clean? (this will delete the local files meaning you will have to downlod anything you are trying to install again)

---

### Post by AndyW on 2007-01-06
> **quartzy said:**
> It still seg faults after the update? How about after you run a apt-get clean? 
1. Yes 
2. It didnt help

---

### Post by quartzy on 2007-01-06
Hmm, I don't really know then sorry.  Does it do it for all packages or just a specific one?

---

### Post by AndyW on 2007-01-06
anything, even upgrade

---

### Post by obsidion on 2007-01-06
> **quartzy said:**
> Hmm, I don't really know then sorry.  Does it do it for all packages or just a specific one?

  You could try sudo apt-get install -f
However it is looking like your ram could be at fault. Run the memtest and see what it comes up with.

---

### Post by NoWhereMan on 2007-01-06
IIRC it may happen when dpkg's db gets somehow corrupted

follow post number 3, here
[http://www.techiegroups.com/showpost.php?p=602599&postcount=3](http://www.techiegroups.com/showpost.php?p=602599&postcount=3)
or here [http://www.deanlee.cn/linux/apt-get-segmentation-faulty-tree/](http://www.deanlee.cn/linux/apt-get-segmentation-faulty-tree/)

**BACK THEM UP FIRST** ;)

---

### Post by steevc on 2007-04-20
I just had this segmentation error. I was trying to run Adept and it just crashed out every time. 

sudo apt-get upgrade

gave me:

Reading package lists... Done
Segmentation faulty tree... 50%

I fixed it by running the suggestion in the link:

sudo rm /var/cache/apt/*.bin

---

