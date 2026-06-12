---
title: "/dev/sda /dev/sdd??? for grub_install"
date: 2009-11-28
forum: Apple Hardware Users
---

### Post by EvansFive on 2009-11-28
On the iMac internal disk I have two partitions after Mac OS X.

/dev/sda3 linux-swap
/dev/sda4 /boot

Then on external firewire drive I have the following:
/dev/sdd2 /
/dev/sdd3 /usr
/dev/sdd4 /home

When I do GRUB2 grub_install which device do I install to??  I did choose /dev/sda and I am having a few problems that I cannot resolve or explain.

Should I do:

grub_install /dev/sdd (ie where the / parition lives)?

Is it safe to do this even though I originally did it to /dev/sda??

Please assist!

---

### Post by tom4everitt on 2009-11-29
In principle there are at least three places that you should be able to install grub to:

/dev/sda
/dev/sda4
/dev/sdd

There are no major arguments against installing grub to all these places, the worst that can happen is a cluttered rEFIt (or other boot) menu, as there will be a lot of (equivalent) boot options.

Did you install rEFIt? It usually makes it a lot easier to boot linux on your mac. Boot into OS X and [http://refit.sourceforge.net/](http://refit.sourceforge.net/)

Exactly what problems are you experiencing?

---

### Post by EvansFive on 2009-11-29
Thanks for your reply.

I do have rEFIt installed.

I went ahead and did grub_install /dev/sdd.

All seemed to be ok, until I rebooted.

It complained it was waiting for a file system!!

I booted the live cd and looked at the partitions using GPARTED.

My /dev/sdd4 (ie /home) did not show up as a ext4 partition...looks like it got clobbered somehow.

So.....I did another fresh install....and let it put grub2 on the default location...all is working again now...just got to reinstall and recover some databases.  Mac OS X even works as well...phew!

The original problems that I was having were:
1) getting no such device flash up before boot menu appeared
2) none of my grub menu resolution or splash image changes would stick

So in trying to solve a small problem I ended up with a much bigger problem...9.10 has caused me a lot of rework!!!

---

### Post by tom4everitt on 2009-11-30
Okay, cool!

About your grub menu changes not sticking, you're aware that you have to edit different files in grub2 than in grub? and that you always after editing have to run 

sudo update-grub?

If not, that's probably the cause...

---

### Post by EvansFive on 2009-11-30
I did do sudo update-grub but the changes would not stick...no change to resolution and splash image does not appear.

Even though update-grub said it found the image and I can see the resolution line in grub.cfg!!!

I think there are still many bugs with the beta GRUB2!!

---

