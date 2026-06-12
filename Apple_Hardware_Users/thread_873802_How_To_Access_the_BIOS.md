---
title: "How To Access the BIOS???"
date: 2008-07-29
forum: Apple Hardware Users
---

### Post by nikolaos on 2008-07-29
Hi all, I need to access the BIOS to disable the onboard sound Card, in order to enable my external one (Creative X-Fi Xtreme Audio). Does anyone now how to access the BIOS in a macbook? 
Or maybe any other way to do it?

---

### Post by cyberdork33 on 2008-07-29
there is no BIOS.

I am unaware of any method of disabling the audio hardware, although you could prevent the driver from loading for it by placing it in a blacklist.

---

### Post by nikolaos on 2008-07-29
PLEASE continue!!!! 
Blacklist!!!?!?!?!?

---

### Post by cyberdork33 on 2008-07-29
> **nikolaos said:**
> PLEASE continue!!!! 
Blacklist!!!?!?!?!?

Put "blacklist *your-module-name*" in /etc/modprobe.d/blacklist

---

### Post by nikolaos on 2008-07-29
ok man, thanks for the quick reply.

---

### Post by inchaos on 2008-07-30
Macs don't use BIOS, they use EFI.  It is responsible for the same tasks as BIOS, but it's closed source.

Look it up on Wikipedia, I'm sure you'll find good instructions on what you can and can't do.

---

### Post by kdb424 on 2008-07-31
I may be wrong but I do think that Macs have t emulate a BIOS for PS OS's to run on an EFI. It also uses an MBR. NO big deal, as modifying the MBR won't help you, and the emulated BIOS is, or would be locked.

---

### Post by cyberdork33 on 2008-07-31
> **kdb424 said:**
> I may be wrong but I do think that Macs have t emulate a BIOS for PS OS's to run on an EFI. It also uses an MBR. NO big deal, as modifying the MBR won't help you, and the emulated BIOS is, or would be locked.
It emulates some of the BIOS functionality, not the BIOS itself. basically it is a compatibility layer for EFI.

---

### Post by nikolaos on 2008-08-01
well, the blacklist didn't do much, so i did some search and found that the
```
efibootmgr 
```
packet might help.

the problem is that when i try to run it, I get
```

Fatal: Couldn't open either sysfs or procfs directories for accessing EFI variables.
Try 'modprobe efivars' as root.

```

so when i type 'modprobe efivars' i get
```

FATAL: Module efivars not found.

```

Any suggestions?

---

### Post by flaggh on 2008-08-01
I have no experience with this utility, or with manipulating the efi options, but I believe this utility may only be useful if you're using elilo or some other efi boot manager (I don't know of any others.)  

After going through the man page, it appears that the kernel is supposed to have access to the efi variables (again I think this assumes you're using elilo) and these should be located in /sys/firmware/efi/vars.  If this directory or file does not exist, I don't think this utility will be of much use to you.

From the looks of your signature, you're still running feisty.  Any reason you haven't upgraded to hardy?  Just curious, but why are you trying to use an external soundcard?

---

### Post by nikolaos on 2008-08-01
I **AM** using Hardy (just forgot to update the Profile:oops:). 
The thing is that i am playing music in a bar and i have everything  except that damn external sound card. Basically i need two channels as output not only one?

---

### Post by cyberdork33 on 2008-08-01
> **nikolaos said:**
> well, the blacklist didn't do much, so i did some search and found that the
```
efibootmgr 
```packet might help.

the problem is that when i try to run it, I get
```

Fatal: Couldn't open either sysfs or procfs directories for accessing EFI variables.
Try 'modprobe efivars' as root.

```so when i type 'modprobe efivars' i get
```

FATAL: Module efivars not found.

```Any suggestions?
That module is part of the kernel source, and it appears that the Ubutnu kernel does not have that module enabled in it's config. Even then, I am unsure if it will work unless you boot linux from EFI (not in the legacy OS mode). Good luck.

In other words, you are probably going to have to compile your own kernel and possibly try to figure out how to boot from EFI.

---

