---
title: "Speed up Ubuntu"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by Victormd on 2008-03-01
I found this "how to speed up ubuntu" and though I might post it here so we can discuss/improve/explain. These steps seem very enticing but I don't know (or don't understand) how some of them might speed up ubuntu. Anyone up for an educational discussion?

1. Disable IPv6
Edit /etc/modprobe.d/aliases and change the line:

alias net-pf-10 ipv6
to
alias net-pf-10 off #ipv6

2. Run boot processes in parallel
Edit /etc/init.d/rc and change:

CONCURRENCY=none
to
CONCURRENCY=shell
UPDATE: This tweak does not work with Gutsy


3. Aliasing hostname to localhost
Modify /etc/hosts's first two line as follows:

127.0.0.1 localhost yourhost
127.0.1.1 yourhost

where yourhost, is your chosen hostname. This will fasten up applications load.

4. Preload
Preload is an adaptive readahead daemon. It monitors applications that users run, and by analyzing this data, predicts what applications users might run, and fetches those binaries and their dependencies into memory for faster startup times.

sudo apt-get install preload

5. Swappiness
Let's use swap less frequent. It will faster switching between applications.

sudo sysctl vm.swappiness=10

And edit /etc/sysctl.conf and add the line at the end of the file to set it automatically at boot time:

vm.swappiness=10

7. Profile grub
Grub cap profile your startup, it's a kind of index on file read at boottime, so after the first time (when it builds the index) it will access those files faster.
Edit /boot/grub/menu.lst and place "profile" at every line's end witch is starting with "kernel /vlminuz..."

UPDATE: remove if after the next boot.

8. Speed up your HDD
Install hdparm with

sudo apt-get install hdparm
and enable 32 bit IO and UDMA if it wasn't before with:
hdparm -c3 -d1 /dev/yourdevice
where /dev/yourdevice is your HDD.

And to make it persistent you also need to edit /etc/hdparm.conf, and make it run at every startup, so you have to enable the "Hard disk tuning (hdparm)" service with System->Administration->Services.

(The post was taken from [http://yoten.blogspot.com/2007/04/speed-up-ubuntu.html](http://yoten.blogspot.com/2007/04/speed-up-ubuntu.html))

---

### Post by Mud.Knee.Havoc on 2008-03-01
I've heard of a few of these (and have used the first), but I'd love to read what the community has to say about the pros and cons of each of these.

---

### Post by Victormd on 2008-03-01
do you know what IPv6 does?

---

### Post by Gepetto on 2008-03-01
[http://ubuntuforums.org/showpost.php?p=2355677&postcount=9](http://ubuntuforums.org/showpost.php?p=2355677&postcount=9)

Some interesting points.

---

### Post by Victormd on 2008-03-01
didn't see that... thanks!

---

### Post by Victormd on 2008-03-02
Since this is a speed up ubuntu thread, a question:
Why does ubuntu run smoother on:
Desktop: AMD Athlon XP64 2800+, GeForce FX52000 + 1Gb RAM + ATA HD
when compared to:
Laptop: AMD Turion 64X2 + Nvidia Go + 2Gb RAM + SATA HD???

I don't really understand this...

---

### Post by xeth_delta on 2008-03-02
> **Victormd said:**
> Since this is a speed up ubuntu thread, a question:
Why does ubuntu run smoother on:
Desktop: AMD Athlon XP64 2800+, GeForce FX52000 + 1Gb RAM + ATA HD
when compared to:
Laptop: AMD Turion 64X2 + Nvidia Go + 2Gb RAM + SATA HD???

I don't really understand this...

It depends. It what you mean is access / launch time for programs, it would most likely be due to the HDD. Laptop harddisks are, in most cases, slower than desktop ones.

Another possibility is graphics. Your laptop graphics card is with most probability much slower than the one you have in your dektop computer.

---

### Post by Tatty on 2008-03-02
> **Victormd said:**
> do you know what IPv6 does?

IPv6 is the new form of IP address which is being rolled out at the moment.  

Its been in the pipeline for ages, but it is finally being rolled out now - personaly i wouldnt disable IPv6 now as we are going to start seeing IPv6 IPs appearing soon, but its up to you.

---

### Post by selda on 2008-03-02
Using IPv6 slows down Opera web browser a lot. It's a good idea to disable it when you are using it.

---

### Post by Victormd on 2008-03-02
> **xeth_delta said:**
> It depends. It what you mean is access / launch time for programs, it would most likely be due to the HDD. Laptop harddisks are, in most cases, slower than desktop ones.

Another possibility is graphics. Your laptop graphics card is with most probability much slower than the one you have in your dektop computer.

Well, I'll give you the graphics card, MAYBE, my FX5200 has 256Mb while the Nvidia Go has 128Mb (shared). However, I can run Need for Speed Pro Street on the Laptop and not on the Desktop and that tells me that the graphics card for the laptop may be better and actually, I think it is but haven't seen any reviews to verify this.

As for the HD, well, both are 5400rpms but the Desktop is ATA and the laptop is SATA so I think the laptop wins again...

Overall, the laptop I'm comparing the desktop to is much better, dual core proc. more mem, an so on, so I don't understand why Ubuntu is slower...

---

### Post by xeth_delta on 2008-03-02
> **Victormd said:**
> Well, I'll give you the graphics card, MAYBE, my FX5200 has 256Mb while the Nvidia Go has 128Mb (shared). However, I can run Need for Speed Pro Street on the Laptop and not on the Desktop and that tells me that the graphics card for the laptop may be better and actually, I think it is but haven't seen any reviews to verify this.

As for the HD, well, both are 5400rpms but the Desktop is ATA and the laptop is SATA so I think the laptop wins again...

Overall, the laptop I'm comparing the desktop to is much better, dual core proc. more mem, an so on, so I don't understand why Ubuntu is slower...

Graphics card. Regular RAM is much (much!) slower than the memory you have on a graphics card.
HDD. They both may spin the discs at 5400 rpm, but the laptop platters in the HDD are smaller, hence the disc proper will have a smaller diameter. In that case, the tangential velocity of any point on the laptop disk will be lower than for points in a big part of the bigger HDD:
```
v_tan = r * omega
```
where v_tan=tangential velocity, r=radius, omega=angular velocity of the disc.

In the case of the smaller diameter platter, the reading device of the HDD has to wait longer for two equally distanced points (the chord that joins the points in any of the two HDD platters would be the same length).

The fact that one is SATA and the other is PATA would not matter much, since when accessing the data from the platters none of these disks will reach that maximim bandwith for any of the interfaces.

You can make a test, just be **very** careful with this command and don't use it for anything else unless you know what you are doing, since it could damage your data!

This will test transfer rates.
For your laptop:
```
sudo hdparm -Tt /dev/sda
```
for your desktop:
```
sudo hdparm -Tt /dev/hda
```

I hope I somehow managed be clear enough on what I wanted to explain.

[EDIT] Please do not be discouraged that some of the components on your laptop are slower on your new laptop. Practically most laptops will be slower than fast desktops (with the exceptions of some very heavy, big and difficult to transport dektop replacements, meant for games and graphic editing). Like most things, laptops represent a compromise, in this case, between performance and portability. Think about it, how easy would be for you to carry around a dektop?
I have a laptop, and am well aware of the limitations, but those limitations, for what I need, are outweighted by the portability I get.

---

### Post by Victormd on 2008-03-03
> **xeth_delta said:**
> 
```
v_tan = r * omega
```
where v_tan=tangential velosity, r=radius, omega=angular velocity of the disc.


Never really stopped to think about it that way... same angular velocity so the tangential velocity is directly proportional to the radius of the platter so the laptop drive is ~30% slower than the desktop drive...

---

### Post by xeth_delta on 2008-03-03
> **Victormd said:**
> Never really stopped to think about it that way... same angular velocity so the tangential velocity is directly proportional to the radius of the platter so the laptop drive is ~30% slower than the desktop drive...

Desktop HDDs are faster for the same angular velocity, by how much, I don't know, considering that the speed improvement will be visible for the data located in the outer regions of the disc, where the radius is longer than for a laptop HDD. Some of the speed will also depend on how data is organized and recorded on the disk, but the trend should persist, IMHO.
That is why even smaller HDDs, such as the ones found in some portable music players are even slower. This is also the case with the MacBook Air (for the HDD option instad of the solid state memory) and some other ultraportables using very small HDDs. They lose in speed, but win in portablility and a reduced weight.

---

### Post by Victormd on 2008-03-03
Yeah, the ~30% is for the velocity on the outside of the platter but the average would be something less.

---

### Post by ChameleonDave on 2008-03-11
> **Victormd said:**
> 

4. Preload
Preload is an adaptive readahead daemon. It monitors applications that users run, and by analyzing this data, predicts what applications users might run, and fetches those binaries and their dependencies into memory for faster startup times.

sudo apt-get install preload



I have preload installed, and I can see it in the system services in systemsettings, but it doesn't work.  In fact, although systemsettings says that it will be started at boot time, it always notes that it is not currently running.  There are other services marked to be started which are also never actually running.  What's up with that?

---

### Post by bobbob1016 on 2008-03-11
You can enable concurrency on Gutsy, as per skymera's post here, [http://ubuntuforums.org/showthread.php?t=611049&highlight=concurrency&page=2](http://ubuntuforums.org/showthread.php?t=611049&highlight=concurrency&page=2)
you just need press ALT+F2, and enter "gksu nautilus /etc/rc2.d" rename s12hal to s13hal
That will make HAL start after dbus, as it should.

---

### Post by agtownz on 2008-03-14
Doesn't do anything here, running 64-bit.

---

### Post by Duck2006 on 2008-03-14
Nice post mush try soon.

---

### Post by iansane on 2008-03-14
I know the original was posted a while back but for those who don't know, IPv6 is already an integrated part of Windows Vista too and it is actually in use some places from what I've heard so remember how to reinable it itf you disable it. You might need it one day soon to comunicate with others. IPv6 allows longer IP's like when in US phone numbers started requireing the area code too because we were running out of numbers. So be ready to remember numbers that look like mac addresses as if remembering an IP wasn't hard enough.

---

### Post by Mud.Knee.Havoc on 2008-03-15
Most people will never find it necessary to remember ip addresses.  That's what DNS is for.

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-03-15
> **xeth_delta said:**
> 
```
v_tan = r * omega
```
where v_tan=tangential velocity, r=radius, omega=angular velocity of the disc.

i looking on google now but a assumption of the hard drives angular velocity not changing.
which i think it doses to mantain the data rate.
meaning good physics just i think you made the rouge assumptions
so if the fastest the hard drive can spin is 7200 rpm then i think it slows down when it gets to the out side.

but i am probably wrong.... so was it an assumption or do you know this to be fact

---

### Post by VraiChevalier on 2008-03-16
> **Victormd said:**
> Since this is a speed up ubuntu thread, a question:
Why does ubuntu run smoother on:
Desktop: AMD Athlon XP64 2800+, GeForce FX52000 + 1Gb RAM + ATA HD
when compared to:
Laptop: AMD Turion 64X2 + Nvidia Go + 2Gb RAM + SATA HD???

I don't really understand this...

I had a similar question when running Ubuntu 7.10 on a Gateway notebook with an Athlon 64 X2 with 2 gigs RAM. I asked my local neighborhood Linux Geek about it and he said it was likely due to CPU scaling. Ubuntu throttles down the CPU to conserve power. You can adjust this after booting up but he said he had yet to figure out how to make the setting permanent after rebooting. Had to manually adjust it every time.

---

### Post by xeth_delta on 2008-03-16
> **<<joe>> said:**
> i looking on google now but a assumption of the hard drives angular velocity not changing.
which i think it doses to mantain the data rate.
meaning good physics just i think you made the rouge assumptions
so if the fastest the hard drive can spin is 7200 rpm then i think it slows down when it gets to the out side.

but i am probably wrong.... so was it an assumption or do you know this to be fact

AFAIK, the angular veolcity in the harddisk is constant while it is on and it is directly related to the number of revolutions per minute:
```
omega = 2 * pi * f
```
Where omega is angular velocity and f frequency. Here is physics link that will explain it better: [http://hyperphysics.phy-astr.gsu.edu/hbase/hframe.html](http://hyperphysics.phy-astr.gsu.edu/hbase/hframe.html)

The number of revolutions per minute being constant (Let's take 7200 RPM as an example) in two HDDs with different platter sizes, portions of the large disk that are placed further away from the center of rotation than the small disk's radious will certainly move faster.
This is, AFAIK, one of the reasons HDD with smaller platters have a lower read/write velocity.

The tangential velocity of a point in the edge of the platter of a laptop HDD will be
```
v_d = r_d * omega (1)
```
Take a point beyoud this radius at a distance r_2:
```
v_2 = r_2 * omega (2)
```
```
r_2 > r_d (3)
```
From (1), (2) and (3) you get
```
v_2 > v_d
```

---

### Post by xeth_delta on 2008-03-16
> **VraiChevalier said:**
> I had a similar question when running Ubuntu 7.10 on a Gateway notebook with an Athlon 64 X2 with 2 gigs RAM. I asked my local neighborhood Linux Geek about it and he said it was likely due to CPU scaling. Ubuntu throttles down the CPU to conserve power. You can adjust this after booting up but he said he had yet to figure out how to make the setting permanent after rebooting. Had to manually adjust it every time.

Laptop parts tend to sacrifice speed and size for portability. In the case of the OP, I suspect it had to do with the HDD (Being a laptop model and considering that neither it or the desktop model would be able to satureate the SATA or PATA interfaces), graphics card using regular shared RAM and not dedicated memory. Memory on graphics cards is much, much faster and use a dedicated bus, independent of the front side bus.

Scaling. The frequency on a scaling capable CPU will stay at a default lower level when processing power is not required but it scales up when needed. I do not believe this will have a very big impact on performance (maybe someone knows more on this and wants to shed some light) and in many cases today, even desktop CPUs scale the frequency to reduce power consumption and heat.

---

