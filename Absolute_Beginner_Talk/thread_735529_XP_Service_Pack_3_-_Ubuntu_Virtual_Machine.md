---
title: "XP Service Pack 3 - Ubuntu Virtual Machine"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by snake01 on 2008-03-25
Hi everybody! Im totally new to Linux. After years of pain with Windows
I have finally decided to switch. However, the switch I want to make is gradual until I am totally comfortable with Linux as my main and hopefully only OS. What is the best way to install it on my laptop, as a virtual machine or as dual boot? Could somebody let me know the pros and cons of each one? Also (if this can be possible), how can I install Ubuntu on the machine if it is already running XP?

Thanks! Im really looking forward to joining this community and benefit from from the knowledge you guys share!

---

### Post by Paqman on 2008-03-25
Hi, welcome to the forum.

Virtualisation is a good option for trying Ubuntu, although the easiest is of course to simply boot up the LiveCD. There's also Wubi, but i've not used that so can't really comment.

You can get VMWare Server for Windows (it's free). Then just create a new virtual machine, boot up the LiveCD and install it. You'll need plenty of RAM, and even then you'll still suffer a performance hit. VM's also don't have 3D acceleration, so you won't get the nice desktop effects.

Setting up a proper dual-boot is actually pretty easy though, and is certainly the best way to see what Ubuntu can do.

---

### Post by boboyo4 on 2008-03-25
i am dual booting

i recommend you to dual boot if you dont have alot of RAM. if u do, just do whatever you want.
i got XP "virtually" and i am dual-booting whit vista

---

### Post by ajgreeny on 2008-03-25
Without doubt the beat way is to boot the live CD and if all is OK go for a dual boot.  Virtualisation is a bit slower if you have a slower or older machine with a relatively small amount of RAM, and it will still not give you all the advantages of an install as your peripherals will not all work as they do on a proper installed system.
Do it and you may quickly find that windows is hardly booted.  I stall have it on my machine but its partitio size has got smaller and smaller with every new version of ubuntu untill it just sits there and is never used.  Others in the household need it occasionally, so it has to stay, but for me it's Ubuntu all the way

---

### Post by snake01 on 2008-03-25
Hey thanks everybody for answering so quickly! 
Just another little doubt from a newbie. Do I have to reformat my XP Machine and repartition or there is a way to install it (native) without having to reformat and repartition first? 

Thanks again

---

### Post by ajgreeny on 2008-03-25
You will have to just make room for ubuntu by shrinking your XP partition.  Use the ubuntu live CD Partition Editor to do it and then install ubuntu on the unallocated space.

See the info here as it is very useful andf has lots of tips etc.
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Tamjay on 2008-03-25
I duel booted when i first started my conversion from windoze to linux. the install wen't very easy and as long as i took it slow and read exaclty what it was doing, never had a problem with windoze disipearing or anything crazy like that. BUT there was no Wubi at the time. i tried it with Hardy Heron alpha 6 and i thought it was an amazing alternative to the duel boot for someone wanting to see what it's all about.  it's seems especially useful for a windoze user because if you decide you don't want it or want to duel boot, then it uninstalls from your windows just like any other program.  wish they had it around when i first started =p.  but bare in mind,  it's only available on the beta hardy (read all warnings if you decide to go this route), which won't be declared stable till april. 

as a side note,  alpha 6's wubi (i386) went off without a hitch on my amd64.  my .iso of hardy beta 64bit didn't autostart in my vista (not sure if it was something to do with my vista being 32bit or not).  but just throwing it out there as an option.  good luck and have fun, i'm on my windoze maybe 5% of my computing time now adays =).

---

### Post by snake01 on 2008-03-25
Awesome. Ill try the live cd ( already downloaded the image)and make space on the xp machine and post results as soon as  do it (probably at the end of the week). thanks again

Also and pardon my ignorance, what is Wubi?

---

### Post by Shazaam on 2008-03-25
Be sure to defragment Windows in "Safe Mode" (disables the Windows swap file) before you resize it. Once it is resized boot into Windows normally; it will want to do an automatic chkdisk. Let it run.

---

### Post by ByteJuggler on 2008-03-25
> **snake01 said:**
> Awesome. Ill try the live cd ( already downloaded the image)and make space on the xp machine and post results as soon as  do it (probably at the end of the week). thanks again

Also and pardon my ignorance, what is Wubi?

WUBI is an option for you.  It is an installer that will dual-boot install Ubuntu as a set of "disk" files on you Windows partition, which mean you sidestep even having to repartition your disk at all.  But, the normal LiveCD install should also be fine.  Wubi is [here]("http://wubi-installer.org/").

Aside: The next release of Ubuntu (codename Hardy Heron), due in about a month, will offer Wubi as an "official" installation choice.

---

