---
title: "reinstaling Vista after installing Ubuntu?"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by ryan22158 on 2008-04-13
So I am having major problems with Vista(don't we all) and want to reinstall it, so it is once again usable. And I love Ubuntu and I don't want to reformat my whole drive because it took me quite a while to get it working right. 

So my question is will anything foresee ably bad happen with GRUB or Ubuntu if I were to reinstall Vista?

---

### Post by Metaleks on 2008-04-13
Don't quite know what you said near the end there, but AFAIK many people dual boot Vista and Ubuntu.  You shouldn't have any problems at all.

---

### Post by Irihapeti on 2008-04-13
As I understand it, Vista (or any version of Windows) has a nasty habit of messing up GRUB. Before you start, download and burn a copy of SuperGrubDisk. If you have that, it's fairly easy to fix.

---

### Post by Hendrixski on 2008-04-13
> **Metaleks said:**
> Don't quite know what you said near the end there, but AFAIK many people dual boot Vista and Ubuntu.  You shouldn't have any problems at all.

No, people have problems dual booting Vista all the time.  Microsoft made sure that it doesn't play nicely with anything.  There was even an article about it in this months Linux Journal.

I haven't used Windows in ages now.   Our office standardized on Ubuntu so none of my work computers have it, and I use Ubuntu at home... so... my advice is to forget Vista.

---

### Post by ryan22158 on 2008-04-13
> **Metaleks said:**
> Don't quite know what you said near the end there, but AFAIK many people dual boot Vista and Ubuntu.  You shouldn't have any problems at all.

To make it a little clearer. I am dual booting both Gutsy and Vista. and currently Vista is slowing dying and the only reason I keep it is because I paid for it. So, I want to fix Vista by reinstalling it. 

 I was wondering if I were to keep Gutsy intact and just boot vista and reinstall it would I have a problem with GRUB any thing a long the lines of booting into either Vista or Gutsy?

---

### Post by ryan22158 on 2008-04-13
> **Hendrixski said:**
> No, people have problems dual booting Vista all the time.  Microsoft made sure that it doesn't play nicely with anything.  There was even an article about it in this months Linux Journal.

I haven't used Windows in ages now.   Our office standardized on Ubuntu so none of my work computers have it, and I use Ubuntu at home... so... my advice is to forget Vista.

I try to forget my Vista problems every day. But then I notice that I bought a Zune and I can't sync it with anything but Windows. So I am stuck with it for now. I just hope something better comes out in the next release of windows.

I do really like Ubuntu it was just a pain to get everything work right. It is funny that I got an entire OS working before I could find a fix for something as easy as reinstalling "Windows Trusted Installer."

---

### Post by Irihapeti on 2008-04-13
I ran dual-boot Vista + Ubuntu 7.04 for a couple of months. I never reinstalled Vista, but I understand that doing so can cause problems.

In theory, if you reinstall Vista to its present partition, you should just need to boot into the SuperGrubDisk, choose the reinstall GRUB option (I don't remember offhand exactly which menu this is under) and everything should work.

Of course, if anything can go wrong, it eventually will. Partitions can get overwritten. So make sure you have a backup first of your Ubuntu partition. You can use partimage for this, which is part of the PartEd Magic and Gparted liveCDs. If you have another way of backing up partitions, then use those if you prefer.

Another option for booting, which I haven't used, is EasyBCD, which runs under Windows.

---

### Post by ryan22158 on 2008-04-13
> **Irihapeti said:**
> I ran dual-boot Vista + Ubuntu 7.04 for a couple of months. I never reinstalled Vista, but I understand that doing so can cause problems.

In theory, if you reinstall Vista to its present partition, you should just need to boot into the SuperGrubDisk, choose the reinstall GRUB option (I don't remember offhand exactly which menu this is under) and everything should work.

Of course, if anything can go wrong, it eventually will. Partitions can get overwritten. So make sure you have a backup first of your Ubuntu partition. You can use partimage for this, which is part of the PartEd Magic and Gparted liveCDs. If you have another way of backing up partitions, then use those if you prefer.

Another option for booting, which I haven't used, is EasyBCD, which runs under Windows.

Wow if only I knew about this last december.......Probably could of saved me a lot of time and pain. This looks like the exact program I needed to fix a GRUB problem I had then.

But this looks like it can at least fix things when they go wrong. 

Thanks

---

