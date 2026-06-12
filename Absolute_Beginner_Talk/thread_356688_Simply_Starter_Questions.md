---
title: "Simply Starter Questions"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by Plankzt on 2007-02-08
So I tried installing Ubuntu for the second time, which, might i say, worked, hoorah.
But I'm having some teething problems, I've just switched over from windows.

First up: graphics card drivers, I'm experiencing some seriously choppy performance, which is nothing new, since this board has a stupid on board card which does the same thing and boots itself first over my main card. I need to know how to switch my card from the on board one, to the PCIe card. I also need to know how to install the drivers for it, but I'm hoping very much wine will take care of it *crosses fingers*
Secondly: Another graphical issue, changing the resolution, I'm utterly clueless about how to do it.
Third: I've just threw ubuntu on a spare drive, and would very much like to access the files on the other drive I use for windows, is this possible..?

(while writing this my desktops just locked up ^^)

that's all the whining I can think of at the moment,
Thanks for your help =]

---

### Post by taurus on 2007-02-08
1 & 2.  Is it one of those onboard Intel graphic controllers?

3.  [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

4.  What's the spec of your machine and how much swap space do you have?  Paste the output of this command here.

Applications -> Accessories -> Terminal
```
free
```

---

### Post by daou on 2007-02-08
Some motherboards with integrated gfx cards allow you to boot with a different gfx card by changing BIOS settings, or even possibly a motherboard jumper. However, this is something to be done with documentation in hand and with caution. I certainly don't recommend it if there is a software based solution to switch the integrated card off.

---

### Post by Plankzt on 2007-02-08
Swap:      1646620          0    1646620
=]

And as for the gfx card, In windows I just played around with rebooting and changed it simply in the control panel.
specs: AM2 3600+, ATI1650pro (which isn't working :p) 1gb DDR2, 'tis fairly sufficient, the desktop crashed after updating some stuff from the livecd install. Reboot fixed it.

Thanks again =] (halp me make my gfx card work pleasaasease, can't even browse with this choppy crap ^^)

EDIT: As for the mounting windows drives in linux, I got stuck on the first step, how do I find out what my mount positions are called?

And it's an AMD board, so yeah it's still a crappy on board one.

---

### Post by Happy_Man on 2007-02-08
```

sudo fdisk -l

```

will display all your partitions that are hooked up. For example, mine is:

```

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           5       40131   de  Dell Utility
/dev/hda2   *           6        9158    73521472+   7  HPFS/NTFS
/dev/hda3            9159       14500    42909615   83  Linux
/dev/hda4           14501       14593      747022+   5  Extended
/dev/hda5           14501       14593      746991   82  Linux swap / Solaris

```
So you can see my Windows partition is on /dev/hda2, and my Ubuntu partition is on /dev/hda3. For you, you may see /dev/**hdb1** or /dev/**hdb2** or whatever. Just find that partition that has HPFS/NTFS as format and mount it. Easy!:KS

---

### Post by Plankzt on 2007-02-08
> **Happy_Man said:**
> ```

sudo fdisk -l

```

will display all your partitions that are hooked up. For example, mine is:

```

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           5       40131   de  Dell Utility
/dev/hda2   *           6        9158    73521472+   7  HPFS/NTFS
/dev/hda3            9159       14500    42909615   83  Linux
/dev/hda4           14501       14593      747022+   5  Extended
/dev/hda5           14501       14593      746991   82  Linux swap / Solaris

```
So you can see my Windows partition is on /dev/hda2, and my Ubuntu partition is on /dev/hda3. For you, you may see /dev/**hdb1** or /dev/**hdb2** or whatever. Just find that partition that has HPFS/NTFS as format and mount it. Easy!:KS

Hmm, tried that, but, apparently, it's allready unmounted :S man i'm confused now. my windows partition is /dev/hdb1, but it's determined that it's allready unmounted. And it then has nothing next to it in /etc/fstab so i can't change it :p *looks around in despair*

---

### Post by Plankzt on 2007-02-09
bumpy bump, still stick =[

---

### Post by daou on 2007-02-09
> Hmm, tried that, but, apparently, it's allready unmounted :S man i'm confused now. my windows partition is /dev/hdb1, but it's determined that it's allready unmounted. 
When you list a hdd in fdisk, it just shows you what partitions you _can_ mount, not ones that are mounted. To see the partitions and peripherals that are mounted, you would run "mount -l". The things in /dev list devices that Linux has detected. But they aren't necessarily in use. (golden rule of Linux: everything is a file. A hard drive is a file, the mouse is a file. Everything is a file).

> And it then has nothing next to it in /etc/fstab so i can't change it  *looks around in despair*
Don't try playing with fstab yet. Once you are able to mount, then do the fstab.

Two easy steps to mount temporarily:

1: sudo mkdir /mnt/win

2: sudo mount -t ntfs -o user,umask=000 /dev/hdb1 /mnt/win

So basically this puts a NTFS type partition at /dev/hdb1 into /mnt/win. Then you can read it (although you cant write to it simply using these commands).

---

### Post by Plankzt on 2007-02-09
Woot got the drives sorted out, I've also managed to get it to boot up with the x1850, now to install the fuxxing drivers for it, basically need Catalyst, any ideas anyone?

Much appreciated.

---

### Post by daou on 2007-02-09
ATI driver howto:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

---

