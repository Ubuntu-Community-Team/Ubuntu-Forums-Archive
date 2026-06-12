---
title: "need to reverse function of &quot;fn&quot; key on MacBook 5,1 keyboard"
date: 2009-03-01
forum: Apple Hardware Users
---

### Post by ElsiePiddock on 2009-03-01
hi, normally (when held) the fn key in the lower-left corner of the keyboard on my MacBook 5,1 (unibody aluminum late 2008) turns the funtion of the function keys into whatever the defaults for the current app are.

without the fn key held, the function keys perform functions like: adjusting screen brightness, volume, and controling media players.

i would like to reverse this (i.e. make the function keys perform the defaults for the current app when pressed singly, and perform the brightness/volume/media functions when pressed while the fn key is held)

any help will be greatly appreciated. thanks.

---

### Post by cyberdork33 on 2009-03-01
[http://www.rickycampbell.com/swap-fn/](http://www.rickycampbell.com/swap-fn/)

---

### Post by inphektion on 2009-03-07
thanks worked perfectly.
if there is an initramfs update will I have to do this again?

---

### Post by guidop on 2009-03-08
If you're running a recent (8.04 or 8.10) version on Ubuntu on a mac, pommed is most likely installed to provide the special function key behavior for brightness, volume, and disk eject.  (Earlier versions of Ubuntu ppc used pbbuttonsd.)

I believe another way to do switch the "fn" key behavior isto edit the /etc/pommed.conf file, and change the value of fnmode under general configuration.

Here's one link to an example pommed.conf file:
[http://sysinf0.klabs.be/etc/pommed.conf?dist=;arch=]("http://sysinf0.klabs.be/etc/pommed.conf?dist=;arch=")
If pommed is installed, this file should already exist on your machine.


Note:  Per this post, it looks like Jaunty may use applesmc, instead of pommed:
[http://ubuntuforums.org/showthread.php?t=964224]("http://ubuntuforums.org/showthread.php?t=964224")

The pommed package is still listed as available in Jaunty:
[http://packages.ubuntu.com/intrepid/pommed]("http://packages.ubuntu.com/intrepid/pommed")

Guess I'll have to see what happens with a fresh Jaunty install.

---

### Post by cyberdork33 on 2009-03-08
> **inphektion said:**
> thanks worked perfectly.
if there is an initramfs update will I have to do this again?
I don't think so. The option will still be in the file, and thus will be used when the initramfs is updated in the future.

and correct, you should not use pommed anymore. there is no need for it, and it only interferes with other things making your computer work properly.

---

### Post by guidop on 2009-03-12
> and correct, you should not use pommed anymore. there is no need for it, and it only interferes with other things making your computer work properly.

Reading the RickyCampbell post:

> Previous to Intrepid, it was recommended to install pommed to enable the functions of many of these special keys. pommed’s config file had the option to swap the way the Fn key works, requiring you to use Fn in order to change the brightness, etc. Now, in Intrepid (8.10) most of the functionality of pommed has been implemented into hal and pommed simply creates conflicts.

**Can someone point me to documentation on the new hardware abstraction layer [hal] method of implementing special key functions?**

Does this hal functionality only start with the Intrepid kernel 2.6.28, or is there a package/application/kernel module for older kernels, such as Hardy's 2.6.24?

Does the same hal functionality exist on ppc?  
I noticed with Debian lenny (2.6.27) ppc, the brightness keys seemed to have kernel support, but not the volume nor eject keys.  Adding pommed made them work, even when X is not running.

Thanks.

---

### Post by cyberdork33 on 2009-03-12
> **guidop said:**
> Does this hal functionality only start with the Intrepid kernel 2.6.28, or is there a package/application/kernel module for older kernels, such as Hardy's 2.6.24? no, it was added during the development of intrepid and the kernel was patched then as well.

> **guidop said:**
> Does the same hal functionality exist on ppc?
No idea, but PPC used some other daemon besides pommed for this stuff, and then pommed came along as the "new" replacement fo those, and continued into the Intel Mac.
> **guidop said:**
> I noticed with Debian lenny (2.6.27) ppc, the brightness keys seemed to have kernel support, but not the volume nor eject keys.  Adding pommed made them work, even when X is not running. I would stick with that then on PPC for now. None of the changes made to the kernel to replace the pommed functionality were tested or designed to work with the PPC Macs that I know of.

---

