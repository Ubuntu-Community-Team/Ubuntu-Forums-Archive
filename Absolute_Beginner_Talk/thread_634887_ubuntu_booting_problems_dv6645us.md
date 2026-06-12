---
title: "ubuntu booting problems dv6645us"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by donnonotin on 2007-12-08
Well after much trial and error I have Ubuntu 7.10 up and running on my HP DV6645us notebook...
I went through the process of installing the nvidia drivers for my machine (easy as pie), then I moved on the the broadcom wireless (took me all night). Nevertheless I got everything working as far as hardware wise. 

My only problem now is whenever I restart my system, Ubuntu will hang. I researched several pages on how I can fix this and turned up empty handed. I found that if I hit Esc during grub and hit "e" on the default option and remove "quiet splash" from the entry continuing with "b" it works almost everytime. After I found this out I logged in a root and edited my /boot/grub/menu.lst to exclude "quiet" and "splash" from the default boot option. Even after doing this it still hangs right before the part it normally says "loading files needed to boot" or something along those lines. 

I found out the most reliable way to get my machine to boot is just by pressing e on the entry and then b to boot it. Once I do that it usually boots though clean...I don't understand how it's not working. 

Otherwise I have to hard reset to attempt again. You see after hours and hours of configuration my system  would be perfect had it the ability to boot at least 90% of the time w.o me altering the boot process with manual intervention. I mean it would just be nice if I could get in Ubuntu w.o pressing "E" + "B".. 

If it's any help when it hangs the HDD LED on front of my notebook stays on. Any help is appreciated as I want to learn Ubuntu and ditch windows all together. If you think knowing what hardware I am on pls look at hp dv6645us, as it is 5am now and I haven't slept. Sorry for grammatical errors.I barley have the energy to post this topic. lol 

I am hoping I am just a n00b and it's a quick fix. cuz I really love this OS.

---

### Post by laidback on 2007-12-08
Think I'd check the hard drive BIOS settings first. Is the BIOS detecting the hdd correctly? When similar, but not the same, problem occurred on my installation of 7.10 I found that it was an hdd problem. The BIOS just refused to pick up the hdd properly, and if it did the size report was all wrong. After much messing I realised what the problem was, I hadn't set the jumper on the back of the hdd to MASTER, it was still on cable select, a setting that Linux doesn't like/use. Switch it to MASTER and off it went happy as anything.

---

### Post by donnonotin on 2007-12-08
Well, I opened my laptop though the HDD door on the bottom of it.. It appears that it uses no jumpers at all. I cannot access my cd-rom for jumper changing. My BIOS picks my hdd up. Is there some sort of command I can add to the boot sequence in grub to make it work properly? Thanks again.

---

### Post by donnonotin on 2007-12-09
I've been messing around in here and still am no closer to being able to fix my problem. But for those other people using a DV6645us I was able to get the broadcom 43xx error fixed with [http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/]("http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/").

Here is an overall update of my current situation. I took out both the HDD and DVD-ROM from my laptop and they both do not have jumpers. I changed my boot cfg in grub to this.

```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2aa514f7-e02b-4876-af5b-75b7798f4ab8 ro splash
initrd		/boot/initrd.img-2.6.22-14-generic

```

When it boots with no intervention it hangs at "Waiting on root filesystem". I go into my BIOS to see if there is any options I can set to maybe help it, but there is mostly just information and a few video card/boot device order options. (nothing too useful to me at this point) One thing I did just notice while pasting my default boot from grub is that the UUID that shows up in my BIOS is just a sequence of 0's. I know nothing of UUID's though...

Still the strange thing is that when I do edit the boot options in grub it pretty much always boots. What is grub doing when I hit E and enter on a line x2 and then B. What is grub doing different when I do those few steps?? 

BTW: I tried booting with the cd-rom completely outside of the computer and it still hung at the exact same "waiting on root filesystem" spot. Any ideas??

---

### Post by donnonotin on 2007-12-09
I know bumping may be against the rules of this forum (not too sure yet).

BUMPBUMPBUMP

 I am flat out desperate for some help. Someone please shed their expertise on my situation. I am willing to try anything I can to get this problem solved but I'm running out of ideas fast.

---

### Post by PinkFloyd102489 on 2007-12-09
HP computers have a tendency to be very fussy with Ubuntu.


In your BIOS, try disabling Plug and Play OS. I know it seems farfetched, but my friend was having the same problem on his HP desktop. This solved it.

---

### Post by donnonotin on 2007-12-09
I double checked my BIOS and there is no option for Plug and Play OS to Enable/Disable. Thinking it was just grub that messing up my boot process somehow, I contemplated switching it out for LILO. I think learned about UUID's and why LILO isn't a good choice for Ubuntu. Instead I installed grub2 and I still get the same error as i did before. Still no boot unless I edit a line of code.

---

### Post by spiderbatdad on 2007-12-09
[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29?highlight=%28Gutsy%29%7C%28dual%29%7C%28boot%29%7C%28installation%29](https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29?highlight=%28Gutsy%29%7C%28dual%29%7C%28boot%29%7C%28installation%29)

---

### Post by schwascore on 2007-12-09
I am having similar problems with a HP dv6636nr.  Hangs at somewhat random points and gives warnings about disabling PNP but like original poster my BIOS has no PNP option.  I am currently booting with noapic and acpi=off.

---

### Post by spiderbatdad on 2007-12-09
[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29?highlight=%28Gutsy%29%7C%28dual%29%7C%28boot%29%7C%28installation%29](https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29?highlight=%28Gutsy%29%7C%28dual%29%7C%28boot%29%7C%28installation%29)

---

### Post by donnonotin on 2007-12-10
> **spiderbatdad said:**
> [https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29?highlight=%28Gutsy%29%7C%28dual%29%7C%28boot%29%7C%28installation%29](https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29?highlight=%28Gutsy%29%7C%28dual%29%7C%28boot%29%7C%28installation%29)

Thanks a lot! you da man!

:)

---

