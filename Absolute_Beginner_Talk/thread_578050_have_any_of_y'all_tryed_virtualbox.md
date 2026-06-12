---
title: "have any of y'all tryed virtualbox??"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by 001100 on 2007-10-16
Hello I was just wondering if any of yall have tryed virtual box?? I was wondering if I should try it here are my system specs.
++++++++++++++++++++++++++++++++++++++++++++++++
Intel P4 1.8ghz
512mb of ram
120GB hdd
128mb nvidia mx4k

---

### Post by jusmurph on 2007-10-16
Virtual Machines hit the ram the hardest because basically your spliting the amount of ram between each computer. Ie you would be running two machines on 256mb of RAM which will work, but is not somwthing that you will enjoy as your computer will be using the swap parition alot. I don't see why it won't work, but i would not say your hitting what i would recommend.

---

### Post by ~~Tito~~ on 2007-10-16
You would need at least a gig. I gave it 256 ram so I still have room for ubuntu, even though it still uses the cpu 100% it runs fine as it was with out it but you probably wont be able to get far with 512.

---

### Post by barkej on 2007-10-16
Virtualbox will work with 512MB but I would not expect great performance out of it. For best performance 1 or 2 GB of ram.

VB is a great program though. IMHO it's the best virtual machine prog for linux.

---

### Post by bromix on 2007-10-16
What is it that you are wanting to run VirtualBox for?  Just out of curiousity.

---

### Post by 001100 on 2007-10-16
windows 2k or xp, I just need to run some apps that won;t work with wine. Another question how would you creat a short cut with a root command??

---

### Post by bodhi.zazen on 2007-10-16
[http://doc.gwos.org/doku.php/doc:office:virtualbox](http://doc.gwos.org/doku.php/doc:office:virtualbox)

+1 on more ram ...

---

### Post by ~~Tito~~ on 2007-10-16
Hey take off smilies it screwed up the link.

---

### Post by bodhi.zazen on 2007-10-16
> **~~Tito~~ said:**
> Hey take off smilies it screwed up the link.

Thanks, I keep forgetting to do that :redface:

---

### Post by nikoPSK on 2007-10-16
I sthis good? I have vmware and I convert the .rpm to .deb with alien the install but i dont see entries in the apps menu. (version 6):(

also if i decide to screw vmware and go dual booting, is there a way that i could get my pc to auto boot ubuntu unless i tell it otherwise?

---

### Post by nikoPSK on 2007-10-16
also it doesn't ask me for the serial, Does it do this after?:)

---

### Post by 001100 on 2007-10-16
thx. I did get virtualbox and i got it to work. to launch it I had to go into termanial and type su VirtualBox but when I type virtual box I cannot boot a newly made vm. I have to use the root command. Is tere any wat to make some kind of shortcut for that command?

---

### Post by Orbital75 on 2007-10-16
I use Virtual Box and it works very well. As other have said VM's need a lot of RAM
You can get by with 512 but it's not going to be very fast at all. I myself have 1gig
and it seems to move along pretty smoothly. So my advice is if you have 1 gig or more
you'll be happy with the results.

---

### Post by 001100 on 2007-10-16
just google virtual box and download it its better than vmware. after install just goto termanial and type su virtualbox.

---

### Post by lazyart on 2007-10-16
You have to put yourself in the vboxusers group....** read the installation documentation** and you won't have to su or sudo.  I use VMWare on my 64 bit desktop, and virtual box on my 32 bit laptop.  I have no problems with either one.  I have a gig of memory on the laptop and 1.5 on the desk.

Just know that if you do a kernel upgrade (and one is scheduled in 2 days) it will break your VM and you will have to reconfigure it.  It's not hard (again, read the docs) but just be prepared for it!

---

### Post by bodhi.zazen on 2007-10-16
> **nikoPSK said:**
> I sthis good? I have vmware and I convert the .rpm to .deb with alien the install but i dont see entries in the apps menu. (version 6):(

also if i decide to screw vmware and go dual booting, is there a way that i could get my pc to auto boot ubuntu unless i tell it otherwise?

> **nikoPSK said:**
> also it doesn't ask me for the serial, Does it do this after?:)

That is not the best way to run vmware on Ubuntu.

[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

[http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto)

---

### Post by ~~Tito~~ on 2007-10-16
> **bodhi.zazen said:**
> Thanks, I keep forgetting to do that :redface:

Lol, When I got your pm's I thought I was in trouble XD.

---

### Post by nikoPSK on 2007-10-16
> **bodhi.zazen said:**
> That is not the best way to run vmware on Ubuntu.

[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

[http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto)

Gah! Did I just waste over 100$ So vmware server will work for emulating windows? And I want to be able for it to auto-start ubuntu if I dual boot:)

512 RAM
2.0 GHz processor :guitar:

---

### Post by bodhi.zazen on 2007-10-16
> **nikoPSK said:**
> Gah! Did I just waste over 100$ So vmware server will work for emulating windows? And I want to be able for it to auto-start ubuntu if I dual boot:)

512 RAM
2.0 GHz processor :guitar:

:rolleyes:

VMWare server is available at no cost, perhaps you have the upgraded version ?

---

### Post by nikoPSK on 2007-10-16
yes. :( I should be able to return it. I got it a week ago. XD I should give that a try then:lolflag:

---

### Post by akiratheoni on 2007-10-16
I just got Virtual Box today. I have to say, I'm really impressed. I was able to get QEMU to work and VMware, but Virtual Box was indeed the easiest way. I even got it connected to the Internet, and I can share files between Ubuntu and Windows (well, right now, only Ubuntu -> Windows, not the other way around.)

---

### Post by FredB on 2007-10-17
VBox is great. But it only misses one thing which makes me stays with VMWare server : no support for 64 bits OS as guests :(

---

