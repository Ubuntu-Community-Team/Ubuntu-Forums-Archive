---
title: "some VMWARE related questions ...."
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by wolfmaniac on 2006-07-08
please answer my follwing questions..

0. how i install vmware
1. how i install BSD on vmware
2. can i install xp along with bsd
3. is vmware resoursce hungry
4  will xp on vmware be prone to virus.

thanx!!

---

### Post by maskd on 2006-07-08
0: I've seen the install and it's fairly easy, its a perl script that installs everything for you.

1: you can install bsd like you would on a normal computer, using an iso or cd in the physical cd rom.

2: you can make severel "virtual machines", so bsd and xp would be installed on "different machines"

3: vmware on my computer doesnt seem to take up much resources, i have 1gb of ram and allocating 256mb of ram to it seems fine.

4: the xp install will be prone to viruses if you give it network access, it will be susceptable to viruses as if it were a real machine, but luckily if your computer gets too screwed up you can simply reinstall it easily. anything that happens to the virtual machine wont affect the host machine though.

---

### Post by cjm5229 on 2006-07-08
0 [http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)
1 After you have installed VMware Server you will find a button to create a vitual machine. you will find BSD under "other". just follow the instructions.
2 The only limit to how many virtual machines you can put in is the size of your HDD, each VM will use about 8-15 Gb's of HDD space.
3 it will limit the ram use to no more than 3/4 of your ram.
4 yes, it will be just like a real XP partition.

---

### Post by FredB on 2006-07-08
About ram limit : 50% is really the best. On my 1 Gb fitted computer, I don't use more than 512 Mb for a virtual machine.

And for size : try using dynamically growing partition. They save space ;)

---

