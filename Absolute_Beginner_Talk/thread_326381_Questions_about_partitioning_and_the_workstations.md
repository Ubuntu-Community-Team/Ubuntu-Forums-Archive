---
title: "Questions about partitioning and the workstations"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by MasterofRidley on 2006-12-27
Hello to you all, I just have a few questions that I would like to get answered before I have to go work, but them getting answered at any time would be greatly appreciated.

First off, if I have something running in the workstation that I'm not using, will it be active? I've had the installation thing going for well over two hours and it's stuck on partitioning the HDD (I think).

Secondly, how long does partitioning the HDD take? I want to partition 4 GB (out of 5 that I know are free, on a 20 GB HDD) for Ubuntu.

So, if it is stuck, will cancelling the installation right now ruin my HDD?

Also, is it just me or does Firefox use an inordinate amount of resources when I open a new tab? I only have 256 MB of ram, so my paging file gets overused I guess. I have yet to install any software, but I think the first will be Opera, if that works better on Ubuntu than Firefox. I don't much care for extensions.

So far, I've really liked the experience, and I love the organization it comes with. I'm definitely switching to a Linux distro completely when I move (so I don't have my family hounding me for "messing up" the computer), so I can avoid upgrading to Vista. Can Ubuntu kind of serve as a way to work up to less user friendly distros? Thanks for any answers, and sorry if I asked any questions that can be solved otherwise.

---

### Post by jonathan.lees on 2006-12-27
> if I have something running in the workstation that I'm not using, will it be active?

All programs remain active until you close them or they may have some feature that puts them to sleep when not in use.

> I've had the installation thing going for well over two hours and it's stuck on partitioning the HDD (I think).

The partioning and formatting of 4GB should only take a few minutes, if you cancel it should'nt ruin the disk, what does the display say?

> 
Also, is it just me or does Firefox use an inordinate amount of resources when I open a new tab?  

Firefox certainly has memory leaks, you can use the system monitor to see how much RAM it's using, with only 256mb ram you'd be better of using a different browser.

---

### Post by pseudonym on 2006-12-27
> **MasterofRidley said:**
> First off, if I have something running in the workstation that I'm not using, will it be active? I've had the installation thing going for well over two hours and it's stuck on partitioning the HDD (I think).

Were you using the graphical installer? If your installation is hanging, I'd ctrl+alt+del (or reset if you have to) and start over with the text-based installer. It's a little more work but is much less prone to stalling.

> **MasterofRidley said:**
> Secondly, how long does partitioning the HDD take? I want to partition 4 GB (out of 5 that I know are free, on a 20 GB HDD) for Ubuntu.
Once you tell the installer to start, it shouldn't take more than a few seconds, even on an older machine.

> **MasterofRidley said:**
> So, if it is stuck, will cancelling the installation right now ruin my HDD?
I shouldn't think so. It might be a good idea to boot up a live cd first and wipe any partitions on it with the 'cfdisk /dev/hd*' command, so you end up with free, unallocated space again.

> **MasterofRidley said:**
> Also, is it just me or does Firefox use an inordinate amount of resources when I open a new tab? I only have 256 MB of ram, so my paging file gets overused I guess. I have yet to install any software, but I think the first will be Opera, if that works better on Ubuntu than Firefox. I don't much care for extensions.
If the page you loaded had flash in it, and you've got say, a PII or an early P3, it could slow down your system quite a lot. One useful extension is 'flashblock', which allows you to choose whether you want to view flash content.

I don't know anything about opera (neither the browser nor the musical genre :) ).

> **MasterofRidley said:**
> So far, I've really liked the experience, and I love the organization it comes with. I'm definitely switching to a Linux distro completely when I move (so I don't have my family hounding me for "messing up" the computer), so I can avoid upgrading to Vista. Can Ubuntu kind of serve as a way to work up to less user friendly distros? Thanks for any answers, and sorry if I asked any questions that can be solved otherwise.
Ubuntu is a good starter distro. It helped me work my way up to using Debian. But I recently came back to Ubuntu, not least because of the support available from the community. I also found the faster release cycle and generally more recent software more appealling, too.

all the best in your quest to avoid vista, anyway. you've definitely made a good start :)

---

### Post by dwblas on 2006-12-27
I use Opera and Firefox.  I use Opera more often because I don't have all of the plugins installed on it and so avoid a lot of the negative side of the net.  IMHO a web browser is a web browser and they are both pretty similiar.

---

