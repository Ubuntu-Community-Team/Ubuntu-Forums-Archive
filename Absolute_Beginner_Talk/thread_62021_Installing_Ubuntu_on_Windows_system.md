---
title: "Installing Ubuntu on Windows system"
date: 2005-09-03
forum: Absolute Beginner Talk
---

### Post by walterius on 2005-09-03
I am brand new to Linux and Ubuntu and barely know how to post.

I studied the other thread with the same title, but I couldn't solve my problem. ](*,) 

I have a dual boot Windows 2000/ME system on which I installed Ubuntu yesterday. FYI I have four versions of Win 2K installed, one of which is the default.

GRUB promised to let me still boot to Windows, and it will. Except I can't boot to my main (default) system--I get a Kernal Missing error. I can boot to Win ME, the three other Win 2000 systems, and the Recovery Console, but not to the main Win 2K system.

At the moment, therefore, I have no Internet access in Windows (I only allow the main Win 2K system to have Internet access). I also can't use most of my main apps because they are in the main Win 2K system.

I know how to fix the Kernal Missing error in Win 2K, but that would blow away my new Ubuntu system.

Any help would be greatly appreciated and humbly accepted.

Walterius

---

### Post by bjweeks on 2005-09-03
Would is be possible to start form scratch and put 1  Windows and 1 lUbuntu partion that would be alot easier. I commend you for useing Windows ME that is the worst os ever. ](*,)  
> (I only allow one system to have access) I dont understand.

---

### Post by walterius on 2005-09-03
I don't want to rebuild an established multiboot Windows 2000 system. I would probably even give up Linux before doing that. I also don't want to trash Windows ME, which works great for me, and has many useful features not available in Windows 2000.

How about more help from someone who has answers?

Thank you. I'd appreciate it.

Walterius

---

### Post by numberexhaust on 2005-09-03
What you need to do is boot into linux and follow a couple of steps.

First: install the program qtparted.  using apt-get:

```
sudo apt-get update
``` 
```
sudo apt-get install qtparted
``` 

Next, run the program, but in su mode.

```
sudo qtparted
``` 

Take a look at your main hard disk and keep it running in the background.

Now we're going to edit the grub config file:

```
sudo gedit /boot/grub/menu.lst
``` 

Scroll down until you get to a couple of options like this:

> title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hdc6 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot 

Every one of these are a boot option.  Using the info from qtparted and the examples here, append the boot config file to match the hard disks that are missing.

Hope this works for you,

---

### Post by walterius on 2005-09-05
Thank you. Helpful guidance at last. I have one question before trying what you posted: If I follow the directions carefully, will my current multiboot system be *safe*? I already blew both Windows ME and Windows 2000 MAIN trying to use GRUB. I'm a little scared. I reinstalled both OS's, but it is tedious to tweak two large systems and I'd like not to blow them again!  \\:D/

---

### Post by numberexhaust on 2005-09-05
[QUOTE=walterius]Thank you. Helpful guidance at last. I have one question before trying what you posted: If I follow the directions carefully, will my current multiboot system be *safe*? I already blew both Windows ME and Windows 2000 MAIN trying to use GRUB. I'm a little scared. I reinstalled both OS's, but it is tedious to tweak two large systems and I'd like not to blow them again!  \\:D/[/QUOTE]
 Nothing changes until the last step where u edit the grub config file.  As long as you follow the format, the only thing that gets changed is the bootloader... it shouldn't affect the partitions at all.

If you would like to see another example of what a windows entry in the bootloader looks like, post back and I'll put my entire grub config file up... it has windows xp running with ubuntu.  I'd say you're pretty safe doing this, because even if you mess up it's just a matter of installing the bootloader again.  (or worst case, installing ubuntu again, which is pretty simple).

---

### Post by rafakl on 2005-09-05
Is qtparted similar to Windows Partition Magic??

---

### Post by Hobbsee on 2005-09-06
[QUOTE=rafakl]Is qtparted similar to Windows Partition Magic??[/QUOTE]

Yes, but it's free, and for linux.  It will let you partition your drives, and will actually partition them without having to buy a full version of it....

---

### Post by walterius on 2005-09-07
Yes, I would much like to see your (forgot the name) file. Please post it. I have been busy the last few days rebuilding Windows ME and Windows 2000, but they are about done and I can now devote my attention to learning Linux.

I also appreciate the input about how nothing changes until the end, and even if I blow it I can recover.  \\:D/ 

Any good Linux books (inexpensive) for newbies that are also advanced enough that I can refer to them later after I get past the newbie learning curve?

I have 22 years as a software designer, now retired, and learning new OS's is nothing new.

Walterius

---

### Post by walterius on 2005-09-07
Never mind the file. After blowing my Win ME system the second time -- I am rebuilding it now -- I realize that cryptic directions such as your "boot to linux" are useless. That was the whole problem: I *couldn't* boot to linux and I blew my system twice by trying.

If I choose to pursue Linux further, I'll start with a good book.

I appreciate your help, but it was *way* over my head.

Linux appears to be an extremely geeky system.

Walterius

---

### Post by numberexhaust on 2005-09-07
Well I would honestly not rush into conclusions like that.  Linux has one purpose only... to give the pleasure of knowing that you have an operating system that everyone else would fail miserably trying to even boot up.  I cannot count the number of times I have been presented with a difficult problem in linux, and if I had quit on any occasion, I would not be enjoying the computing experience I am today.  So as for Linux, don't be turned off by it at all... everyone falls (all the time, actually), that's what these forums are for.

If you want a good book, I probably wouldn't recommend Linux for dummies.  It's the only linux book I have and it doesn't help nearly as much as I would like it to.  But of course, starting out with a good book is always a good idea.

---

### Post by walterius on 2006-04-10
On rereading the thread, I realize I was rather short with people who were only trying to help me. I apologize. My struggles to learn a new OS in less than a week were (a) fruitless and (b) frustrating.

I have put Linux aside and will keep it there for a day or two. I am temporarily burned out.

Thanks to everyone.

Walterius Oldfartus.

---

### Post by walterius on 2006-04-16
Apologies for my shortness with those who were only trying to help me. When I get stuck, esp. with something new, I get grouchy and short. :-| 

Today I installed qtparted and used it to examine my partitions. Same format as Partition Magic, which I have on Windows.

Question: would it be safe to delete the two grub references to the earlier kernal? They seem useless to me and I never use them.

I also guess it would be safe to change the alternate OS's text to "Windows ME and Windows 2000 Pro"?

I would back up menu.lst and edit a copy, so if I blew it I could restore the original.

---

### Post by htinn on 2006-04-16
Shouldn't be a problem. I edit my menu.lst all the time.

---

