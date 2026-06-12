---
title: "Unusal installation technique: Epic Fail"
date: 2008-03-04
forum: Arch and derivatives
---

### Post by Arthur Archnix on 2008-03-04
I have a pretty flexible partition scheme, two primary 128 MB and a 900MB swap, the rest is an extended with at the moment two partitions for Nixs, a shared /tmp and shared /data partition.

I also have a no cd's, and only a few dvd's, and no money to buy more, so I tried to install Arch using a net install disc extracted to my free 128MB boot partition. I edited grub on my /dev/sda1 boot partition and rebooted into the net installer. Installed normaly then rebooted into Ubuntu.

First problem: Because it's a shared /tmp partition arch creates a new partition and then Ubuntu doesn't have the correct permissions. Simply chowning it doesn't work. Fortunately, there's a workaround on the ubunty forums explaining how to set the correct ownership on tmp.

At this point I should have left well enough alone, but I moved the /arch/boot to the second 128 /boot partition, updated arch's fstab and booted into arch.

Everything worked fine. I ran pacman -Syu which oddly enough found updates. Apparently the net-install disk doesn't take down the latest packages. Or maybe I was just using an out of date mirror. Anyway, it updated the system, BUT, and here is where my system got hosed, it complained about there being no boot partition when creating the image. 

Since I knew I had a boot partition I ignored it, and now, I must start again from square one.

I thought I'd share this with you in case anyone is considering something similar. This time I'm just going to leave boot where it is on the /root partition, at least at until I find out where its getting it's information on partition layout if not from fstab.

---

### Post by Arthur Archnix on 2008-03-04
A'ight. Well, after everything I heard about Arch I just had to see for myself. So, I got it all going. Base install. Added gnome. Add the daemons to replicate all that useful behaviour like fam, hal, acpid networmanager.... basically what I found was that if I want the functionality of Ubuntu (and I'm not talking gui's here) then just use Ubuntu.

Ubuntu boots to about 150MB-180MB. After setting up arch so that it did the same things, it was a little more, but I probably coulda tweaked it down to the same without much trouble. Also, the speed was slightly faster on Arch. But only noticeable if I booted one then the other. 

On the other hand, if you don't really like using gnome or kde or xfce... if you like the idea of a rolling release...I could see the attraction. It took me all of five minutes to figure out where the config files were for everything. There is no mystery to that system. It's really something.

I got to say the irc channels give a real bad impression of Arch. They're pretty much always bashing Ubuntu and other "noob" distros. I had to tell myself I was going to try it in spite of the community. It's not surprising that they're developers are so overworked though. They don't exactly have a strong pr campaign going on with the user base. Who'd want to contribute to a project whose users tell visitors to the IRC to "screw off" and "go back to Ubuntu"? Don't get me wrong. A few people were helpful. But there's no moderation there to prevent abuse of "noobs".

Anyway, time to put hardy back on that partition and see about doing some bug reporting...

---

### Post by fwojciec on 2008-03-04
I don't really use irc so I have no real means of disputing or confirming your account, butit seems to me that you must have had a rather unusual experience there.  In my experience it's usually the recent adopters of Arch who bash other distros, people who had used Arch for a while usually know better.

Anyways, here is a thread that has been active on Arch forums as of late -- hopefully it helps to create a slightly better impression than the impression you got from the irc channel: [http://bbs.archlinux.org/viewtopic.php?id=44501]("http://bbs.archlinux.org/viewtopic.php?id=44501")

---

### Post by fwojciec on 2008-03-04
Oh, and if you (or anybody) needs to install Arch without using CDs in the future -- try this, for example: [http://bbs.archlinux.org/viewtopic.php?pid=283021]("http://bbs.archlinux.org/viewtopic.php?pid=283021")

---

### Post by Arthur Archnix on 2008-03-04
Yeah, no I certainly don't want to bash arch. Like I said, its simplicity was a thing of beauty. I can see the attraction for many people.

And I realize (though I should say it again) that four hours on the irc over the course of three days isn't really enough time to give a fair assessment of the "community".

Thanks for the links...

---

### Post by finferflu on 2008-03-04
The IRC community and the forum community are usually two separate entities. The forum community is much more friendly than the IRC community, but IRC is IRC, it's like a tendency of the people using that media. 

I think you haven't got a full grasp of Arch yet, because you only talked about simplicity and speed, while I think the most beautiful feature is ABS, the Arch Build System. With that you can easily build your own packages or reconfigure the ones you have installed. That is the apex of simplicity for me. 

And, by the way, you can install any Window Manager/Desktop Environment, there are sections in the wiki dedicated to setting them up.

---

### Post by mips on 2008-03-04
Stick to Ubuntu, Windows or whatever tickles your fancy. May the force be with you, even if it is on the dark side ;)

---

### Post by deepclutch on 2008-03-05
arch forum is fast in replies! :D though I am yet to try IRC channel of arch .
I dont think archlinux needs coreg33ks to maintain it!those who bash ubuntu or gnome are keeping away potential arch converts.
BTW,ABS -I am yet to try it.

---

