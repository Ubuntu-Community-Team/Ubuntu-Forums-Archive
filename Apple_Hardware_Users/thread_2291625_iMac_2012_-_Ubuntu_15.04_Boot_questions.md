---
title: "iMac 2012 - Ubuntu 15.04 Boot questions"
date: 2015-08-21
forum: Apple Hardware Users
---

### Post by luciano.x on 2015-08-21
Hi. Is it possible to install Ubuntu dual boot w/ OS X without overwriting the default rEFInd?

Here is how I did it:

Install rEFInd under OS X
Partition from disk utility under OS X
Boot from USB via rEFInd
[I]Install wizard took several minutes but did not detected OS X
[/I]Create 3 partitions using that free space created with disk utility
swap, / and /home
Install boot manager at /dev/sda5 mount point /[B] (so I expect to boot onto it later using rEFInd)
[/B]Everything went OK but...

rEFInd didn't showed up anymore. No grub, it boots into Ubuntu (insecure mode).
Reinstalled rEFInd but this time under Ubuntu. Actually rEFInd was there but not set as default. Anyways problem solved so now I have rEFInd menu again.[B]

Again: how can I install Ubuntu in order to keep rEFInd in place?[/B]

---

### Post by awamunro on 2015-08-24
It appears that grub overrides the rEFind as it seems to happen when here is a grub update in ubuntu. Don't know why.
Booting with cmd+R gets into Mac OS recovery and you can then reset the default disk to Mac.
HTH

---

### Post by crystalocean on 2015-09-01
Hi luciano.x,

> ** Again: how can I install Ubuntu in order to keep rEFInd in place?** 		

Here is one option (if I understand your question correctly):

Install rEFInd to its *own* partition.

Then in system preferences>startup disk, select the rEFInd partition as the startup disk.

Now, once you install Ubuntu, your mac may, in fact, bypass the rEFInd boot menu and go straight into Ubuntu however that's okay.

Once in Ubuntu, open up the terminal and run:

```
sudo efibootmgr
```

If terminal says it can't find efibootmgr then run:

```
sudo apt-get install efibootmgr
```

Now, once again, run:

```
sudo efibootmgr
```

You will have an order in which Mac OS X is *not *first, and that is what you need to change.

Take an example where we assume this is your configuration seen from the output of the previous command:

Current: 0000
Order: 0000,0080

...
Ubuntu: 0000
Mac OS X: 0080
...

In this example, you would need to run:

```
sudo efibootmgr -o 0080,0000
```

Then, once you reboot your machine, it should boot into either the rEFInd boot menu *or *OS X.

If it boots into OS X, repeat:

> Then in system preferences>startup disk, select the rEFInd partition as the startup disk.

Please report back with any questions!

I hope this answers your question and **good luck** :D

---

### Post by luciano.x on 2015-09-01
Thank you awamunro and crystalocean!

---

