---
title: "multi-boot Ubu+Kubu+XP"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by alphaniner on 2008-03-10
I'm planning on doing a multi-boot system with Ubuntu, Kubuntu, and XP.  I have done dual-boot Lin/Win setups before but never Lin/Lin, and that is where things get fuzzy.  I usually make separate partitions for /, /boot, and /home.  I know I can't share / and I don't plan to share /home but I'm not sure about /boot.  Actually I'm thinking I would need a different /boot, but I'm not sure how handle boot loading.  At the moment, this is what I am thinking:

Partitions:

1    Windows (existing)
2    Ubuntu /boot (existing, but reformat)
3    Kubuntu /boot
4    Extended
5    Ubuntu /
6    Ubuntu swap
7    Ubuntu /home
8    Kubuntu /
9    Kubuntu swap
10  Kubuntu /home

Windows and Ubuntu are already installed but I will need to wipe everything but partitions 1 & 2 and reformat partition 2 to set this up.  I copied my existing menu.lst to an ext3 partition on another drive that will remain untouched.  After partitioning, I'm going to reinstall Ubuntu without grub, then install Kubuntu with grub, then modify Kubuntu's menu.lst using my present menu.lst as a guide.

So, are there any holes in my Master Plan? :-k And what about the swap(s)?  Should I consolidate them into one large swap for share between the two?  I've read that sharing swap is a problem if you use the Suspend feature, but I have never used that.  Are there any other reasons not to share swap?  Thanks.

a9

---

### Post by sayakb on 2008-03-10
Why are you installing both Ubuntu and Kubuntu anyways? Why don't you just install Ubuntu with both gnome and KDE? INstall Ubuntu and in a terminal, type:

```
sudo apt-get install kubuntu-desktop
```

---

### Post by scragar on 2008-03-10
swap is universal, no need to make 2.

another thing I'd be concerned about is the number of partitions your drive can hold, most do 4(or similar), so I'm not sure if such a large number of partitions will actualy work.

---

### Post by sayakb on 2008-03-10
> **scragar said:**
> swap is universal, no need to make 2.

another thing I'd be concerned about is the number of partitions your drive can hold, most do 4(or similar), so I'm not sure if such a large number of partitions will actualy work.

If he is extending the partition table, he might create more than 4..

---

### Post by scragar on 2008-03-10
that causes serious problems if you want anything from said partitions to be available on windows though...

---

### Post by louieb on 2008-03-10
> **alphaniner said:**
> ..but I'm not sure about /boot.  Actually I'm thinking I would need a different /boot,
Sharing a /boot partition between two distros from personal experience is a bad idea.  Update-grub gets all confused come kernel update time. Your better off with a separate /boot partition for each distro. 
[IMG]http://louboldt.com/ptwocents.gif[/IMG] Unless you get grub error 18:  I think having /boot on its own partition is more trouble that its worth. 

When running two Linux distros on the same hard-drive the IPL code for one goes in the MBR and the IPL code for the other goes in the boot sector of its root partition. At least that is what I do.

The most trouble free way is to** chainload or the configfile** option of grub.    Herman has a lot of good info on how to do it here. [IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm")

Other that doing away with the separate /boot partitions
the only other thing is just create one swap partition.:KS IF you create two what you will find is both distros will find them both and use both of them.

---

### Post by alphaniner on 2008-03-10
> **alphaniner said:**
> 
Partitions:

1    Windows (existing)
2    Ubuntu /boot (existing, but reformat)
3    Kubuntu /boot
**4    Extended** ):P
5    Ubuntu /
6    Ubuntu swap
7    Ubuntu /home
8    Kubuntu /
9    Kubuntu swap
10  Kubuntu /home

Thanks for all the info, but to be perfectly blunt it doesn't help me much.  Although I admit I had no idea that windows had problems accessing logical partitions, it's not an issue, as all the logical partitions are for Linux use.  Anyway, can anyone tell me if I'm on the right track?

---

### Post by alphaniner on 2008-03-10
> **louieb said:**
> Sharing a /boot partition between two distros from personal experience is a bad idea.  Update-grub gets all confused come kernel update time. Your better off with a separate /boot partition for each distro. 
[IMG]http://louboldt.com/ptwocents.gif[/IMG] Unless you get grub error 18:  I think having /boot on its own partition is more trouble that its worth. 

When running two Linux distros on the same hard-drive the IPL code for one goes in the MBR and the IPL code for the other goes in the boot sector of its root partition. At least that is what I do.

The most trouble free way is to** chainload or the configfile** option of grub.    Herman has a lot of good info on how to do it here. [IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm")

Other that doing away with the separate /boot partitions
the only other thing is just create one swap partition.:KS IF you create two what you will find is both distros will find them both and use both of them.

Thanks for the info and linky, I missed your post earlier, as I was too busy being passively belligerent.. :oops:

---

### Post by louieb on 2008-03-10
> **alphaniner said:**
> ... I had no idea that windows had problems accessing logical partitions, it's not an issue, as all the logical partitions are for Linux use.  Anyway, can anyone tell me if I'm on the right track?

News to me too. I've used them on windows machines before without a problem. I have read that windows should be installed in a primary partition.   (have to do some extra work to install windows in a logical partition). 

Layout looks alright to me -  nice and flexible. Very similar to the way I have my desktop pc setup. (has Ubuntu Gutsy and Ubuntu Hardy alpha).   I have a seperate grub partition [http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_) and a shared data partition. But thats just me. No one perfect way to do it just ways that fit the way you work.

---

### Post by Rocket2DMn on 2008-03-10
> **LinuxIsInnovation said:**
> Why are you installing both Ubuntu and Kubuntu anyways? Why don't you just install Ubuntu with both gnome and KDE? INstall Ubuntu and in a terminal, type:

```
sudo apt-get install kubuntu-desktop
```

+1, Kubuntu is really just Ubuntu with KDE, and you can have both desktop environments installed.  You choose which session want from the login screen.  Then all you have to do is logout to switch between them.

> **scragar said:**
> swap is universal, no need to make 2.

another thing I'd be concerned about is the number of partitions your drive can hold, most do 4(or similar), so I'm not sure if such a large number of partitions will actualy work.

If the OP were to install 2 linux distros (not necessarily 2 *buntus), the swap CAN be shared, but 2 swaps would be needed if you ever wanted to hibernate one of them and use the other.

---

