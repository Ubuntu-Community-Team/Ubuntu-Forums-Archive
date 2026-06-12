---
title: "Linux &amp; Vista"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by bobbyshafter on 2007-02-14
My friend just bought a laptop,it has vista.

I convince him to give linux a try,he saw my wife pc with beryl .

My question is, will linux dual boot with vista.

Is there anyone who tried this...

---

### Post by tronica on 2007-02-14
give this a go

yes disregard this post, i didn't fully read this guide. Thanks for pointing that out highneko

---

### Post by highneko on 2007-02-14
Yep it's the same as Windows Xp. It works best with a second hdd. You're not gonna get him to resize are you? Because resizing has risks.

---

### Post by bobbyshafter on 2007-02-14
Thanks the laptop has only one drive.

Vista still use ntfs ? What about the MBR

I will install grub in the mbr.

---

### Post by i-am-me on 2007-02-14
> **highneko said:**
> You're not gonna get him to resize are you? Because resizing has risks.
There's a built in HD partitioner in Vista. [Go here]("http://lifehacker.com/software/vista/screenshot-tour--repartition-your-hard-drive-in-windows-vista-231613.php").
You can use it, and if you trust Windows software not to destroy itself, then go ahead and use it.

---

### Post by rirodz on 2007-02-14
I'm also new to LINUX (Ubuntu 6.06) and after running the LIVE CD was impressed. I have installed it by itself. I have since set it up Dual-Boot with XP Pro and runs great. As far as VISTA is concerned I have not tried, however, I plan to.
I have been brainstorming my approach. As you may know VISTA, the code on VISTA changed and the traditional NTLDR is no longer in place as it was under NT 5.
I was not satisfied with the suggestion provided for Dual-booting LINUX-XP Pro
So my approach was;
 80GB HD, NTFS Partition 37.2GB for XP
                LINUX ext3 33.2 GB for Ubuntu
                          swap 4GB

After installing XP, I used Acronis Disk Director to create the other partitions as mentioned above. Then installed Ubuntu. 
What I can seem to get to work is I have and 30GB HD which I format FAT32 and is slave.
When I boot I am given the option for which ever OS, no problem, however, XP can browse, read/write to the FAT 32 OK. Ubuntu can for whatever reason only read, won't write.
Do a search for Hiren's 7.5 or above, if you don't already have a copy. It is loaded with some seriously good utilities. I will be experimenting with the VISTA dual boot within the next week. I plan to take a similar approach. Nothing beats a try but a failure.

Would you happen to know a work around for this.

Thanks in advance for any help you can offer.

---

### Post by bobbyshafter on 2007-02-14
Ok i see what you mean .....[http://www.pro-networks.org/forum/about78184.html](http://www.pro-networks.org/forum/about78184.html)

What we need is a program like gpart that can resize vista .

Most converts hold on to ms untill they see the light

---

