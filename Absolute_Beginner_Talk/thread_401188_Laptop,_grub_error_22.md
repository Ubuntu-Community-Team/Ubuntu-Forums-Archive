---
title: "Laptop, grub error 22"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by Outrunner on 2007-04-04
Hello,

Seems like I kind of messed up a bit... You see I wanted to try some distros on my lappy, but after a few hours I decided that there is no point with messing with WiFi drivers anymore(just won't work, and I can't be bothered to find more guides). Well, after deleting the linux partitions(which at the time, I didn't know that it would mess things up) I then wanted to boot into Windows a bit. 

Yeah, grub error 22. I know I need to reset the MBR but I'm telling you, EVERY SINGLE guide I could find(of course, I probably didn't search enough) involves the Windows CD. Come on people, I don't own any such CD, I only got 3 CDs from acer to restore my Windows partitions to default, but that's all.

Can you help me please?

---

### Post by phidia on 2007-04-04
If you can get a dos commandline just type:
> fdisk /mbr press <enter>

or read the webpage: [http://www.cpqlinux.com/mbr.html](http://www.cpqlinux.com/mbr.html)

---

### Post by Outrunner on 2007-04-04
Hello again, I'm sorry to say that it seems like if butchered it completely. You see I found a Win98 cd(forgot I had it), booted it up and go to the command line... Oh my god, if I don't fix this in time I'm dead. I wrote fdisk /mbr.Well, no errors so I assumed it worked... I was wrong. Every time I try to boot up it seems to be checking for some SIS device
```

SIS UNDI, PXE-2.1
Copyright lalala....

SIS900 PXE BootROM v1.09f - ZL5_0324  Use BEU/BBS

=== Press ESC to bypass LAN check ===

CLIENT MAC ADDR: [insert wrong MAC adress here]
DHCP: . . . . . . . . . . . . . .

PXE-E51: No DHCP or proxyDHCP offers were received,

OXE-M0F: Exiting SIS PXE ROM
Operating System not found
```

Pressing ESC restarts the whole message. Yes I can go into the BIOS.

I will be perfectly DEAD in two hours time if I don't find a way to fix this. Can anyone help me with this please?

---

### Post by Herman on 2007-04-04
Hello Outrunner,
I'm sorry I didn't see this post a lot earlier, but here's some post-mortem help for you anyway, there are lots of easy ways listed and in this web-page, [Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm")
I know what you mean about the Acer 'Restore' CDs, I'm an Acer owner too. I still like Acer computers regardless, but the 'Recovery' CDs aren't helpful to Linux users at all. Fortunately there are lots of work-arounds.

I hope that helps, maybe it will help someone else,
Regards, Herman  :)

---

