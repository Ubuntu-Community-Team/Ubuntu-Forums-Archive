---
title: "dual boot"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by stone80 on 2006-06-12
hey guys, i just joined up because i have a few questions. i have been wanting to put linux on my home computer for a while and i finally downloaded the ubuntu livecd and i love it. but i need to keep windows xp on here because my wife uses it. i am a newbie when it comes to linux and still am pretty green when it comes to computers in general, but i'm quickly learning my way around. i have a few questions that i want to get straight before i do this. xp is currently installed and i am wanting to have a dual boot with xp/ubuntu. 

1. do i have to download and install a partition softare to partition my hard drive before installing ubuntu? if so, whats the best way to go about doing this?

2. if i have to partition my hard drive, do i just pop in the livecd and do an install of ubuntu?

3. anything else i should know before doing this?

---

### Post by shanepardue on 2006-06-12
ubuntu will guide you through the partition stage with it's built in partition manager. it's really easy if you know a little about partitions.

hope that helps!

---

### Post by stone80 on 2006-06-12
ok so all i have to do is put the livecd in and do an install? and the partition manager is built in?

---

### Post by shanepardue on 2006-06-12
that's right!

---

### Post by stone80 on 2006-06-12
thank you shane, man i have been reading everything i could find for the last 3 days and still was a little unsure about it.

---

### Post by shanepardue on 2006-06-12
no problem! just take the leap..you'll find it's a lot easier and less intimidating than you think!

---

### Post by EndGame on 2006-06-12
Just don't try it with Vista............you won't be a happy camper! Grub/Lilo will overwrite BCD/boot.mgr and if you want access to Vista you'll have to do a repair to Vista which will in turn overwrite Grub/Lilo..........:confused:

---

### Post by stone80 on 2006-06-13
ok i tried it, i clicked on the install icon but nothing ever happened. the cd was spinning, so i thought maybe it was just going to take a few minutes to get going, so i left it alone, came back and my computer was locked up. i had to turn off the power to it and it came back up fine, but i didn't try to run the livecd again, does anyone know why it didn't install when i clicked on it? i d/l the livecd straight from the ubuntu website.

---

### Post by renis on 2006-06-13
[QUOTE=stone80]
1. do i have to download and install a partition softare to partition my hard drive before installing ubuntu? if so, whats the best way to go about doing this?
[/QUOTE]
no

[QUOTE=stone80]
2. if i have to partition my hard drive, do i just pop in the livecd and do an install of ubuntu?
[/QUOTE]
kinda, it will ask you

[QUOTE=stone80]
3. anything else i should know before doing this?[/QUOTE]
back up data just in case

---

### Post by stone80 on 2006-06-13
how much ram should i need to run xp and ubuntu on the same system? maybe thats why my computer froze today when i tried to install ubuntu, because i only have 256 on there right now.

---

### Post by confused57 on 2006-06-13
[QUOTE=stone80]how much ram should i need to run xp and ubuntu on the same system? maybe thats why my computer froze today when i tried to install ubuntu, because i only have 256 on there right now.[/QUOTE]

You really need the Dapper alternate CD and do a text-install with 256 mb of ram.   I haven't tried, but maybe when you first start the LiveCD with the boot prompt,  press one of the help keys(F1,F2,etc) and see if there is an option to begin the install without actually booting up the LiveCD...I've read somewhere in the forum that someone pressed "Esc" after clicking on the install option on the LiveCD and was taken to a text-install option.  Your best bet would be to download the alternate CD and install from that, Dapper runs reasonably well with 256 mb ram; firefox is a little slow, but acceptable.  You might want to consider Xubuntu(alternate CD), it's a little lighter than Dapper.

---

### Post by stone80 on 2006-06-13
thanks, i'll try that. or maybe i should just upgrade my ram. it runs real slow on the livecd, i didn't have any trouble when i ran the livecd on my laptop, which has 512 mb of ram. which brings me to another question, i have a dell dimension computer and i was told that the only memory that works in dell computers is the memory that you have to buy from them, is this true?

---

### Post by confused57 on 2006-06-13
[QUOTE=stone80]thanks, i'll try that. or maybe i should just upgrade my ram. it runs real slow on the livecd, i didn't have any trouble when i ran the livecd on my laptop, which has 512 mb of ram. which brings me to another question, i have a dell dimension computer and i was told that the only memory that works in dell computers is the memory that you have to buy from them, is this true?[/QUOTE]
I have a Dell Dimension 4550, which has PC2100 DDR SDRAM; I don't think you'd have to buy dell-specific memory modules...I did a search and found some sites selling dell compatible memory for a decent price, if you want to be sure.
Dapper flies on my Dell(2 GHz), which has 512 mb ram...if I were you, I'd try installing with the alternate cd...your problem with your computer being slow is trying to run the live cd and installing at the same time, which probably requires 512 mb.  More memory would definitely help, but if your CPU is at least 1 GHz, Dapper should run pretty fast, even with 256 mb ram.

---

### Post by stone80 on 2006-06-13
thanks, i was told this, but knew it sounded odd. but i wouldn't put anything past dell to do something like that, so i didn't totally dismiss it, glad i know now. 

i'm going to d/l the alternate cd and give it a try, does the alternate cd install any differently than the livecd?

---

### Post by confused57 on 2006-06-13
[QUOTE=stone80]thanks, i was told this, but knew it sounded odd. but i wouldn't put anything past dell to do something like that, so i didn't totally dismiss it, glad i know now. 

i'm going to d/l the alternate cd and give it a try, does the alternate cd install any differently than the livecd?[/QUOTE]

It's a text-installer, easy to use; see this site for some excellent screenshots:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

It says for Breezy, but I've used it for Dapper...the screenshots should give you some idea of what to expect.

If you're dualbooting with Windows, be sure to defrag before installing Ubuntu & resizing the Windows partition...this is pretty important, because files get scattered all over the hard drive and the partitioner won't be able to resize if your drive is highly fragmented.

---

### Post by stone80 on 2006-06-13
cool, yeah i defragged my hd earlier today wheni was trying to install ubuntu. i did it about 3 times to make sure it would be ok, i've got plenty of room left on my hd, so i shouldn't have any problems with it.

---

### Post by xrchris on 2006-06-13
[QUOTE=stone80]how much ram should i need to run xp and ubuntu on the same system? maybe thats why my computer froze today when i tried to install ubuntu, because i only have 256 on there right now.[/QUOTE]

Are you booting from the Ubuntu LiveCD or are you loading Windows up and then trying to run the LiveCD?

---

### Post by stone80 on 2006-06-13
i am booting from the liveCD, allowing ubuntu to come up and then clicked on the install icon on the desktop when ubuntu had loaded.

---

### Post by gommle on 2006-06-13
I think minimum for dapper is 256, same with XP. XP is sluggish with so small amounts of ram tho, so go buy some ram. Two 512's is cheap.

---

### Post by Merlin Whitewolf on 2006-06-13
[QUOTE=stone80]hey guys, i just joined up because i have a few questions. i have been wanting to put linux on my home computer for a while and i finally downloaded the ubuntu livecd and i love it. but i need to keep windows xp on here because my wife uses it. i am a newbie when it comes to linux and still am pretty green when it comes to computers in general, but i'm quickly learning my way around. i have a few questions that i want to get straight before i do this. xp is currently installed and i am wanting to have a dual boot with xp/ubuntu. 

1. do i have to download and install a partition softare to partition my hard drive before installing ubuntu? if so, whats the best way to go about doing this?

2. if i have to partition my hard drive, do i just pop in the livecd and do an install of ubuntu?

3. anything else i should know before doing this?[/QUOTE]


To install from the live CD, you should start the installation as soon as the GUI comes up. If you start any other programs (firefox, for example), clicking on the install icon will cause the computer to 'freeze up'. 
I do not know why this happens. Maybe opening other applications causes them to take over too much of the memory.
I have 512 MB ram and a 3 GHz processor on an HP. The 'freeze up' happened to me, too. I restarted my computer and went straight to the install. Everything worked.  

Important -- don't forget to defrag your windows before starting. Windows program files can be all over your HD. Defraging will fix that and save you a major headache.

-Merlin (another new Linux user)

---

### Post by Merlin Whitewolf on 2006-06-13
Dell uses a generic type of ram card. You should be able to use any of the off the shelf type cards. Check the specs first, though. If the card was made for HP or Compaq, it most likely will not work for your Dell.

---

