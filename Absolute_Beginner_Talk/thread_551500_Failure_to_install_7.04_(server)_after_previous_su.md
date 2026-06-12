---
title: "Failure to install 7.04 (server) after previous success"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by gobstopper on 2007-09-15
I have got my hands on a Dell Optiplex GX270 chassis and upgraded the RAM with a view to installing Ubuntu 7.04 server eddition and VMWare Server and then use it to run virtual machines to help me work from home and not have to rely so much on using my VPN to work with installations at the office.

I will admit to being a novice in these matters. I have a desktop installation of Feisty which I tinker with from time to time as well as XP and 2000 machines.

Last weekend I downloaded and installed 7.04 server edition. I was pleasantly pleased with the simplicity of the process after a little research on the Internet I had replaced the DHCP config with a static IP configuration and the correct IP address in resolv.conf so that I could connect the Unbuntu box to the Internet. After this I downloaded and installed Webmin and felt pretty pleased with myself. During the course of the week I tinkered with various things, got some things to work, broke others, but considered it all a learning process.

Today, I thought I take all of that learning and start from scratch with a nice fresh server installation. I followed the installation steps through and having specified my username credentials I sat back to watch the installation proceed.

Barely 2-3% into the base system installation task, I was presented with the following message:-

Warning: Failure trying to run: chroot /target mount -t proc proc /proc

Wondering if the presence of the existing partitions was having a negative influence, I repeated the process but re-created the partitions. Still the same.

I have even resorted to digging out an old DOS boot disk which I have used to completely remove all partitions from the disk, but the installation still fails at the same point.

I must confess to being quite bemused by this as the base installation the previous weekend completed so easily.

Tried putting the error message into Google (and the search box in these forums) but nothing obvious came back.

Can anyone shed any light on the likely cause of this problem and what I need to do to fix it?

Many Thanks.

---

### Post by nixclusive on 2007-09-15
looks pretty much like disc failure to me.. may the CD you are using got an error that wasn't there the last time. I mean CD's do get corrupted don't they? ...just a guess here. Maybe burning a new disc should solve your problem. :-)

---

### Post by gobstopper on 2007-09-15
Well, despite the fact that the CD hadn't moved between last weekend and today, you were absolutely right. I burned a fresh CD from the downloaded ISO and the installation was as trouble-free as before!

Thanks very much.

---

