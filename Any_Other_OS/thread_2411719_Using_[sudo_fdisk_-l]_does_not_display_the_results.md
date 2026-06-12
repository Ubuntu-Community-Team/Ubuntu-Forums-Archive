---
title: "Using [sudo fdisk -l] does not display the results."
date: 2019-02-02
forum: Any Other OS
---

### Post by vollmair on 2019-02-02
I really need help on this one.  I'm using the Linux terminal through Crostini and I want to see the name of my SD card (like sdb1 or something) and nothing happens.  The terminal just continues on as normal, as if I didn't type anything in.

---

### Post by yetimon_64 on 2019-02-02
Are you by any chance running Ubuntu inside a virtual machine or container on a Chromebook or Chrome OS ?

Up until you asked this question I had never heard of "Crostini" with respect to Ubuntu, but after a bit of google usage...
> **What is Crostini?**

Official definition

[[COLOR=blue]Crostini[/COLOR]]("https://chromium.googlesource.com/chromiumos/docs/+/master/containers_and_vms.md#Crostini")[FONT=&amp] is  the umbrella term for making Linux application support easy to use and  integrating well with Chrome and Chromium OS. It largely focuses on  getting you a [/FONT][[COLOR=blue]Terminal[/COLOR]]("https://chromium.googlesource.com/chromiumos/docs/+/master/containers_and_vms.md#Terminal")[FONT=&amp] with a container with easy access to install whatever developer-focused tools you might want.[/FONT]

Please tell us what the main OS you are using is and if you are using Ubuntu within a virtual machine etc on another OS like Chromium OS.

If you are operating from within a virtual machine (container) the guest OS/tool set may not have direct access to the hardware and as such commands like fdisk will likely fail. More information about what you are trying to do is needed here.

Regards, yeti.

---

### Post by coffeecat on 2019-02-03
Not Ubuntu.

*Thread moved to **Any Other OS**.*

---

### Post by vollmair on 2019-02-03
Yes I am running it inside a virtual machine in Chrome OS, and I am trying to change the file directories for Steam.

---

### Post by vollmair on 2019-02-03
Is there any way of getting direct access to the tool?

---

### Post by yetimon_64 on 2019-02-03
> **vollmair said:**
> Yes I am running it inside a virtual machine in Chrome OS, and I am trying to change the file directories for Steam.

You will need to wait for someone more familiar with virtual machines to get an accurate answer here, it is a bit outside of my experience/knowledge. I have a feeling/hunch the fdisk command in the terminal within a virtual machine will not be able to poll the hardware directly so will just continue on as you note in the opening post with no output; though I have zero experience with crostini so really can't give a definitive answer.

Good luck with this, regards, yeti.

---

### Post by SeijiSensei on 2019-02-03
Virtual machines don't see the hardware on which they are running.  They use the emulated hardware in the VM.  Running "fdisk -l" in the VM will only display the virtual disk.  To see the actual drives and their partitions, you have to be running the command in the host OS, not a VM.

---

### Post by vollmair on 2019-02-04
But is there a way for the SD to be "emulated" to the virtual machine?

I can "share with linux" but it doesn't seem to change anything

---

### Post by SeijiSensei on 2019-02-05
You haven't told us what virtual machine software you're running so I can't say precisely.  With VirtualBox and its Extensions installed, you can share specific folders on the host with the guest.

---

### Post by yetimon_64 on 2019-02-05
> **SeijiSensei said:**
> You haven't told us what virtual machine software you're running....
From post 1...
> I'm using the Linux terminal through **Crostini** ....

A Crostini container on Chrome OS holding Ubuntu (Ubuntu is not specifically stated, but going on the thread so far appears to be so).

I have some experience with virtualbox but not ever having used Chrome OS and Crostini  I can't do much to help here. Being crostini the OP may have to wait for someone who uses it and Chrome OS or if that doesn't happen maybe open a support question on a Chrome OS support site.

Ubuntu is the guest OS not the host here. Cheers, yeti.

Edit: I suspect, like you mention in post 7, the OP will have to find out how to get that information from Chrome OS not Ubuntu (if it is Ubuntu in use).

---

