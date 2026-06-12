---
title: "How does Ubuntu manage hotplug/unplug events + LTSP Hotplug"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by narayan on 2007-05-31
Hi All,

First time ive needed to post, so please bare with me!

Here's my situation,

I have Ubuntu 7.04 (Great job BTW) Desktop installed and running as a tftp+NFS server for serving LTSP boot images.  The OS, tftp and LTSP all work great.  For those of you who are not up to speed the LTSP (Thin) Client sends out a Tailored DHCP request, in our case this is acknowledged by a Windows server, this points the client to the Ubuntu server from which it pulls down Network Bootstrap Image and boots into a fairly minimal linux environment.

One of the requirements in my organisation was to be able to ltsp to a mixed environment, both Linux and Windows, I have that bit working fine.  

Everything is working fine except hotplug on the clients.  I have seen LTSP's wiki on Local Device Access and it allows for auto mounting partitioned USB sticks, which in an ideal world containing only partitioned usb sticks would be fine, but not in our organisation.  

what I need to do is to find a way, a script, a daemon or something for automounting USB Sticks.  As it stands, when I plug the USB Stick into the thin client and do a dmesg I can see it being loaded (excuse my terminology!) to the device node /dev/sda1.  I can mount it as follows:

mkdir /Drives/USB
mount  -t vfat -o uid=0,gid=0 /dev/sda1 /Drives/USB

and then I can ls the contents of /Drives/USB and hey presto they are there and correct.

Brilliant, job solved! - I WISH!!!! 

And heres the big question, is there a daemon or a script that will run in the background all the time that will handle the hotplug event and do an automatic mount of the USB stick and similarly handle an unplug event, unmounting the stick appropriately.  If its any help im at kernel 2.6.21.1 level.  I can rebuild kernel if needs be, (I've already tried supermount but to no avail)

Sorry about the length of the post, I hope i was thorough enough to answer any questions people may have in advance.

thank you in advance!!!

---

