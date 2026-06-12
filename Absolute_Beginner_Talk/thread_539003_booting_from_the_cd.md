---
title: "booting from the cd"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by fminmexico on 2007-08-30
How do I boot from the Ubunto live cd

---

### Post by Happy_Man on 2007-08-30
If your computer is recent, all you have to do is put it in your CD drive and reboot. If it's an older computer, you will have to watch the screen at the beginning (the one that has the computer manufacturer's logo on it) for a key to press to change the boot order. Press that key, and select the CD drive, with the CD in it.

---

### Post by Daveth on 2007-08-30
that will put you into your PC's BIOS where you will be looking for a boot order tab. You will have to navigate only using the keyboard usually. Select the boot order so that the cd drive is first, then your hard drive(s), then save changes and reboot (something like the F10 key from memory). Be careful what you do in the BIOS. The cd drive will then look for a bootable cd, find ubuntu and off you go.

---

### Post by fminmexico on 2007-08-30
> **Happy_Man said:**
> If your computer is recent, all you have to do is put it in your CD drive and reboot. If it's an older computer, you will have to watch the screen at the beginning (the one that has the computer manufacturer's logo on it) for a key to press to change the boot order. Press that key, and select the CD drive, with the CD in it.

I tried choosing cd on boot order but it still will only boot windows
        fminmexico.

---

### Post by fjf314 on 2007-08-30
> **Daveth said:**
> that will put you into your PC's BIOS where you will be looking for a boot order tab.

Not necessarily. On some machines, you get two options during the BIOS screen. One is to enter the BIOS and the other is to manually select the boot location for that one instance. For example, on my 2.5 year old Dell, I can press F12 during the BIOS screen and I just get a screen asking me if I want to boot from the HDD or the DVD drive.

Edit: It looks this didn't matter since the OP got into the BIOS.

---

### Post by Daveth on 2007-08-31
perhaps it is a DELL feature then, as my Asus Premium, which is the same age, is a standard BIOS entry mode job.
As to the post, did you make the live cd or buy/get given it, and if you made it how did you burn it? I'm assuming the drive works with everything else, of course.

---

### Post by fminmexico on 2007-08-31
> **Daveth said:**
> that will put you into your PC's BIOS where you will be looking for a boot order tab. You will have to navigate only using the keyboard usually. Select the boot order so that the cd drive is first, then your hard drive(s), then save changes and reboot (something like the F10 key from memory). Be careful what you do in the BIOS. The cd drive will then look for a bootable cd, find ubuntu and off you go.

I did this cdrom 1st hd 2nd saved restarted still booted into windows.
    fminmexico

---

### Post by fminmexico on 2007-08-31
> **Daveth said:**
> perhaps it is a DELL feature then, as my Asus Premium, which is the same age, is a standard BIOS entry mode job.
As to the post, did you make the live cd or buy/get given it, and if you made it how did you burn it? I'm assuming the drive works with everything else, of course.

I burned the cd,when I put the cd in it opens to the browser so their is not a problem with the cd. I went to bios changed the boot order 1 cd/2 hd/3 floppy it still boots to windows.
   fminmexico.

---

### Post by fminmexico on 2007-08-31
> **fminmexico said:**
> I burned the cd,when I put the cd in it opens to the browser so their is not a problem with the cd. I went to bios changed the boot order 1 cd/2 hd/3 floppy it still boots to windows.
   fminmexico.

I tried the cd in my mac it loaded no problem.I then rebooted the mac from the cd and it booted into OSX.Why can I read the cd but not boot from it.
     fminmexico.

---

### Post by schorsch on 2007-08-31
What did you see in the browser window when you put the CD in: One file named .iso at the end or many files and directories?

---

### Post by fminmexico on 2007-08-31
> **schorsch said:**
> What did you see in the browser window when you put the CD in: One file named .iso at the end or many files and directories?


Ubunto 7.04 (disc tree)
boot from this cd try ubunto without changing your system.
Firefox
Thunderbird
Abiword
Blender
Clamwin

---

### Post by oldos2er on 2007-08-31
>I tried the cd in my mac it loaded no problem.I then rebooted the mac from the
> cd and it booted into OSX.Why can I read the cd but not boot from it.

 Possibly because you didn't burn it as an ISO image.

---

### Post by Happy_Man on 2007-08-31
Read this article: [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

If you didn't use a method similar to that to burn your CD, follow those directions and try again.

---

