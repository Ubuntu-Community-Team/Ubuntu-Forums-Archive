---
title: "Looking for a good OS to put on a 2GB SSD"
date: 2011-04-07
forum: Any Other OS
---

### Post by linuxuser12345 on 2011-04-07
Hey, I am trying to set up a small netbook with a 2GB SSD onboard, but I cannot find many good operating systems I can install on it. Does anyone have suggestions??

---

### Post by CharlesA on 2011-04-07
Can't really do much with 2GB, but I would suggest trying Lubuntu. It's small and fairly lightweight.

---

### Post by seawolf167 on 2011-04-07
A couple off the top of my head: [Damn Small Linux]("http://www.damnsmalllinux.org/"), [Puppy Linux]("http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm")

---

### Post by linuxuser12345 on 2011-04-07
Is there a way I can create a small, generic, lightweight distribution that fits on a 2GB SSD? If so, how?

---

### Post by CharlesA on 2011-04-07
It would probably be easier to use something that's already out there.

---

### Post by Bcrowes11 on 2011-04-07
nimblex might work....[http://linuxologist.com/1general/create-your-own-linux-distro/](http://linuxologist.com/1general/create-your-own-linux-distro/)

---

### Post by linuxuser12345 on 2011-04-07
> **Bcrowes11 said:**
> nimblex might work....[http://linuxologist.com/1general/create-your-own-linux-distro/](http://linuxologist.com/1general/create-your-own-linux-distro/)

If I create my own distro using this, will the OS that I made receive security updates?

---

### Post by Bcrowes11 on 2011-04-07
I haven't used it myself, but I've read that it's supposed to be pretty secure. Do you do alot of web surfing?

---

### Post by linuxuser12345 on 2011-04-07
Okay, how do I format the SSD and install Puppy Linux?? Can somebody help me?

---

### Post by Bcrowes11 on 2011-04-07
Your Bios should have an option to boot from usb or cd/dvd. Alternatively if your bios doesn't do that, install PLoP Boot Manager, then you can boot from them. YOu just have to write the ISO of PUppy to thumb, or cd/dvd...you get the idea. By installing Puppy to whole entire drive it should wipe out the drive. SO then Puppy should be the only distro on your netbook.

---

### Post by linuxuser12345 on 2011-04-07
> **Bcrowes11 said:**
> I haven't used it myself, but I've read that it's supposed to be pretty secure. Do you do alot of web surfing?
Yes

---

### Post by seawolf167 on 2011-04-07
Here is the Puppy Linux [manual page]("http://puppylinux.org/main/Manual-English.htm"), and here is the [how NOT to install]("http://puppylinux.org/main/How%20NOT%20to%20install%20Puppy.htm") Puppy Linux page

---

### Post by Lolpanda on 2011-04-07
Damn Small Linux
Puppy Linux
Arch Linux
Lubuntu (maybe, not sure on size)

and there was one other that was a new one.. I honestly can't remember what it was called, started with an X. I think it weighed in at 10mbs

---

### Post by linuxuser12345 on 2011-04-07
Can anyone help me with installing Slitaz onto the SSD? I do not know how to myself. :(

---

### Post by levk on 2011-04-20
You can put regular Ubuntu on 2GB, my roommate has it on a 2GB USB drive. This is with X11 and gnome-panel. You won't be able to apt-get dist-upgrade out of the box though; you can try canning openoffice and other stuff after the install and then get it to do an update.

---

### Post by uRock on 2011-04-20
Not an Ubuntu support request. Moved to *Other OS/Distro Talk*.

---

### Post by Jerry N on 2011-04-20
You might try Tiny Core.  I think it comes from the same guy the developed Damn Small Linux.  DSL, by the way, has been dead for several years although the last version can still be downloaded.

Jerry

---

### Post by Plumtreed on 2011-04-20
I would suggest you look at PeppermintICE [http://peppermintos.com/]("http://peppermintos.com/")

I use peppermintICE on my eeePC701 and initially it installed to less than 1.5 so you still have some room on a 2GB SSD.

You could install or run it effectively as a persistent live install.

Slitaz does not run in ram when installed so you are better off running it live, it can also be problematic with wireless and USB broadband. Ice will probably run these out-of-the-box.

---

### Post by mips on 2011-04-20
[http://macpup.org/](http://macpup.org/)
[http://www.slitaz.org/en/](http://www.slitaz.org/en/)
[http://www.archlinux.org/](http://www.archlinux.org/)
[http://archbang.org/](http://archbang.org/)

---

### Post by snowpine on 2011-04-20
Hi Linuxuser12345, please tell us the netbook make and model if you would like further assistance. Every answer so far is just an educated guess since we don't know much about your hardware. Other factors such as processor type, RAM, video chip, and BIOS are equally important as SSD size.

---

### Post by wolfen69 on 2011-04-20
> **linuxuser12345 said:**
> Is there a way I can create a small, generic, lightweight distribution that fits on a 2GB SSD? If so, how?

Do a command line install of debian.

---

