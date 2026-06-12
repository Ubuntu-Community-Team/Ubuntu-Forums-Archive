---
title: "Thinking about a Mactel Mini"
date: 2007-02-16
forum: Apple Intel Users
---

### Post by technodigifreak on 2007-02-16
Thinking about a Mactel Mini, who has already tried installing Ubuntu (Dapper, Edgy, or a Feisty Herd) on it? And what problems, considerations have you encountered?

---

### Post by Gen2ly on 2007-02-16
I use Ubuntu Efty Edge on a Macbook (which is essentially the same thing) and you have to know what you're doing if you want to dual (triple?) boot.  But it runs great!

---

### Post by xfile087 on 2007-02-16
I currently run Edgy on my Intel Mac Mini and it runs beautifully - even with Beryl which i'm pleased about considering it's an integrated GPU.

I'd also like to note that since these are Intel Macs and they run the i386 version of Ubuntu, I find that there is much more software available and it's much easier to get a hold of and install.

For example I was trying for days to get Beryl installed on my PowerPC iBook. On the Mini it took seconds...

If you want to to dual boot with Mac OS X - [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) - is what I follow. It works perfectly on the Mac Mini.

---

### Post by entangled on 2007-02-17
I have a Intel Mac Mini solo with 1GB RAM. I have dual-booted ubuntu Dapper, using Boot camp, and virtualised using parallels. At the time parallels was too slow to use.
Since then I have single-booted ubuntu Dapper, and upgraded it to Edgy. The single boot system means setting the main disk to be MBR-style (instead of GPT that Apple uses) and installing ubuntu directly onto the main disk, just like a PC box.
The boot camp dual boot was a bit inconvenient and slightly awkward to set up. But it did work, and supported booting off a cloned external drive too.
The parallels option was useless when I first tried it, but there has been a recent update and that works much better. It is fast enough, but sound doesn't work. There is no file copy with host either. Both these work well with XP running in parallels.
The single boot option worked best. I had sound, bluetooth, networking, usb, printing, scanning, etc.... but no MacOSX!
As you might guess I switch between MacOSX and Ubuntu fairly often, but it doesn't take long and its good for remembering and testing backups.

---

### Post by garlito on 2007-02-21
> **entangled said:**
> 
Since then I have single-booted ubuntu Dapper, and upgraded it to Edgy. The single boot system means setting the main disk to be MBR-style (instead of GPT that Apple uses) and installing ubuntu directly onto the main disk, just like a PC box.

Hi, are you still there? I've just bought an Intel Mac Mini and I'm not interested in MacOs X, I will run Ubuntu and Windows XP. Do you mean that I can turn a Mac into a normal PC just by changing the partition table format? Can you tell me how can I do it, please? I'm reading about Dual Boot but that might be much easier.

Thanks.

---

### Post by tubasoldier on 2007-02-21
How well does Ubuntu run under Parallels desktop? I know Windows boots up and runs as if it was on it's own machine. Just curious about Linux in Parallels.

---

### Post by entangled on 2007-02-21
Hello garlito (and tubasoldier).
To get a Mac disk into the state for installing and mbr-based distribution you can 
1.  run up the Mac Disk Utility
2.  select your main disk
3.  click the partition button to get a view of the disk layout
4.  click the options button to be offered a choice of partition scheme.
5.  choose mbr and then OK.

After that your disk is no good for macosx but you will be able to install mbr-booting CDs like linux and windows install disks and you can use normal grub to do boot loading.
To get back to Macosx you need to boot from the Mac install CD and run the Disk utility again to set the scheme back to GPT so the Mac recognises it and can install itself on there.

For tubasoldier - latest version of parallels (1970) runs well under macosx. It can be slightly slow for mouse pointer movement, but it used to be incredibly slow and they've improved it a lot. I think it is very usable but you won't get file copy between host and guest - use a USB stick and connect-disconnect USB devices.

---

### Post by garlito on 2007-02-21
Thanks entangled, I will try next week-end :)

---

### Post by ketilkn on 2007-03-02
I have enabled MBR and installed Ubuntu (Feisty) following entangleds ideas . When I try to boot my screen goes Mac gray and then eternal black.I do not think Ubuntu boot after this. Any ideas are welcome.

---

### Post by ketilkn on 2007-03-04
My issues where resolved by booting up Ubuntu with rEFIt and then updating. After this Ubuntu will boot without any problems. I am not sure if the updating part is necassary.

---

### Post by macLuntu on 2007-03-16
ketilkn: I have exactly the same problem. Can you please be more specific on how you fixed it, please?

---

