---
title: "What happens if I..."
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by SuperLuigi31 on 2007-01-06
Well, my household's main computer (we have 3 coms, but I'm using the good one) is using Windows XP, and I'm trying to migrate to Ubuntu. I burned myself a LiveCD and have tried it out, and liked it. I've heard that I can download a GNU/Linux operating system onto a machine with Windows without damaging the Windows platform. Can anyone tell me how to do this? I'm guessing that I won't be able to completely install Ubuntu unless this condition is met--my family would probably be pretty angry if I lost all the Windows stuff already on here.
](*,)

---

### Post by MkfIbK7a on 2007-01-06
what you do is to partittion the harddrvive when it asks you then you can dual boot between windows and ubuntu 
careful not to format the HD

---

### Post by Bachstelze on 2007-01-06
Yes, it's perfectly possible, with Linux or with any other OS. All you have to do is to resize the WIndows partition down, install Ubuntu in the free space it created, voilà :)

Keep in mind though that the "zero risk" doesn't exist so backup all valualble data before hand. Also, runing a defrag on the Windows partition is recommended.

---

### Post by aysiu on 2007-01-06
Even if you know what you're doing, there's only a 99% chance your Windows data will stay undamaged.

Since you don't know what you're doing, I'd say the chance probably lowers to something like 60 or 70%.

So **back up everything**. If you don't have a reliable way to back up and restore your entire Windows installation (not just the personal files) to *exactly* the way it was before, do not attempt a dual boot installation.

Once you have figured out how to back it up (Norton Ghost or some other restore method), then this guide should help you:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by SuperLuigi31 on 2007-01-06
Ummm... What exactly is a 'Hardrive Partition'? I',m afraid I've forgotten that context...

---

### Post by aysiu on 2007-01-06
> **SuperLuigi31 said:**
> Ummm... What exactly is a 'Hardrive Partition'? I',m afraid I've forgotten that context...
It's like you're divvying up your hard drive into little mini-hard drives.

If you want an analogy to real life, it's like taking one big room, throwing up a foam "wall" in the middle of it to make two rooms. It's still one big room in once sense, but practically speaking (in terms of privacy, space use, etc.) it's two rooms.

Same deal with the hard drive. When you look at the hard drive in your computer (i.e., if you physically open the computer case with a screwdriver), you'll see only one physical drive in existence. But for all practical purposes, you will appear to have two or three different drives (or, now, we're calling them *partitions*).

Windows and Ubuntu cannot be installed in the traditional sense to the same partition. They need to live on separate partitions.

Read more here:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by Cariboo1938 on 2007-01-06
I would say a very safe way to start your "migration trip" to Ubuntu would be to install a second Hard Drive. You could use it for Linux only and wouldn't have to touch your Windows installation at all.;)

---

### Post by aysiu on 2007-01-06
> **Cariboo1938 said:**
> I would say a very safe way to start your "migration trip" to Ubuntu would be to install a second Hard Drive. You could use it for Linux only and wouldn't have to touch your Windows installation at all.;)
I agree in principle, but it's possible that a beginner (I'm thinking back to when I first started using Ubuntu) might accidentally reformat the wrong drive.

It's **always** a good idea to back everything up first--whether you're planning a dual boot with a separate drive or a separate partition.

---

### Post by Cariboo1938 on 2007-01-06
> **aysiu said:**
> .....
It's **[SIZE="3"][COLOR="Magenta"]always[/COLOR][/SIZE]** a good idea to back everything up first--whether you're planning a dual boot with a separate drive or a separate partition.
Oh Yes...You are totally right, I 100% agree...Do a Back-Up first and make sure you saved all your stuff...

---

