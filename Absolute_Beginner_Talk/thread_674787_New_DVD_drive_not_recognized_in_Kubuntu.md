---
title: "New DVD drive not recognized in Kubuntu"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by TeaSwigger on 2008-01-22
Have 2 optical drives on my ol' PIII PC. 1st (master) is a DVD-RW. Was and is working perfectly.

Removed functioning CDROM drive (slave at /dev/scd1 ) and replaced it with a DVD-RW drive. 

The new drive is correctly recognized in BIOS.

The new drive does function perfectly in Windows 2kpro.

The new drive is not recognized at any location in Kubuntu. 

Running command sudo lshw -C disk does not list the new device.

Help? :(

---

### Post by LaRoza on 2008-01-22
What kind of drive is it?

Also, are the jumpers set correctly?

---

### Post by TeaSwigger on 2008-01-22
Thanks for the quick response, LaRoza. 

It's a generic HI-VAL thing, specified (ha!) as Generic in BIOS and 2kpro. Afraid I don't know the real make. It was a gift and works just ducky in 2kpro so I haven't complained. ;) Yes the jumpers were set to slave, as the other drive on the IDE channel (NEC ND-3540A DVD-RW, nice drive that) is set to master (again, that drive wasn't touched and continues to work fine). These opticals are on an 80-pin ribbon.

---

### Post by rhc on 2008-01-22
Do you use the same Ide cable for both Dvd and hard-disk?
If so,try to use another one for Dvd,let's see the result then.

---

### Post by TeaSwigger on 2008-01-22
> **rhc said:**
> Do you use the same Ide cable for both Dvd and hard-disk?
If so,try to use another one for Dvd,let's see the result then.

Thanks for the reply. No, fortunately it has two IDE channels, one has the hard-disks and the other has the opticals.

---

### Post by TeaSwigger on 2008-01-22
Given the speed of this forum, this isn't a bump, it's a relocation :biggrin:

---

### Post by TeaSwigger on 2008-01-22
All I could find out about this thing is that it's OEM is "Accesstek or BTC" and chipset is "Sanyo or Mediatek." 

It's probably working fine, I just can't seem to find out how to install a new optical drive in Linux / ubuntu.

---

### Post by TeaSwigger on 2008-01-22
Searching here or googlin' seems to turn up anything but this subject.

---

### Post by TeaSwigger on 2008-01-23
So far it ain't fixin' its self.

---

### Post by rhc on 2008-01-23
Did you try to put a cd or dvd into dvdrw? :)
No drive is shown in Ubuntu unless you do it.
: )

---

### Post by TeaSwigger on 2008-01-23
Sure did, and thanks for getting back on this. A funny thing, I'd put in a DVD and nothing whatsoever; I'd put in a CD and the KDE "autoplay" options dialog popped up, but when I chose to open it, nothing - no content, no disc, no drive - was found.  Not even with sudo lshw -C disk command. Weird. Must be missing something.

---

### Post by logos34 on 2008-01-23
run

**cdrecord --scanbus**

anything?

If lshw doesn't list it, that's not a good sign.  

What about swapping it with the other dvd drive (remember to set the jumper to master).  Is it recognized now?  

Alternately, try one or both with 'cable select' jumper setting

(even though the Bios recognizes it ok, maybe changing a few things around will help linux see it).

---

### Post by TeaSwigger on 2008-01-23
Thank you for the reply, logos34. There was no cdrecord on my system, so I tried wodim --scanbus, if that's essentially the same. It showed my NEC DVD drive but not the new one.

So I opened the case again and switched locations, and again to change the jumpers to CS. Neither method made a difference. The new drive is still recognized in BIOS, still working in 2kpro, but not recognized in Kubuntu. Arr.

Ideas?

---

### Post by logos34 on 2008-01-23
> **TeaSwigger said:**
> Ideas?

Not really.

Unless maybe grub is causing some problem.  Sounds strange, I know, but there are a few threads out there where people have an optical that works fine in windows but not at all in linux, and they've only gotten it to work in linux if they switch to another bootloader, like LILO.  I haven't really looked into it, though.

Hopefully someone else can offer some suggestions.

---

### Post by mc4man on 2008-01-23
I've got a similar setup I use for testing and I see some oddities about adding and /or replacing cd/dvd drives but can't quite wrap my head around it yet. You should post your fstab and also put some media (like a boot disk) in both drives and post mtab. I'm gonna kept fooling around

note:fstab is never updated from orig. install

---

### Post by TeaSwigger on 2008-01-23
Thanks for the reply. Yeah I checked fstab right off, I have:

```
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec 0 0
```

for the two opticals. Exactly the same as it was before I pulled the old cdrw and replaced it with this dvdrw (it was working fine). 

Where scd1 would be the new drive.

Incidentally I looked in /dev/ and there's no scd1 anymore. If one made a "device block" - if one can - would it work...? lol clearly I'm far from expert on any of that.

mtab? There's a new one for me to learn :p

---

### Post by mc4man on 2008-01-24
i thought I had a similar issue but turns out not. i had been interrupted swapping out the slave dvd drive before a fresh install and hadn't hooked it up. In any event I haven't had any issues swapping drives - I went back and forth a couple of times between a cd-rw and dvd-rw, they're always recognized upon booting up, (and actually work for the most part without an fstab entry)
I would think you could remove grub from the equation by using your working drive to boot to the live cd and see if your other drive is found and operational

---

