---
title: "Powerbook G4 install &amp; wireless advice needed"
date: 2009-05-29
forum: Apple Hardware Users
---

### Post by outerspacerace on 2009-05-29
Hi all,

I'm quite used to dual booting ubuntu with Windows variants but now I'm considering setting up a dual boot using Jaunty on a Powerbook G4.

I've downloaded and booted into the PPC live CD as a test run, and mostly it's working fine, though I'm left with a few questions.

1. Can I use GParted to do all my resizing/partitioning of the Mac drive from the live CD just like I would for windows?

From a quick look it seems straight forward though I've read about others partitioning first from the Mac, disabling journaling and so forth... which I'd rather not mess about with. I'm much more at home using GParted.

2. Also, does yaboot install automatically?

I know with Grub you can specify under the advanced install options not to install it, is that neccessary? Or will the installer take care of all this automatically as I have the correct PPC live CD? For all I know Grub probably isn't even on the PPC live CD builds...

3. The live CD doesn't detect the wireless network in the house (the Mac does however). Is there anything special I need to do for that to work, or is it just a matter of finding my network details (it's been a while) and setting it up manually after the install?

Thanks in advance!

---

### Post by spiceminesofkessel on 2009-05-29
I have Ubuntu 9.04 installed on my PowerBook G4. Now, I didn't dual boot, so I can't answer your first question. Concerning your second question, I would say that it does automatically install, at least it did on mine, and I just did a default install. My wireless card works just fine. I did, however, have to do a little more than just install the proprietary driver. I chronicled my experience in a post on my blog, [here]("http://spiceminesofkessel.com/2009/05/21/reviving-a-powerbook-g4-with-ubuntu-9-04-ppc/").

I have done nothing but enjoy my PowerBook since installing Ubuntu on it. Good luck!

---

### Post by outerspacerace on 2009-05-30
Thanks so much!

I actually bookmarked your page last night though I must have only skimmed over it to miss the wireless section.... thanks again for that tip.

I'm also fairly convinced the bootloader will take care of itself now after further reading.

And I'm pretty confident that I can indeed partition the drives in GParted. I guess I'd just like some confirmation/advice from folks here as it's not my Mac to mess up!

Otherwise I'd just be trying it first hand!

---

### Post by tiresia on 2009-05-30
> **outerspacerace said:**
> 
1. Can I use GParted to do all my resizing/partitioning of the Mac drive from the live CD just like I would for windows?

Yes, you can resize (ONLY resize) HFS+ partition. [COLOR="Red"]But it is safer to make a back up of all your important data on MacOSX[/COLOR]

> 2. Also, does yaboot install automatically?

Yes. You have now just one Partition (let's say /dev/sda). After resizing and installing you will get other four partitions (choose the guided installation, the installer will make all the necessary partitions for you): an Apple Partition Map (actually you have it already), the Apple Bootstrap Partition (where yaboot will be installed), the Partition for the System (ext3 or ext4), the Swap Partition.
If you want to be able to exchange data between the two System, without disabling journaling the HFS+ Partition, it could be a good idea to make another Share partition (with HFS+ *not* journaled) - of course you can you instead an external HD

> 3. The live CD doesn't detect the wireless network in the house (the Mac does however). Is there anything special I need to do for that to work, or is it just a matter of finding my network details (it's been a while) and setting it up manually after the install?

I guess you got already an answer. You could try to install the necessary driver also while running the LiveCD, just to check if it works.

---

### Post by outerspacerace on 2009-05-30
Wow thanks Tiresia,

The data has already been backed up, I neglected to mention that earlier.

I do want to run ext4 if at all possible, so I can't really let the installer do it for me automatically in that case.

Is it hard to do a manual partition for apple?

Or rather what should I do differently than if I was doing a manual windows install? I'm quite handy at those now...

I will just take a gamble on the wireless drivers, they need a restart to work so that rules the live CD option out. That and I'm confident what spice said should more than likely work for me!

Thanks again.

---

### Post by tiresia on 2009-05-30
> **outerspacerace said:**
> 
I do want to run ext4 if at all possible, so I can't really let the installer do it for me automatically in that case.
Yes, it is a good idea

> Is it hard to do a manual partition for apple?

Or rather what should I do differently than if I was doing a manual windows install? I'm quite handy at those now...

Not really, to understand how yaboot works, you can have a look here.
[http://ubuntuforums.org/showthread.php?t=994882](http://ubuntuforums.org/showthread.php?t=994882)
Let us know, if you have still questions

---

### Post by spiceminesofkessel on 2009-05-30
> Is it hard to do a manual partition for apple?

As mentioned by tiresia, it's not; however, I did run into difficulties. It shouldn't be difficult, but for some reason, the partitioner was quite stubborn on my system. It would always try to assign the boot partition to either the /home, /usr/bin, or even the / mount point. It was rather bizarre. No matter what I told it to assign the boot partition to, it would always switch it to one of those three I mentioned. Frustrated, I just did the automatic partitioning and it worked like a charm. Hopefully, your system will act differently.

Let us know how it works for you.

---

### Post by outerspacerace on 2009-05-30
Thanks for the extra take on it.

I think I'll do an automatic install, the apple partitioning sounds a bit tough to pull off and I'll just wait for Karmic Koala to have ext4 by default I think.

The machine itself has more ram and I seem to recall it having a faster processor than yours too spice, so it'll be cool.

Even the live CD ran very well on it.

Will let you guys know how I go, thanks again.

---

### Post by outerspacerace on 2009-05-31
I'm pleased to say after almost a few hours resizing the OS X partition, I did a manual install and things are great so far.

The wireless driver was offered automatically and worked fine straight after a reboot.

Now I've just gotta see about enabling the open source ATI driver which apparently works ok, and editing yaboot so that OS X is still the default boot option.

I know I've seen instructions around somewhere... off to look now.

---

