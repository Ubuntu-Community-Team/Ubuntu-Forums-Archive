---
title: "Advice on partitioning"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by cmcb on 2008-03-13
Guys,

I have a 120gb drive in a vostro 1500 laptop. It came pre-installed with Vista. 

I have a ubuntu partition which is 10gb , a 2gb swap.

Vista is no longer booting, but that's not too much of an issue. That partition is 40gb. There's another 50gb partition which is spare. I plan to wipe that and join it with the 50gb partition = 90gb. Then I want to use this on the ubuntu OS as a D:\ drive for storing files etc. 

Can someone explain how to do this, please?

Cheers!

---

### Post by seshomaru samma on 2008-03-13
what you should do is run gparted
```
sudo gparted
```
its a graphical tool to edit and change partitions
after you format the vista partition as ext3 you need to mount it
[read here ]("http://www.psychocats.net/ubuntu/mountlinux")on how to mount linux partitions

---

### Post by handydan918 on 2008-03-13
Sure...just boot the live cd and run gparted. It's a nice graphical partitioner that makes the partitioning process very visual and intuitive. 
Post back if you get stuck.

edit: NOTE: gparted MUST be run from the live cd if you intend to manipulate ubuntu file systems! Moving partitions containing mounted file systems is generally catastrophic!

---

### Post by lemmy999 on 2008-03-13
Give yourself 10gB for root, 2 gig for swap and make /home whatever' s left. That way you can change distros, upgrade and not lose any settings, files etc

---

### Post by NorthernLights on 2008-03-13
> Then I want to use this on the ubuntu OS as a D:\ drive for storing files etc. 

That means using this partition as "/home" when using gparted. You won't see this partition as something separated like "D:\" in Windows, but all files in /home will go into that partition. As previous post said, when re-installing Linux, whatever distro, the files there will not be lost.

---

### Post by cmcb on 2008-03-18
hi guys thanks for the help

ive done this and can see the volume if i go to "computer". i cant change permissions though, its set to read only :confused:

also, if i try to run an xp install it doesnt recognise the drive. says tehre are no partitions. 

any ideas?

---

