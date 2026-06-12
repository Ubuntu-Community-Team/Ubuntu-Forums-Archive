---
title: "Need Help On Dual Booting Ubuntu"
date: 2005-08-31
forum: Absolute Beginner Talk
---

### Post by wootwoot on 2005-08-31
Okay, well i got my Ubuntu Linux in the mail yesterday and today ive been tryin to figure out how to get it working. Now the Live CD works just fine, but the install CD will just pop up tellin me how id like to view its pictures. And thats where im totally confused! Can anyone out there help me?

---

### Post by TristanMike on 2005-08-31
wootwoot, welcome to Ubuntu,

All you should need to do, is on boot up, enter the BIOS and change your "Boot Order" to boot from cd, this should probably look something like this: Floppy/Cd/Cd(or HD0). This should bring you to a splash screen as seen here..[http://mrbass.org/linux/ubuntu/install/](http://mrbass.org/linux/ubuntu/install/) 

If I'm way off the mark, sorry, If you have any other questions, feel free to ask.

---

### Post by cayamara on 2005-08-31
[QUOTE=wootwoot]... but the install CD will just pop up tellin me how id like to view its pictures.[/QUOTE]It kinda sounds like you try to load the CD from within Windows. Try booting from it.

---

### Post by byen on 2005-08-31
yes.as mentioned here...change your Bios settings to boot from CD (this can be done by pressing wither f2/f6/esc- depends on the system)
_ once this is done...restart your PC and the system boots the OS installer off the cd! 
good luck. If you are havin trouble feel free to ask.

---

### Post by Casethejoint on 2005-09-01
Quick, related question. Is [this article](https://wiki.ubuntu.com/WindowsDualBootHowTo) on the wiki still correct concerning 5.04? It seems quite unclear about whether the 5.04 partitioner will allow you to re-size NFTS partitions at the point of install.

---

### Post by TristanMike on 2005-09-01
[QUOTE=Casethejoint]Quick, related question. Is [this article](https://wiki.ubuntu.com/WindowsDualBootHowTo) on the wiki still correct concerning 5.04? It seems quite unclear about whether the 5.04 partitioner will allow you to re-size NFTS partitions at the point of install.[/QUOTE]Yes, I must admit that the wiki in this area is a little confusing. The Hoary installer will let you resize a partition, but it's manual with no pretty GUI so be sure you know what's going on there. With that said, you should always Defrag and Scan Disk before you partition. Also, since NO partitioner can guarentee 100% success, it's always smart to back up any important files just in case. This might help...[http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html)

Hope it's helpful.

---

### Post by Hobbsee on 2005-09-01
[QUOTE=TristanMike]This might help...[http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html)

Hope it's helpful.[/QUOTE]

That link is definetly helpful - i can tell you, after reinstalling ubuntu, then kubuntu about 3 times (dont ask, windows was being a pain in the neck)

That link really ought to go in the wiki...

Just be careful - if the partitioning doesnt look right, it probably isnt right.  You will know that it looks right - it wont say "free space" for one thing!

---

### Post by newbintu on 2005-09-02
Hi all, 

I'm very very new to unix and ubuntu stuff. I got this free unbuntu cd from a friend. So I was thinking why not trying something new??? But I am so clueless about unix/ubuntu and the process of installing dual operating system. So I'm doing some research now to make sure that I got it right before doing it and wiping all my hard drives.  :smile: 

So far most of the articles that I came across is about installing double OS on the same hard drive. I have two hard drives at the moment. Would be better if I installed Win XP and Ubuntu on 2 different drives? Or is it better to keep them all on one drive? Which one would be easier and secure to do?

Lastly, is installing the 2 OS on 2 different hard drives would be much different from installing them on the same drive?

Any suggestion would be appreciated  :grin:  thanks so much for the help!


The Clueless

---

### Post by Casethejoint on 2005-09-02
TristanMike, Hobbsee -- Thanks loads for the thoughts. That link is super useful. Perhaps a new FAQ on partitioning for Ubuntu might be a worthwhile thing for the doc_team to throw together, if only to reassure wannabe-converts that not all is lost because there's no GUI.

---

### Post by Hobbsee on 2005-09-02
[QUOTE=Casethejoint]TristanMike, Hobbsee -- Thanks loads for the thoughts. That link is super useful. Perhaps a new FAQ on partitioning for Ubuntu might be a worthwhile thing for the doc_team to throw together, if only to reassure wannabe-converts that not all is lost because there's no GUI.[/QUOTE]

Definetly...

I'd never thought i'd say this, but it doesnt matter if there's a GUI or not, as long as it's simple and intuitive.  And as long as it's all laid out nicely at the end so that you can see you've used all the space, which ubuntu installer does beautifully

To the poster above, if you have two hard drives, install ubuntu to your second hard drive - it stops the possibility of you wiping out your data on the first, and it gives each operating system more space than it would if you had them on the same drive...

Not sure if there's something in the wiki about it, or if it's in other threads, but i've seen a fair bit of information on how to dual boot with 2 hard drives - i'd check, but the pages are taking forever to load here...

---

### Post by newbintu on 2005-09-03
Hobbsee,

Thanks so much for the info...   ;-) If installing the 2 OS on two diff hd is better, I will definitely do that... I'll do some more research again to make sure I'm not blowing up my pc... hehehhehe...

But if you do find something good on it, I dont mind you posting it in here hehehhe  :-P

---

### Post by Casethejoint on 2005-09-03
> 
To the poster above, if you have two hard drives, install ubuntu to your second hard drive - it stops the possibility of you wiping out your data on the first, and it gives each operating system more space than it would if you had them on the same drive... 

How do you configure GRUB to handle this?

---

### Post by Hobbsee on 2005-09-03
argh!

There is an answer to this, and i'm sure i've seen it in a wiki somewhere!  Yet I cant see it in the ubuntu wiki, or anywhere else right now, which is odd, as i'm absolutely positive that it exists, or did as of a few months ago...

I'm assuming GRUB should autodetect the two operating systems, like it does when you have one hard disk containing two operating systems, but I cant confirm this - I dont have two hard drives with this laptop.  If someone else could provide input on this, that would be awesome!

I wouldnt worry about blowing up your system - i've tried many things with both windows and ubuntu installers (including turning off the computer in the middle of the install - not such a great idea, i suspect), but make sure you make a full backup first!  If you dont have a backup, you'll stuff it up, but if you do, it will be fine...it's Murphy's law, you know!

---

