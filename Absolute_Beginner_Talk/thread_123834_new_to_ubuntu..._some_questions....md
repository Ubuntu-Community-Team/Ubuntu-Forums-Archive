---
title: "new to ubuntu... some questions..."
date: 2006-01-31
forum: Absolute Beginner Talk
---

### Post by Leo_01 on 2006-01-31
1. Can i run ubuntu without any anti-virus program?

2. are there proper support for using ubuntu with a wireless adapter?

3. Can ubuntu show the battery life of my laptop and goes into "sleep" if the batt is low?

4. I heard Linux does not support NTFS... Is it true?

5. Err... do i actually need a swap partition?

Thanks in advance!

---

### Post by mcduck on 2006-01-31
1. Yes, you don't need any antivirus programm. Even firewall is optional :D

2. Depending on your adapter, yes. You might want to check your adapters linux support with google. (or I think there was some tested hardware database somewhere)

3. I don't have a laptop myself, but battery monitor sure is available, and I'd be surprised if shutting down on low batt wasn't possible.

4. It's true. NTFS is Microsofts proprietary file system, and they won't release it's specs so making proper support for it is hard. You can still read from NTFS, but writing isn't supported. There are some hacks to enable even writing, but they aren't 100% safe and at least I don't trust them.

5. Yes, you do. make it 2x your memory, or if you have 1GB or more of ram, 1GB of swap is enough.

---

### Post by Leo_01 on 2006-01-31
ok.. final stupid question...
is there a guide on how to install ubuntu which gives me a cosy and easy feeling?

EDIT : I have found a nice guide... what is the miniment requirement of space to install ubuntu?

---

### Post by Herman on 2006-01-31
>  I have found a nice guide... what is the miniment requirement of space to install ubuntu? Welcome, Leo_01,
I think the full operating system itself takes up at least 1.7 or so GB, plus you'll need at least a small swap area as well, the partitioner will probably create that for you automatically, depending on what install guide you have decided to use. The cover of the Shipit CDs says 1.8 GB is the minimum, and that would likely be pretty close. You wouldn't be save very many files with an install that small though, only try Ubuntu out. It would do everything, but you might as well try Ubuntu out on the Live CD if you have to make it that small and not have room to save any files.
If you really need it smaller than that, there will be ways of doing a special server install or something like that, and installing only the bare minimum of things you require. I'm not able to give any help with that other than to say I think it's possible, But I don't know much about it. 

Personally, I would recommend around 3.0 GB or more if you can if you want to not be too restricted. Of course, more than that even, would be better, but I have used Ubuntu on 3.0 GB installs quite alright. :-D (Herman)

---

### Post by 3rdalbum on 2006-01-31
Let the partitioner create the swap partition for you. According to the Disks administration panel, my swap partition is only 111 mb! Also, virtual memory on Mac OS 9 worked best when it was less than 1.5 * (installed memory - RAM disk); Ubuntu may be the same.

I set aside 2 gigs of space for Ubuntu when I installed, and now I'm cursing myself for not setting aside more. (still, what can you do with only 6 gigs to begin with?). For the record, I've got 100 megs free in my home folder, and I don't have many packages at all installed.

---

### Post by Leo_01 on 2006-01-31
is 256mb of RAM ok for normal use? (it is a pretty old laptop)

---

### Post by byen on 2006-01-31
yes ubuntu would run smoothly on a 256 ...but I do suggest having atleast 512 mb swap.

---

### Post by Carchanestar on 2006-01-31
Hello everyboody.

I'm just trying to install Ubuntu 5.10 on my PC, but it hangs up between 31-34% of the installation of the main core. Someone knows why this happen? 
I would be really greatfull for an answer cause I really want to try Linux for the first time.
Thanks!!!

---

