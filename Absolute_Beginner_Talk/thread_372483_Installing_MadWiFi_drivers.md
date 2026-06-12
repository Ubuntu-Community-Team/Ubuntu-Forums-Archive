---
title: "Installing MadWiFi drivers"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by lawentzel on 2007-02-28
I am completely new to Linux. Installed Ubuntu 6.10 flawlessly. It recognizes a borrowed network card on my laptop. I have a wireless card I would like for it to use. I am told the correct drivers would be the "MadWiFi" drivers.  I've downloaded them onto my desktop, unarchived them. Now what? How do you go about installing drivers?  The only thing I have installed thus far have all been through the Add/Remove option.  Your help in these matters would be greatly appreciated. Thanks.

Lee

---

### Post by Maestro23 on 2007-02-28
> **lawentzel said:**
> I am completely new to Linux. Installed Ubuntu 6.10 flawlessly. It recognizes a borrowed network card on my laptop. I have a wireless card I would like for it to use. I am told the correct drivers would be the "MadWiFi" drivers.  I've downloaded them onto my desktop, unarchived them. Now what? How do you go about installing drivers?  The only thing I have installed thus far have all been through the Add/Remove option.  Your help in these matters would be greatly appreciated. Thanks.

Lee

In the extracted directory, there should be a README or INSTALL doc.  Follow the directions.

If you are compiling from our source, you will need "build-essential" installed first.

> sudo aptitude install build-essential

Compiling from source can be tricky for people new to linux, good luck.

---

### Post by forrestguide on 2007-02-28
I'm in the same boat.  I had a cd with the drivers.  The usb wireless is generic and thus has no Manufacturer listed. There's not install info in the directory that I loaded it int.

Any help would be helpfull.

Is there a generic driver that can be used?

Thanks,

Greg

---

### Post by bcalder01 on 2007-04-07
Thanks for this post, Maestro. I was tearing my hair out trying to reinstall MadWifi, and couldn't figger out what I was missing! My laptop is happily (finally!) make-ing away right now. :-)

---

