---
title: "Installing Ububtu 7.04"
date: 2007-05-10
forum: Apple PPC Users
---

### Post by radi0head on 2007-05-10
Hello, I'm new on the Linux world, so I would like to try this new version of Ubuntu on my Mac. I've got a 15' PowerBook G4 1.33 Ghz model with Mac OS X 10.4.9. I downloaded the installation CD, and I played around with it and loved the wonderfull enviroment (and the fully working Desktop Effects ;) ). Then I decided that I want to install it, but I'm afraid that it would erase my entire disk information on the install procedure...

I created an unformatted partition of 5Gb to install it, but I don't know how to "tell" Ubunbtu to install the OS *ONLY* in that partition.

I would like to know if the installation application automatically creates a way to dual boot my Mac (with Mac OS X and Ubuntu).

Thank you!

Best regards

---

### Post by cybervato on 2007-05-10
When you install 7.04 from the CD it will not wipe out your OSX partition.
But to be on the safe side backup any important data in OSX that you do not want to loose.

The Ubuntu 7.04 install will prompt you for information that will result in 7.04 being installed onto the 5 gb partition that you have set aside for Ubuntu 7.04.
The install will also install and configure yaboot which is the boot loader that Ubuntu utilizes for dual booting both Ubuntu and OSX.

When installing Ubuntu 7.04 simply run the installer located on the desktop on the Ubuntu 7.04 live CD.
When you are prompted to configure the Ubuntu partition select manual configuration.
A screen will display showing all drive partitions on your PB.
The partition manager will ask that you configure both a root or / partition where Ubuntu will boot from and a swap partition.
Make sure you have also set aside a 500 mb swap partiton from the 5 gb that you set aside for Ubuntu.
Once you configure the partitions that Ubuntu will install on the installer will then continue it's installation of Ubuntu 7.04

When all is complete you will be able to dual boot Ubuntu 7.04 and OSX.

When your PB reboots you should receive a yaboot menu during booting that allows you to select either x to boot into  OSX or l to boot into Ubuntu.

If you do not make a selection yaboot will automatically boot into Ubuntu.

You can change the default  OS to OSX you can easily modify the yaboot.conf located in /etc and add the following to the yaboot.conf file.
defaultos=macosx

The ubuntu 7.04 install is pretty straight forward you shouldn't have any problems installing on your PB.

Hope it works for you

--Art

---

### Post by stmiller on 2007-05-10
Yes the installer by default looks for free, unformatted space. It doesn't want to wipe anything out, or erase pre-existing partitions unless you force it to.

---

### Post by radi0head on 2007-05-10
Hi!

Thank you very much! The installation was smooth and clear, Ubuntu 7.04 and Mac OS X 10.4.9 living happy together!

Now my fight is another one... configuring my wireless network at home. Let's see if I can make it :rolleyes: 

Best regards!

---

### Post by tx_sumo on 2007-05-25
Ever have any luck with getting wireless to work?  That's the only thing that's keeping me from going linux full time.

---

### Post by stmiller on 2007-05-25
> **tx_sumo said:**
> Ever have any luck with getting wireless to work?  That's the only thing that's keeping me from going linux full time.

Read the PPCFAQs at the link below. Wireless works fine now with the airport and airport extreme cards.

---

### Post by AlphaMack on 2007-05-26
1.  Enable universe repo.

2.  Install bcm43xx-fwcutter.

3.  Agree to extracting/installing firmware.

4.  Reboot.

---

### Post by EuroCity on 2007-05-28
BTW, talking about partitions, it would also be possible to make only one **/** (root) partition and subsequently create a swapfile, thus making the complication of a separate swap partition useless: essentially, the same thing that Windows and Mac OS X do (they use swapfiles instead of partitions).

For example, to create a 1 GB swapfile, on could do this in a Terminal, immediately after having installed Ubuntu on a single root partition:

```
sudo dd if=/dev/zero of=/swap bs=1024 count=1048576
```

... and then:

```
sudo mkswap /swap
```

```
sudo swapon /swap
```

... and finally edit */etc/fstab*, adding this line:

```
/swap swap swap defaults 0 0
```

- and voilà, Linux behaves (well, almost...) like Windows and Mac OS X on the swapping front.

Just a possible option, nothing more...

---

