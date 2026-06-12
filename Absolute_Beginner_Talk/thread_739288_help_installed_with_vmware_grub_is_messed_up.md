---
title: "help installed with vmware grub is messed up"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by marine63 on 2008-03-29
okay so I got vmware on winxp and installed ubuntu 8.04 beta on my 2nd physical drive. I restarted my computer and in bios changed my hard drive so the hard drive with ubuntu on it will boot. I was able to load it perfectly and everything was peachy. Now I need help to put in a boot manager so i can have a dual boot computer :) so... help me please!!!

---

### Post by Duck2006 on 2008-03-29
Not sure what you want, but this may help.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by marine63 on 2008-03-29
i need help to install grub with out a live cd.

---

### Post by Duck2006 on 2008-03-29
> **marine63 said:**
> ... when ubuntu installed the grub in vmware it doesnt change anything on my actual computer because of this when booting up my computer there's no grub to change which os i want to boot in to. The only way i can boot if i go into bios to change the hard drive im booting into.

So you installed vmware in your win install. Then installed ubuntu in the vmware, but used your second Physical hard drive for the install. so no it's not going to install grub on your first drive's MBR.
Your saying that if you change to your second drive you can get it to boot up? If so have of the link i gave you on installing grub.

---

### Post by marine63 on 2008-03-29
is there a easier alternative to grub?

---

### Post by Duck2006 on 2008-03-29
From the live cd in the terminal type

sudo grub "That will give you a grub shell"
find /boot/grub/stage1        "That will find where grub has it's files installed"
root (hdx,y)                         "The x,y is what the last command gave you"
setup (hd0)                         "Setup grub in to the MBR that you want it to"
quit

---

### Post by marine63 on 2008-03-29
i said i dont have a live cd...

---

### Post by ghost_ryder35 on 2008-03-29
can you download a live cd?  can you download anything or burn anything?  super grub cd or the live ubuntu cd seems to be your only fix currently.

---

### Post by Duck2006 on 2008-03-29
Then super grub disk may be the way to go then.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by marine63 on 2008-03-29
i can but i ran out of cd's

---

### Post by Duck2006 on 2008-03-29
Does your BOIS let you boot from a usb device?
If so you can install super grub on a ubs stick and run it that way.

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

