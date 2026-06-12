---
title: "Run Windows and Ubuntu at the same time"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by Alex6969 on 2006-12-07
Is there a way to boot windows and linux at the same time, and switch between the two on the fly?

---

### Post by aysiu on 2006-12-07
Yes.

1. Boot into Windows and run Ubuntu in VMWare
2. Boot into Ubuntu and run Windows in VMWare
3. Get two computers and a KVM switch

---

### Post by lucky_chouhan on 2006-12-08
Yes Vmware Is The Right Solution For You.

---

### Post by antharr on 2006-12-08
I have to say that VMware works great for me. Don't even have to have a extra partition set up for windows.

---

### Post by Big_Croc7 on 2006-12-08
I've never used VMware and I'm very new to Linux at all, so someone will hopefully correct me if I'm wrong, but I think that running a system 'within' another one (which is how I think VMware works) will be considerably slower than running it 'natively' - so, for example, playing modern games probably won't work like that.

Perhaps someone else could clarify?

---

### Post by mcduck on 2006-12-08
It actually works really fast. But you can't use it for gaming, as the games need to have direct access to your graphics card and that's not possible with virtual machines. Also about all professional audio or 3D apps are out of question. But normal desktop apps work just great.

---

### Post by wyldstryker on 2006-12-08
If you're wanting to give vmware a go, here's a link to a very nice walk through.

[http://ubuntuforums.org/showthread.php?t=183209]("http://ubuntuforums.org/showthread.php?t=183209")

---

### Post by wpshooter on 2006-12-08
> **Alex6969 said:**
> Is there a way to boot windows and linux at the same time, and switch between the two on the fly?

Yes you can, but my recommendation would be that if you want to run Windows and Linux, to run them on two separate machines.

---

### Post by housam on 2006-12-08
Originally posted by wyldstryker >   
If you're wanting to give vmware a go, here's a link to a very nice walk through.

[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209) 


Great link ,very helpfull.:D

---

### Post by Jonas90 on 2006-12-08
You could use the suspend-to-disk/hibernate feature. This will write the current status to disk and then reboot the computer.

It's shift click on suspend in WinXP, if I remember correctly.

I'm not sure wheter you need some extra packages installed on Ubuntu or if this is supported out of the box.

Caveat: You can not write to partitions, that are used by the suspended operation system.

---

### Post by burek on 2006-12-08
> **Big_Croc7 said:**
> I've never used VMware and I'm very new to Linux at all, so someone will hopefully correct me if I'm wrong, but I think that running a system 'within' another one (which is how I think VMware works) will be considerably slower than running it 'natively' - so, for example, playing modern games probably won't work like that.

Perhaps someone else could clarify?

If you have good cpu, vmware and wine will work great.

On the other hand, for old machine, vmware can be too slow.
wine can still make it but a bit slow too in this case.

---

