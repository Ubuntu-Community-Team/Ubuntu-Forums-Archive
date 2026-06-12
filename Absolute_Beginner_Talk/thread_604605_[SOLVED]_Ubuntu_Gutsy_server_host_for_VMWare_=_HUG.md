---
title: "[SOLVED] Ubuntu Gutsy server host for VMWare = HUGE iowait"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by getut on 2007-11-06
There seems to be an issue with Gutsy server and vmware causing huge iowait performance losses with even mild disk activity.

[Here]("http://communities.vmware.com/thread/109318;jsessionid=58F8328F581BA29A4569A2742C4C76CA?tstart=0&start=0") and [here]("http://communities.vmware.com/thread/109891;jsessionid=BF39F56B4057E955F576CA2EC72F1E3C?tstart=15") are vmware threads that seems to be some of the first reports of this.

It seems to be an issue with the tickless kernel in gutsy but I have seen nowhere where someone has specifically proven that as the issue. It is only a theory at this point. But does anyone know more of this issue or know of a workaround to get performance back?

Someone mentioned running an older kernel in gutsy, but I have no idea how to do that. This doesn't seem to be an issue with Gutsy perse, it seems like more of a problem with any linux distro running 2.6.22 or higher kernel.

Someone please help me.

Edit: forgot to add my performance graph. Magenta bleeding down from the top is the iowait. This is a VERY lightly loaded VERY substantial server. 2 quad core procs and 32 GB of RAM with an 8 drive hardware RAID array (Perc 5/i)

[IMG]http://www.ngkceramics.com/iowait.jpg[/IMG]

---

### Post by getut on 2007-11-07
Well.. I didn't get any help on my question, but after one day of testing after changes I think I got it worked out.

Details of the problem... VMWare Server 1.0.4 running on an Ubuntu Gutsy Server host machine of very high spec. 2 quad core processors, 32GB of ram and 4TB of drive space on an 8 drive Perc 5/I hardware RAID controller, but yet disk performance was horrible. With even very light disk activity, the guest OS's would freeze for 30 seconds to 2 minutes at a time. While frozen even pinging the guests was either impossible or very high round trip times.

The fix... I did 3 things. It is entirely possible that any one of the 3 was the fix by themselves, but I am happy with the performance so I will not test any further.

1. I edited grub for the kernel option clock=pit
2. I edited grub for the kernel option nohz=off (this one supposedly disables tickless kernel)
3. I installed the vmware-any-any-update114 patch to my VMWare server and re-ran vmware-configure.pl

---

### Post by timcredible on 2007-11-07
i had tried running vmware player and it had horrible IO wait and the drive kept churning, i checked the .vmx file and it had 1.5GB of memory specified even though I only have 1GB on that machine, so i changed that to 512MB and it worked great.

---

### Post by getut on 2007-11-08
Wow.. it went for almost 2 days, but.... its baaa-aaaack.

After making the changes that I made, I was still seeing the iowait in the graphs but the virtual machines weren't freezing anymore but today the freezing just started up again.

When the iowait is high, the virtual machines will stop responding to anything, even pings. Once it catches up, everything works normally again.

Some more about my configuration in addition to what is above:
Perc 5/i RAID with 8 drives. sda (2 in a mirror), sdb (2 in a mirror), sdc (4 in a RAID 5).

I've been searching vmwares forums as well as here and Google for a couple of days now. Does anyone know what the problem could be?

---

### Post by getut on 2007-11-08
I forgot to mention. Pinging the host keeps going like normal when the VM's aren't responding.

Also, one more configuration item that may help. I am running ifenslave and bonding the NIC's before installing and configuring VMWare. So the bridged interface is actually to the bonded NIC.

---

### Post by getut on 2007-11-14
Ok.. this is looking less and less like a VMWare problem and more like a Gutsy problem. Here are the details I am still battling:

I have tried more performance tweaking on the VM's and have moved them around and the strangest thing of all is now occurring. As I said before I have the 8 disks broken up into 3 volumes that I had planned on allocating like this:

SDA 2 disks in RAID 1: Ubuntu / and swap and low disk throughput VM's in the default location.

SDB 2 disks in RAID 1: Dedicated to 2 higher throughput VM's

SDC 4 disks in RAID 5: Large storage area for user data. Secondary VMDK for one of the VM's on SDA.


What is the real kicker is the way the problem has evolved. I now have ALL VM's moved off of SDA and am still getting the huge iowait. SDA will hit hard every so often and all the VM's come to a screeching halt while it is going on and hardly respond to ping. The drive lights for both drives on SDA are lit solid. The host OS is also very slow to respond during that period.

What tool will allow me to find out what is hitting the disks on SDA so hard even when no VM is on there now? top and htop both show VMware as being the top processes, but I suspect that is due them hanging due to the iowait... not due to them directly.

It has been running for almost 48 hours with no VM's on SDA at all. Here are relevant graphs all showing same time period. Notice the processor graph showing the hit approximately once per hour. The extremely large iowait from 1:00AM till past 2:00AM is cron jobs running on one of the VM's. The actual volume the VM is on is not stressed that bad, most of that iowait came from SDA again even though the VM is not on that volume. SDA is obviously going berserk in relation to VMware activity, but somehow not directly because of it since there are now no VM's actually on that volume.

[IMG]http://www.ngkceramics.com/a.png[/IMG][IMG]http://www.ngkceramics.com/b.png[/IMG][IMG]http://www.ngkceramics.com/c.png[/IMG][IMG]http://www.ngkceramics.com/d.png[/IMG][IMG]http://www.ngkceramics.com/e.png[/IMG][IMG]http://www.ngkceramics.com/f.png[/IMG]

---

### Post by dtyler on 2007-11-15
I think I have got also the same problem on gutsy desktop. I'm using vmware player 2.0.2 with XP as guest.

---

### Post by getut on 2007-11-20
Well... I finally got this one resolved... but I wasn't able to do it with Gutsy 32 bit.

Take heed, the following is entirely speculative since I have neither the skills nor the time to fully prove the results that I had... so the errors/problems I encountered may have all been symptoms of the root problem as I suspect or they very well could have been different, unrelated issues that still nudged me in the right direction.

Above you see the system specs. A VERY substantial machine was running like a dog with Gutsy Server 32 bit. I went round and round trying every optimization I could find and was working with the guys on the vmware communities also (see thread here [http://communities.vmware.com/thread/111896?tstart=30](http://communities.vmware.com/thread/111896?tstart=30) ). I put noatime, nodiratime in the fstab, removed VMWare memory optimizations and still was getting horrendous io performance in the VM's. IO in the base OS seemed to work normally.

Due to known issues with linux kernel 2.6.22 (which is what Gutsy uses) tickless features I chalked it up to weird issues with that and finally after 3 weeks of pounding on it decided to downgrade to Feisty 32 bit. After downgrading the issue actually got worse and the whole machine would freeze when I brought the 3rd VM up, no matter what order they were brought up in. I noticed Feisty was only reporting 3GB of RAM out of the 32GB in the machine and it set off an ah-ha moment. I was thinking maybe Gutsy was having a similar problem only not quite so severe. It seemed Gutsy was reporting and using all 32GB but VMWare seemed to be behaving as if it were still only using 3GB and was caching wildly.

I finally decided to switch to Feisty 64 bit. And voila.. everything worked like it was supposed to. I wish I had time to try Gutsy 64 bit to see if I had the same good results, but I probably won't have the time to do it until I get an identical backup server just like this one to move the VM's over to. My users just don't have the patience for one more round of having the server down an entire day just so I can see if Gutsy 64 bit works just as well (and potentially have to move back to Feisty).

---

### Post by nemo136 on 2007-12-11
same problem, though smaller box, c2d 6300, 2Gb of Ram 2*raid1 320Go and 3 virtual machines with vmware server (ipcop firewall 1 linux, 1 windows XP) and the same iowait problem under feisty 32 bit, I don't want to reinstall. So , are there any news ?

---

### Post by wirelessmonkey on 2007-12-11
I had a very very similar problem on a gentoo server, 6TB, quad core 16G ram.  I found that for some reason RAM allocation was screwy with VMware server, and by decreasing the VM RAM by 64MB, Performance was restored 100%.

---

