---
title: "A few questions"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by shaan_l on 2007-04-05
Hey

I just installed Fesity Beta, and it's awesome! I've installed past versions and this one is by far the best release ever!

I have a few questions though, which I know once I've sorted out will have me 110% hooked on Ubuntu :) 

I'm using the following:

Ubuntu Feisty Beta on a P4 3.0Ghz, 512mb RAM and a 80Gb SATA drive. All the partitions are ReiserFS, except the swap drive. The partitions are as follows:

/boot    250mb
/swap   512mb
/root    1000mb
/home  the rest of the drive

1. My network connection shows that it is on 10Mb/s. Is that the same as the 100 in 10/100 cards?

2. Ubuntu is very good, however XP seemed a bit more quicker. Why would that be? I've done a few tweaks (like the IPv6 disable) which seemed to make it a little quicker, but you know, I want it flying ;) 

3. How can I edit the GRUB menu? I don't need to wait three second to boot, and also I only need it to boot the initial kernel.

4. There are a lot of updates in Synaptic. How do I know which ones I need and don't need?

Thanks for the help!

---

### Post by NikoC on 2007-04-05
3. open a terminal:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```

This will make a copy of your menu.lst file, in case anything goes wrong, retype the previous line but with filenames switched around. It will restore your original menu.lst file.

To edit, in a terminal:

```
sudo gedit /boot/grub/menu.lst
```

---

### Post by heimo on 2007-04-05
> **shaan_l said:**
> 4. There are a lot of updates in Synaptic. How do I know which ones I need and don't need?

As you know, Feisty is still under development (or beta) and there'll be huge number of updates. After it's released around April 19th, there'll be less and less updates. Usually I update couple times a week when using development versions. When using stable release, update as soon as possible, as those will be mainly security fixes.
[https://wiki.ubuntu.com/FeistyReleaseSchedule](https://wiki.ubuntu.com/FeistyReleaseSchedule)

---

### Post by freebird54 on 2007-04-05
Here is a way to change Grub without diving in TOO far.  

[http://ubuntuforums.org/showthread.php?t=228104](http://ubuntuforums.org/showthread.php?t=228104)

and here is for when you *DO* want to dive in further:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)


That should allow you to do what you want :)

---

### Post by jvc26 on 2007-04-05
In terms of need/don't need, at the moment due to the fact feisty is still in dev (as mentioned above) the odds are you need all of them. Its worth keeping all your stuff up to date, especially when feisty is still a dev release.
Il

---

### Post by seshomaru samma on 2007-04-05
> **shaan_l said:**
> 
2. Ubuntu is very good, however XP seemed a bit more quicker. Why would that be? I've done a few tweaks (like the IPv6 disable) which seemed to make it a little quicker, but you know, I want it flying ;) 



to get ubuntu flying replace the default window manager Gnome with IceWM or Fluxbox
Running IceWM with Rox is a good idea . see [this guide]("http://ubuntuforums.org/showthread.php?t=171203")

---

### Post by heimo on 2007-04-05
> **shaan_l said:**
> 
1. My network connection shows that it is on 10Mb/s. Is that the same as the 100 in 10/100 cards?


Yes. If you have just one computer and it's connected to internet through ADSL or similar speed connection, I wouldn't bother doing anything. But if you need it fixed, it's probably about autonegotiation failing (could be the network interface card [NIC] or the other end), you may be able to fix it by trying to force 100Mb/s full-duplex using these quite generic instructions:
[http://www.cyberciti.biz/faq/linux-change-the-speed-and-duplex-settings-of-an-ethernet-card/](http://www.cyberciti.biz/faq/linux-change-the-speed-and-duplex-settings-of-an-ethernet-card/)

I haven't tested these. [COLOR=Red]Warning[/COLOR]. This could cause your network connection to stop working temporarily. In that case, you need to set it back to 10Mb/s. To install ethtool and net-tools (if not already installed):
```
sudo aptitude install ethtool net-tools
```To get information of you NIC (try which one works):
> ethtool eth0
mii-tool eth0
Force 100Mb/s fullduplex (again, only mii-tool or ethtool):
```
sudo mii-tool -F 100baseTx-FD
sudo ethtool -s eth0 speed 100 duplex full

```To make these settings permanent, you need to put them in some config file, it might be /etc/network/interfaces, but I'm not sure and the syntax will be different from commands above.

---

### Post by shaan_l on 2007-04-05
thank you very much for all the replies! :cool: 

i really appreciate it

---

### Post by TheWizzard on 2007-04-05
> **shaan_l said:**
> 
2. Ubuntu is very good, however XP seemed a bit more quicker. Why would that be? I've done a few tweaks (like the IPv6 disable) which seemed to make it a little quicker, but you know, I want it flying ;) 


ubuntu should be much faster than xp. 
is your video card recognised and configured correctly? is hardware acceleration working? 
i don't know feisty, but in dapper you'd had to do some manual configuration for most cards. 
cheers

---

### Post by shaan_l on 2007-04-05
how do i check that?

---

### Post by TheWizzard on 2007-04-05
> **shaan_l said:**
> how do i check that?

[https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html](https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html)

Note: some things may be different in feisty!

---

### Post by shaan_l on 2007-04-06
ok I did everything and so far so good! running much better and getting close to the way I want it.

now I got another few questions.

1. I'm on a windows workgroup, not a domain. I've edited the smb.conf file with the workgroup name i'm on, testparm shows everything ok however when i try to restart samba i get this:

sudo /etc/init.d/samba restart
sudo: /etc/init.d/samba: command not found

I had a look in the init.d folder and I dont see anything about samba in there.

2. what program can i use to make xvids?

thanks!

---

