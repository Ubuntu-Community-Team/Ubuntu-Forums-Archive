---
title: "vmware vs. bootcamp"
date: 2007-11-06
forum: Apple Intel Users
---

### Post by anemptygun on 2007-11-06
I have been looking around and I haven't quite gotten my question answered so... I am about to purchase a new macbook (no bashing please :P ) and i wish to run ubuntu on this macbook as well as leopard. So would Vmware fusion or boot camp be better? I will be spending a fair amount of time in ubuntu, so booting down is not an issue. But which will provide the easiest method to install and run reliably?

Thanks in advance! :KS

---

### Post by cyberdork33 on 2007-11-06
> **anemptygun said:**
> I have been looking around and I haven't quite gotten my question answered so... I am about to purchase a new macbook (no bashing please :P ) and i wish to run ubuntu on this macbook as well as leopard. So would Vmware fusion or boot camp be better? I will be spending a fair amount of time in ubuntu, so booting down is not an issue. But which will provide the easiest method to install and run reliably?

Thanks in advance! :KS

your real question is: Do I want to dual boot or install in a Virtual Machine?

The answer is: It depends on what you plan to do with Ubuntu. How much do you plan to use it? What applications do you want to use in Ubuntu?

---

### Post by LeopoldBloom on 2007-11-07
If you want to play with the Compiz effects, you'll need to dual-boot as far as I'm aware. Most other things can be done through VMWare or Parallels.

---

### Post by bluedragon436 on 2007-11-07
I would have to say my personal opinion would be to run VMWare...but that is just me...I ran bootcamp on my macbook and I wasn't pleased at all...then I ran VMWare and it ran better for me...

---

### Post by cyberdork33 on 2007-11-07
> **bluedragon436 said:**
> I would have to say my personal opinion would be to run VMWare...but that is just me...I ran bootcamp on my macbook and I wasn't pleased at all...then I ran VMWare and it ran better for me...

This can be a big factor. The VM's virtual hardware is usually much more linux compatible than the real hardware in your Mac.

3D acceleration is not (yet) possible in a VM under linux.

I suggest a VM if you are 'trying out' Ubuntu or if you need quick access to some application without having to reboot. If you are serious about using Ubuntu at all, then you should install it natively.

---

### Post by anemptygun on 2007-11-07
Yeah, I don't need compiz, or graphics acceleration. I would just like to use the ubuntu enviroment. I have some classes at school that I use it for so it would just be good to have...

p.s. vmware can go fullscreen right?

---

### Post by czechman86 on 2007-11-07
yes, i t can go full screen. I have found that with VM, ubuntu runs slow, and that if you want the real thing, go with bootcamp.

---

### Post by anemptygun on 2007-11-07
Really!? hmm i'm surprised! Has anyone else had this problem? It will be running on a 2.2 core 2 duo with 2 gigs of ram, i wouldn't expect that to be slow.

---

### Post by Chrisj303 on 2007-11-07
Yeah , my vote goes for Native install. 

However,..
You can always install Ubuntu as a Dualboot setup, then use parallels to boot that partition from a VM. So it really dosen't have to be a choice of one or another!

---

### Post by anemptygun on 2007-11-07
Wait, so you can set up a partition for Ubuntu and run vvmware on that partition? I'm confused?

---

### Post by Mithrilhall on 2007-11-07
Try the VMware route first. It's easy enough to delete the virtual machine and go the dual boot way if you want.

I've never run Ubuntu in a VM but Debian flies in a VM for me.

---

### Post by aysiu on 2007-11-07
On a sidenote, how does VirtualBox work on Intel Macs? Would VMWare and Parallels definitely be better choices?

---

### Post by anemptygun on 2007-11-07
> **Mithrilhall said:**
> ...but Debian flies in a VM for me.

what kind of hardware do you have?

---

### Post by cyberdork33 on 2007-11-07
> **anemptygun said:**
> Wait, so you can set up a partition for Ubuntu and run vvmware on that partition? I'm confused?

Yes, but it is not really obvious how to do it unless you are installing windows.

---

### Post by cyberdork33 on 2007-11-07
> **aysiu said:**
> On a sidenote, how does VirtualBox work on Intel Macs? Would VMWare and Parallels definitely be better choices?

Good question. I have been meaning to try that out. VMware / Parallels are defintely faster than using Qemu.

EDIT: No, it crashes immediately upon startup (in Leopard though). Looks like it is a bit underdeveloped yet for OSX anyway, even for Beta (2).

---

### Post by anemptygun on 2007-11-07
> **cyberdork33 said:**
> Yes, but it is not really obvious how to do it unless you are installing windows.

I think I'm just going to try boot camp first, and if i'm not happy with that then i will go with vmware.

---

### Post by cyberdork33 on 2007-11-07
> **anemptygun said:**
> I think I'm just going to try boot camp first, and if i'm not happy with that then i will go with vmware.
I really think the opposite is what you want to do first. It is much more hassle free to tryout ubuntu in a VM.

---

### Post by anemptygun on 2007-11-07
i guess the main reason i chose that order is the fact that boot camp is free, but you are right. it might just be worth the money...

---

### Post by cyberdork33 on 2007-11-07
> **anemptygun said:**
> i guess the main reason i chose that order is the fact that boot camp is free, but you are right. it might just be worth the money...

You don't have to buy it unless you keep it. There is a trial period.

---

### Post by anemptygun on 2007-11-07
cool! will do! just out of curiosity does vmware fusion have the latest directx support?

---

### Post by cyberdork33 on 2007-11-07
> **anemptygun said:**
> cool! will do! just out of curiosity does vmware fusion have the latest directx support?

directx 8.1

---

### Post by Frak on 2007-11-07
Go for Fusion, you'll be quite happy with it.

---

### Post by Frak on 2007-11-07
> **aysiu said:**
> On a sidenote, how does VirtualBox work on Intel Macs? Would VMWare and Parallels definitely be better choices?
I've had stability issues with VB.

---

### Post by anemptygun on 2007-11-09
another question :P I play alot of cs:s does anyone know if i would be able to use vmware fusion to replace the windows side of things. I know that vmware supports up to directx 8.1, is there any issues since it does not support dx9?

---

### Post by cyberdork33 on 2007-11-09
> **anemptygun said:**
> another question :P I play alot of cs:s does anyone know if i would be able to use vmware fusion to replace the windows side of things. I know that vmware supports up to directx 8.1, is there any issues since it does not support dx9?

Not unless there is some Directx9 application (i.e. game) that you are trying to run.

I think Counterstrike Source requires Directx 7

---

### Post by Frak on 2007-11-09
> **anemptygun said:**
> another question :P I play alot of cs:s does anyone know if i would be able to use vmware fusion to replace the windows side of things. I know that vmware supports up to directx 8.1, is there any issues since it does not support dx9?
I use Crossover for Mac to run CS:S, but I bet Darwine could run it also.

---

### Post by anemptygun on 2007-11-10
> I think Counterstrike Source requires Directx 7
Excellent! thanx!:guitar:

---

