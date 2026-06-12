---
title: "Problems with GRUB, yes I've checked the other threads..."
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by herrma29 on 2007-01-15
Hi all, I recently installed Mandriva and made the mistake of letting it take of GRUB for me. After the install and the reboot, I realized that Ubuntu had been removed from the GRUB menu and only Mandriva and Linux were left. All of my partitions are intact, it's just that GRUB is recognizing Ubuntu.

I tried the GRUB fixes, where I go into the terminal, access grub, and do the fund /boot thingy, it gave me two different responses. one was hd0,1 and the other hd0,3. I tried it with both of them and nothing worked.

I also tried going through the install process and choosing not to format the drives once I got to that part, but it gave me an error message saying that I had to format at least the swap and / partitions.

Does anyone have a clue as to what I can do to access Ubuntu?!? I even tried to use Super GRUB Loader, but everything I tried in it just went to the Mandriva GRUB screen or Windows.

---

### Post by bodhi.zazen on 2007-01-16
There are several ways yo can do this.

I assume your root partitions as follows:

Ubuntu = /dev/hda2 = (hd0,1)

Mandriva = /dev/hda5 = (hd0,4)

Lets boot to Mandriva.

1. Look in the Mandriva system tools and see if ther is not a configuration tool for boot/grub. If so, add Ubuntu ..

**If that fails ...**

2. Lets re-install grub.

In Mandriva, open a termainal.

```
sudo grub
```Should open the grub prompt ..

OK now:

```
root (hd0,1)
setup (hd0)
quit
```

Re-boot

**If that fails ...**

3. If all that fails, you will need to edit /boot/grub/menu.lst.

boot either Ubuntu or Mandriva

Mount the other root. Let us assume Ubuntu since we just re-installed grub.

```
sudo mkdir /media/mandriva
sudo mount /dev/hda5 /mnt/mandriva
gksudo gedit /boot/grub/menu.lst &
gksudo gedit /media/mandriva/boot/grub/menu.lst
```

Now copy the mandriva stanza form /media/mandriva/boot/grub/menu.lst to /boot/grub/menu.lst

The mandriva stanza will look like this

title Mandriva .....
root (hd0,4)
kernel .....
....

The only potential problem is that whenever you update the mandriva kernel you will need to manually update the kernel and initrd lins of your Ubuntu /boot/grub/menu.lst
[b]
=====
Advanced
=====[/b]

You can fix this by installing grub into the mandriva root partition.

Boot Mandriva

```
sudo grub
root (hd0,4)
setup (hd0,4)
quit
```

Now boot Ubuntu

```
gksudo gedit /boot/grub/menu.lst
```

Change the mandrive stanza to:

title Mandriva
chainloader +1
boot

When you select Mandriva you will see a second grub screen. Choose Mandriva.

In Mandriva you can set the default to Mandriva and reduce the timeout to 0 and you will then not see the second menu, but better to do this once it is working :p

HTH

---

### Post by herrma29 on 2007-01-16
Ok, so I went into mandriva and went to the grub setup that Mandriva has. From there, it gives me the option to add more systems to the list and I selected my Ubuntu partition. It then tells me to select the image file to use, and gives me one option:

/boot/vmlinuz-2.6.17-5mdvlegacy.

I selected this image file, restarted and went to it in grub. When it loaded up, it didn't give me a graphical load, but instead went through the terminal-like screen and then let me log in. A lot of things in Ubuntu were not working. It told me it could not recognize my speakers, my internet wasn't connecting etc.

Is this the correct image to use, or should I be using a different one? And if so, how do I go about doing that?

P.S. I just noticed an advanced button to click on when cofiguring the loader, this gives me the following options:

video mode, with a drop down list of different resolutions

initrd, with these .img files:
  /boot/initrd-legacy.img
  /boot/initrd-2.6.17-5mdvlegacy.img
  /boot/initrd.img

and network profile, with a drop down that says default.

My best guess is that one of these is the image I am supposed to be using, but I would like to be sure on this.


EDIT: The basic screen where I select the partition and the image also gives me the option to append it, if that helps at all.

Thanks a lot, 

Chris

---

### Post by bodhi.zazen on 2007-01-16
Use the initrd to match your kernel:

/boot/initrd-2.6.17-5mdvlegacy.img

title Ubuntu
root (hd0,1)
kernle /boot/vmlinuz-2.6.17-5mdvlegacy root=/dev/hda2 ro splash
splash
initrd /boot/initrd-2.6.17-5mdvlegacy.img

HTH :)

---

### Post by herrma29 on 2007-01-16
I'm afraid I'm not following you. Where should I put all of those different lines?

I attached a screenshot of the boot configuration tool to give you an idea of what I'm working with. If I need to open up some file and add that stuff in there, then I need you to tell me that. I really have no idea what the initrd is or anything like that, I'm really new to all of this, so if you can be as explanative with me as possible, it's very needed :)

Thanks for the help so far!

---

### Post by bodhi.zazen on 2007-01-16
On that GUI:

Image = vmlinuz-2.6.17-5mdvlegacy root=/dev/hda2 ro splash

You may need to put ro splash in the append box, I am not sure with the Mandriva tool :(

Initrd = initrd-2.6.17-5mdvlegacy.img

Again, for both of those I am not sure if we are talking /boot/vmlinuz-... and /boot/initrd .....

If the gui fails,

open a terminal and:```
gksudo gedit /boot/grub/menu.lst
```

Post the Ubuntu lines (stanza) and I can help you with a manual edit ....

It will look something like this:
> title Ubuntu
root (hd0,1)
kernel /boot/vmlinuz-2.6.17-5mdvlegacy root=/dev/hda2 ro splash
splash
initrd /boot/initrd-2.6.17-5mdvlegacy.img
boot

(there was a small typo in my last post, with the spelling of "kernle"


Translation to English :p
To boot we need to identify the partition we will boot AKA root (hd0,x)

What kernel to boot and the root partition in Linux speak AKA /boot vmlinux-xyz (kernel) root=/dev/hda2 (linux root partition) ro (we mount the kernel ro) splash (splash = pretty picture during boot)

For Ubuntu I have to list splash twice ....

initrd is an initial ram image for your hardwdare, things like your hard drive and ethernet card (which is why they failed without initrd).

boot - Tells grub to go ahead and boot already :)

You can also change your Ubuntu stanzas to:

title Ubutnu
chainloader +1
boot

See my previous post under "advanced"

---

