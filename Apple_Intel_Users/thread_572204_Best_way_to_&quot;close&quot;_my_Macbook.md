---
title: "Best way to &quot;close&quot; my Macbook"
date: 2007-10-10
forum: Apple Intel Users
---

### Post by dmber on 2007-10-10
Ok, so I'm used to just closing my laptop when it's not in use because it's almost always plugged in. When I open it with OS X, everything's all good.  When I open it with Ubuntu, it's really hot.

So, what is the best way for me to do this?  I don't want to shutdown all the way, but if that's really the best way, I suppose I can.

Suspend doesn't seem to work, I had to power all the way back up when I did that last night.  What about hibernate?

---

### Post by michiel.patrick on 2007-10-10
I believe that a lot of people with laptops are having this problem. I am hoping that with 7.10 that this problem will be addressed. I have this same problem with my laptop and others do to. i  just make sure that if am taking my laptop somewhere then i shut down if i am in ubuntu.

---

### Post by cyberdork33 on 2007-10-10
> **dmber said:**
> Ok, so I'm used to just closing my laptop when it's not in use because it's almost always plugged in. When I open it with OS X, everything's all good.  When I open it with Ubuntu, it's really hot.

So, what is the best way for me to do this?  I don't want to shutdown all the way, but if that's really the best way, I suppose I can.

Suspend doesn't seem to work, I had to power all the way back up when I did that last night.  What about hibernate?

Hibernate should work. It just stores everything in RAM to the swap partition, and shuts down. Upon turning it on again, if there is the needed data in swap, it boots your saved system.

You could probably write some scripts that alter fan speed, and turn things off when you close the lid using the acpi, but I have no idea how to go about doing what's needed for that.

---

### Post by Seq on 2007-10-10
> **michiel.patrick said:**
> I believe that a lot of people with laptops are having this problem. I am hoping that with 7.10 that this problem will be addressed. I have this same problem with my laptop and others do to. i  just make sure that if am taking my laptop somewhere then i shut down if i am in ubuntu.

I have a macbook Core Duo, and suspend works in Gutsy about 75% of the time -- 25% it does not, and I just open and close it again. I believe this is my fault as I am running some self-built packages and have probably broken something (as well as having some extra kernel modules) and I seem to remember it working fine when I had initially installed gutsy.

It is possible to get suspend/resume working on Feisty, though I can not remember what needs to be done (I think it was something like putting the proper exit code at the top of laptop-detect so 915resolution ran on resume)

Also note that Gutsy uses the 'intel' X11 driver that can do the proper modesetting voodoo (though seems to add a second or two to the resume time due to screen flickering, unfortunately). I have been running on Gutsy for several weeks and recommend updating to it upon release.

---

### Post by dmber on 2007-10-10
so when i hibernate, i should then hit the power button to get going again after opening my lid?

---

### Post by cyberdork33 on 2007-10-10
> **dmber said:**
> so when i hibernate, i should then hit the power button to get going again after opening my lid?
That's how it has always worked for me... It will look like you computer is booting up normally, but it will load the data in your swap partition to resume.

---

### Post by dmber on 2007-10-11
when i tried hibernating, it said something about not being able to use my swap.  then shut down.  if you want the exact error wordage, i can get it for you.

---

### Post by cyberdork33 on 2007-10-11
> **dmber said:**
> when i tried hibernating, it said something about not being able to use my swap.  then shut down.  if you want the exact error wordage, i can get it for you.
hehe, do you have a swap partition? Is it large enough to store the contents of your RAM?

---

### Post by dmber on 2007-10-11
i have 2 gigs of ram and a 512 mb swap.

---

### Post by dmber on 2007-10-11
i'm also wondering how the "powering back up" works with bootcamp.  i can't just hit the power button (from a shutdown) and walk away, or else it starts up in to OS X.  when i hibernate will it know to boot back up to ubuntu when i hit the power button?

---

### Post by tgalati4 on 2007-10-12
You need a 2.1 GB swap partition or else your suspend-to-RAM will not work.  A snapshot of your RAM gets written (byte-for-byte, no compression) to /swap.  Upon wakeup, if Linux sees a suspend file, it will read it back into RAM.  It looks like a cold boot, except instead of loading the kernel and userspace files it reloads the RAM.  

This way all of your Firefox tabs, music library, and any other apps will be open where they were left off.  This suspend system works for the most part, but some applications don't do well after a suspend.  Some laptops (like my Dell Inspiron 7500) will forget to wake up a trackpad, keypad, or wireless card.  This seems to be random and I haven't figured where to put additional wait states to fix these seemingly random problems.

---

### Post by ronocdh on 2007-10-12
> **dmber said:**
> i'm also wondering how the "powering back up" works with bootcamp.  i can't just hit the power button (from a shutdown) and walk away, or else it starts up in to OS X.  when i hibernate will it know to boot back up to ubuntu when i hit the power button?
Hibernating, as I think has been well covered in this thread already, does not boot your machine up "from a shutdown state." Then there really wouldn't be any difference between shutting down and hibernating.

Rather, hibernating writes the contents of RAM to the hard drive (which is why you need a sizable swap file), then shuts everything off, clearing the RAM. (It takes power to retain data in RAM.) Then the system listens for a wakeup call, which is usually given by pressing the power button. When it's pressed, the swap file is located, its contents loaded back into RAM, and the machine is up and running again.

You can create a swap file after the fact, so try making a 2.5GB one or so, if you have the space, and check whether hibernation works then.

---

### Post by dmber on 2007-10-12
thanks for all the great info guys.  

i can't resize my OS X paritition without having to reinstall OS X can i?  i've only got a 15 gig partition for Ubuntu, and I don't really feel like eating up another 2 gigs of that just so i can hibernate.

---

### Post by Seq on 2007-10-12
> **dmber said:**
> i'm also wondering how the "powering back up" works with bootcamp.  i can't just hit the power button (from a shutdown) and walk away, or else it starts up in to OS X.  when i hibernate will it know to boot back up to ubuntu when i hit the power button?

For those that run Ubuntu more than OS X, refit can switch around the default order. Just go to (I'm assuming you installed on your mac os x drive) "/efi/refit/refit.conf" and be sure the "legacyfirst" is not commented. This only works for two OSes. If you triple boot with windows or something, there is no way to change which of those shows up first.

---

### Post by vh1 on 2007-10-12
> **dmber said:**
> thanks for all the great info guys.  

i can't resize my OS X paritition without having to reinstall OS X can i?  i've only got a 15 gig partition for Ubuntu, and I don't really feel like eating up another 2 gigs of that just so i can hibernate.

you can, it's just a little tricky

first, backup. after that you'd have to disable journaling in OSX, then download a relatively new copy of parted (GParted livecd may also do the trick, but they are very hard to use on macbooks I find) and it will be able to do the resize

I'm considering doing this again to add a swap partition before I install gutsy (this macbook has 1GB of RAM and I figured "to hell with a swapfile!"), but I've already got 3 partitions plus the EFI. would it even be possible to add another at this point?

---

### Post by alephsmith on 2007-10-13
> then download a relatively new copy of parted

or you could use diskutil resizeVolume from OSX.

---

### Post by dmber on 2007-10-13
so what actually happens when i just close my lid?  would downloads continue and everything?  is ubuntu still running like normal, just with the laptop lid closed?

---

### Post by tgalati4 on 2007-10-14
It depends on what actions you have set in Power Management preferences.  If not set, then it won't do anything when the lid switch is detected.  So, in effect, the machine is running with the lid closed, which makes it run hot.  

Try setting different actions and note the behavior.

---

### Post by dmber on 2007-10-14
nice.  i actually accidentally discovered those settings last night by right-clicking on my battery thing in my top panel.  once i figure out how to steal 2 gigs from OS X to make a bigger swap, i'll use hibernate when i close my lid.

---

### Post by cyberdork33 on 2007-10-15
> **dmber said:**
> nice.  i actually accidentally discovered those settings last night by right-clicking on my battery thing in my top panel.  once i figure out how to steal 2 gigs from OS X to make a bigger swap, i'll use hibernate when i close my lid.
Just use Gparted. After you create the swap partition you will have to edit your fstab file to auto mount the swap partition.

---

### Post by cyberdork33 on 2007-10-15
> **vh1 said:**
> you can, it's just a little tricky

first, backup. after that you'd have to disable journaling in OSX, then download a relatively new copy of parted (GParted livecd may also do the trick, but they are very hard to use on macbooks I find) and it will be able to do the resize

I'm considering doing this again to add a swap partition before I install gutsy (this macbook has 1GB of RAM and I figured "to hell with a swapfile!"), but I've already got 3 partitions plus the EFI. would it even be possible to add another at this point?

You can add up to 256 partitions, just whether or not you can boot a legacy OS from anything > 4 is the issue. (Which you are not currently). Ubuntu can mount and use all the partitions on a GPT disk.

---

