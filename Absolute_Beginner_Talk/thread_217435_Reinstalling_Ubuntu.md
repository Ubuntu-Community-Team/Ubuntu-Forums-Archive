---
title: "Reinstalling Ubuntu?"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by Starlight on 2006-07-17
Hello :)

I have a question... is it possible to totally reinstall Ubuntu from scratch, but without losing the home directory? I want to reinstall it, because I have some problems with a new wifi card... it doesn't work at all. :( I thought that maybe if I install Ubuntu again, the installer will somehow detect it and install the right drivers... but at the same time I have some important things in the home directory, and I don't want to lose it. Is it possible to do something like that?

---

### Post by Sef on 2006-07-17
If you have a separate home partition then you can reinstall Ubuntu without losing your files on your home partition.  However, back up your files, just in case something happens.  

I have reinstalled Ubuntu a number of times and my files on my home partition have been just fine.

---

### Post by adam.tropics on 2006-07-17
> **Sef said:**
> If you have a separate home directory then you can reinstall Ubuntu without losing your files on your home directory.  However, back up your files, just in case something happens.  

I have reinstalled Ubuntu a number of times and my files on my home directory have been just fine.

...you mean /home **partition** surely!

---

### Post by Starlight on 2006-07-17
I don't have a separate /home partition... and now I think I really need to reinstall Ubuntu, because I've just upgraded to 6.06 and now everything is totally messed up... :( I guess I have to get used to using Windows again...

---

### Post by tommcd on 2006-07-17
Back up your files. Reinstall Ubuntu. Set up 3 partitions:
/root  (5-7GB should be more than enough)
/swap (2x amount of RAM)
/home (what is left)
This way, if you reinstall again just reinstall to /root. The /swap and /home will remain untouched.

[https://help.ubuntu.com/community/HowtoPartition?highlight=%28partition%29](https://help.ubuntu.com/community/HowtoPartition?highlight=%28partition%29)

---

### Post by Sef on 2006-07-17
> you mean /home partition surely!

OOOpppss...yes. you're right. ty for spotting the error.

---

### Post by tommcd on 2006-07-17
Sorry, that was the wrong link. What I gave is the basic idea though.

---

### Post by tommcd on 2006-07-17
Ok here it is:

[http://psychocats.net/ubuntu/installing.html](http://psychocats.net/ubuntu/installing.html)

---

### Post by adam.tropics on 2006-07-17
> **Starlight said:**
> I don't have a separate /home partition... and now I think I really need to reinstall Ubuntu, because I've just upgraded to 6.06 and now everything is totally messed up... :( I guess I have to get used to using Windows again...

It seems a bit soon to give in! If you decide to give it another go, look around for stuff on partitioning, there's loads, and create at least a seperate /home partition. This really does cut the pain, or at least most of it from reinstalling, should that become necessary. (as tommcd said above)

---

### Post by vincentvee on 2006-07-17
aawwwwww man don't go back to windows, live with and enjoy the challenge of gettin by without the gates crutch

---

### Post by Starlight on 2006-07-17
Thanks for the help :) I copied the most important things from my home directory to my Windows partition, and I'm going to reinstall Ubuntu now... I hope it will work! :)

---

