---
title: "Help, vista repair broke GRUB"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by steelmole on 2008-02-03
Ok, so I installed vista, then tried to edit the boot menu to get ubuntu and vista to boot.  This stopped vista booting.  I used the vista cd to get vista booting again (it worked automatically) but now I can't boot ubuntu.  When I try to boot ubuntu I get "loading bootpart 2.60" and then "cannot load from hard disk"

I've tried running live cds to somehow repair grub, but I'm not exactly sure what to do.  Basically I want to use vista's bootloader to boot to ubuntu too.

---

### Post by jan quark on 2008-02-03
try to restore the boot loader with the super grub disc

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

ask for help if needed

---

### Post by steelmole on 2008-02-04
Nothing seems to want to boot.  Every live cd I have seems to hang.  Ubuntu shows the ubuntu logo for a while then goes to a black screen with a cursor flashing.  Damn small linux does a similar thing but with more writing. I hope this grub cd is different.

---

### Post by steelmole on 2008-02-04
Ok, so I used the grub boot cd and did this:

```
root (hd0,6)
setup (hd0,6)
```

Now when I boot I get to the windows boot loader(what I wanted) and then when I select ubuntu I get grub.  The ubuntu logo comes up but then stops at a black screen with a cursor blinking in the top left corner.  Any help?

---

### Post by dstew on 2008-02-04
> when I select ubuntu I get grubDo you get the grub menu, or does it just flash grub and go to Ubuntu?> The ubuntu logo comes up but then stops at a black screen with a cursor blinking in the top left cornerIs this the dark Ubuntu splash screen with the orange bar under the Ubuntu logo? If so, you may be having trouble with the spash screen interacting with your display hardware. To get it to boot, you can edit the kernel line from the grub menu. Press 'e' at the grub menu, select the kernel line using the up-down arrows, press 'e' again, and remove the words **quiet splash** from the line. Press enter, then 'b' to boot. If it works, you can alter the grub menu to permanently remove these words.

---

### Post by steelmole on 2008-02-04
I get the grub menu first.  I'll try the quiet boot option, but I've had this screen before and it hasn't caused problems.

---

### Post by dstew on 2008-02-04
Well, there are of course other possibilities. But first we get rid of the splash screen to see what else is going on. You will be able to see kernel messages, and maybe get some clues. Or, it might boot...

---

### Post by steelmole on 2008-02-06
the last few things it says are :

```
attempting manual resume
kinit: No resume image, doing normal boot
kjounald starting. Commit interval 5 seconds
EXT3-fs: sda7: orphan cleanup on readonly fs
```

And then it doesn't do anything else.

---

### Post by dstew on 2008-02-06
Boot an Ubuntu Live CD, open a terminal window and enter the command```
sudo fdisk -l
```Post the result to the forum.

---

### Post by steelmole on 2008-02-15
Live CDs don't seem to work.  I've tried ubuntu 7.10 64bit (the disc I installed from), 32bit too and damn small linux.  They work on other computers.

---

