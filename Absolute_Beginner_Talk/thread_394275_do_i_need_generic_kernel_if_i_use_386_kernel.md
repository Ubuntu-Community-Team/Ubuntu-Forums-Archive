---
title: "do i need generic kernel if i use 386 kernel?"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by Slapyo on 2007-03-26
i'm using the 386 kernel so i can use the nvidia drivers.  when i first installed ubuntu it installed the generic kernel.  after installing the nvidia drivers it put in the 386 kernel which i have used since then.  my question is, do i really need the generic kernel?  every time there is an update to the generic kernel (which seems a lot more often than the 386 kernel), i have to edit /boot/grub/menu.lst to default to the 386 kernel.  if there is a way i can remove the generic kernel and there wouldn't be a problem that would be great.  or is there a way to use the nvidia drivers with the generic kernel?

---

### Post by mikewhatever on 2007-03-26
I've been using generic kernel with nvidia driver (installed by envy) ever since getting Ubuntu, so I am not sure how or why you got the other kernel. Theoretically, there should be no problem in removing an unused kernel which can easily be done from synaptic. However, since we do not know how and why, wait for another opinion or two.

---

### Post by Slapyo on 2007-03-26
well how do i get the drivers to work on generic?  i'd rather go to that, it seems to be better than the 386 kernel.  then i'll toss 386.

---

### Post by mikewhatever on 2007-03-27
> **Slapyo said:**
> well how do i get the drivers to work on generic?  i'd rather go to that, it seems to be better than the 386 kernel.  then i'll toss 386.

I used envy to install nvidia driver [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
For me, it was so easy, that exceeded all expectations. I was never ever asked or offered to get another kernel, although there was an upgrade to generic.

---

### Post by msak007 on 2007-03-27
I'm not sure why that 386 kernel is still there. There used to be many options for kernels, including those optimized for Athlons, P4s, etc. My understanding is that those were ditched for the "generic" kernel because there didn't seem to be a noticeable speed boost with customized kernels and it wasn't worth it to maintain separate kernels. You should be fine using the "generic" kernel. I have a desktop with an ATI card, but I just installed Kubuntu on my uncle's computer yesterday which has an Nvidia card and I was able to install the driver from the repository and continue using the generic kernel.

---

### Post by Bachstelze on 2007-03-27
The 386 kernel is here for veeeeeeeeeery old (pre-Pentium) machines that don't support all the enhancements in the generic one.

---

### Post by msak007 on 2007-03-27
> **HymnToLife said:**
> The 386 kernel is here for veeeeeeeeeery old (pre-Pentium) machines that don't support all the enhancements in the generic one.
Got it. So it would work for, say, something like my first computer which had an Intel 486DX2-50  :)

---

### Post by Bachstelze on 2007-03-27
It would also work on your Core 2 Duo but you wouldn't get all the enhancements (Dual Core support, MMX and friends...)

---

### Post by msak007 on 2007-03-27
> **HymnToLife said:**
> It would also work on your Core 2 Duo
**<--** Wishes he had a Core 2 Duo :)

---

### Post by Slapyo on 2007-03-27
ok, so then my question is this.  how would i go about installing the nvidia driver with the generic kernel.  then how would i go about removing the 386 kernel so that i only have the generic kernel?  i know i shouldn't remove the kernel i am working on, so i want to get the generic kernel working, then remove 386.

i thought i had to use the 386 kernel because when i installed the nvidia driver, it put in 386 and booted to that one.

i would rather use the generic kernel.

---

### Post by compmodder26 on 2007-03-27
Have you tried booting into the generic kernel?  On Edgy, when I first installed the drivers for my nvidia card, it also downloaded the 386 kernel.  I simply chose to boot into the generic kernel and my card still worked fine.  Give it a try if you haven't already.

---

### Post by NikoC on 2007-03-27
I've been running the 386 kernel on a pentium M for several months now (since Feisty Fawn release herd 3) and when compared to the generic one, the 386 boots faster on my machine.

---

### Post by Slapyo on 2007-03-27
when i try to boot into the generic kernel it crashes with an error and throws me to the command prompt.  has something to do with configuring the drivers i assume.

---

### Post by hardyn on 2007-03-27
> **HymnToLife said:**
> The 386 kernel is here for veeeeeeeeeery old (pre-Pentium) machines that don't support all the enhancements in the generic one.

That is no longer accurate... in speaking with Ben C. the 386 is now a uni-processor generic kernel.  been this way since edgy.

the 386 kernel is required from some P-M applications.

---

### Post by Slapyo on 2007-03-27
so how would i go about making sure the nvidia drivers were installed with the generic kernel and then how would i remove the 386 kernel?

---

### Post by NikoC on 2007-03-28
Startup synaptic and search on 'linux', you will get a lot of hits, but just scroll down and you will find all the kernels installed on your system. You can remove them from here. Make sure that you boot the generic one before you delete the 386 kernel, otherwise it won't be possible... d'uh ;)

To install the nvidia drivers, there are a some good guides on the forum, e.g. searching title only with  'howto nvidia edgy' will give you the following guide:
[http://www.ubuntuforums.org/showthread.php?t=281823&highlight=howto+nvidia+edgy]("http://www.ubuntuforums.org/showthread.php?t=281823&highlight=howto+nvidia+edgy")
The same goes for Dapper or Feisty.

An other option is to download the drivers from nvidia.com and follow the instructions there.

Good luck!

---

### Post by Slapyo on 2007-03-28
ok cool, gonna go see what damage i can do.

---

### Post by Slapyo on 2007-03-28
do i need to be on the generic kernel to install the nvidia drivers on it?  or can i be on the 386 kernel, i saw you specify which kernel in the command line when you install.

---

### Post by NikoC on 2007-03-28
For the installation of the proprietary nvidia drivers (as offered by nvidia or made available via adding extra repositories as described in numerous other threads) you need the boot the kernel you want to install them in (haven't read about an option which allows you to select the 'target' kernel). Because they are proprietary Ubuntu is not allowed to have them in their kernel release, so with every kernel update comes the re-installation of the nvidia drivers.

At least that's how I interprete the topic 'nvidia and kernel' ;)

---

### Post by Slapyo on 2007-03-28
hm, 386 just updated the kernel and i didn't have to re-install the drivers.  new nvidia drivers came through as well.

---

### Post by Slapyo on 2007-03-28
by running the following command in a terminal window while on the 386 kernel, this did the trick.

```
sudo apt-get install linux-generic
```

it went through and did it's thing.  then i booted into the generic kernel no problem.  everything is working great.

---

### Post by NikoC on 2007-03-29
Aha great news there! I guess that's probably because you've previously edited your sources list which made nvidia drivers available...

---

### Post by Slapyo on 2007-03-29
Actually, I've never edited my sources list heh.  I installed the drivers through the terminal, didn't download them from the nvidia site.  Either way, it's cool it's working.  Now I just need to figure out how to remove old kernels I don't need/want anymore.

---

### Post by NikoC on 2007-03-29
In a terminal just type:
sudo synaptic

Synaptic package manager will start up, do a search on 'linux' and scroll through the list to find and remove unused kernels with their modules and headers. The removed kernel(s) will automatically be deleted from grub.

---

### Post by Slapyo on 2007-03-29
cool thanks.

if i remove the linux-image-{kernel} will it automatically remove the modules and headers associated with them?

---

### Post by NikoC on 2007-03-30
Hmmz, just tried it out myself because I wasn't sure anymore and I have to seperately select the linux image (kernel), restricted modules and headers for removal...

---

### Post by Slapyo on 2007-03-30
when i did it last night i removed the linux-image-{kernel} that i wanted and it also prompted me for the restricted modules for each one that had them.  i will go through and look to see if headers are still there and if there is anything else.

---

### Post by NikoC on 2007-03-30
Perhaps that is a difference between Feisty development that I'm running at the moment and Dapper or Edgy that you are using...

---

### Post by Slapyo on 2007-03-30
I'm running feisty.

---

### Post by Slapyo on 2007-03-30
it removed the modules, but not the headers.  i just removed those right now.   was another 195mb of space.

---

