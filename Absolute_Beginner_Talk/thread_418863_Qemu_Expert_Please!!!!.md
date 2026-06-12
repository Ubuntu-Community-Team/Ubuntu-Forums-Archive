---
title: "Qemu Expert Please!!!!"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by esc0587 on 2007-04-22
I am trying to run DSL inside of Ubuntu 6.10.  I have installed qemu and kqemu but don't know the command to run DSL inside of Ubuntu.  Please Help.

---

### Post by crispy_420 on 2007-04-23
I think you just execute it as such:

qemu "file.bat"

You did get the dsl-embedded version right?

---

### Post by AAM on 2007-04-23
dowmload qemu-x.x.x-i386.tar.gz and DSL.iso from where ever, then:
> sudo tar xfvz qemu-x.x.x-i386.tar.gz -C /
Then create a 6 GB virtual hard disk image (called DSLdisk) with:
> qemu-img create DSLdisk.img 6G
Then run qemu with 256MB RAM with
> qemu -cdrom DSL.iso -hda DSLdisk.img -boot d -m 256
give that a try

---

### Post by crispy_420 on 2007-04-26
Or check out this project:

[http://qemulator.createweb.de/index.php4?aliasdoc=213](http://qemulator.createweb.de/index.php4?aliasdoc=213)

---

### Post by darkworld on 2007-04-29
ive got dsl running in qemulator. If your still stuck pm me.

---

### Post by 3rdalbum on 2007-04-29
> qemu -boot d -cdrom 

(that's a space after "-cdrom"). Now drag the DSL disc image to the terminal, switch back to the terminal window and press Enter.

If you want an easier virtualisation solution, I suggest downloading and installing Virtualbox. ([www.virtualbox.org)](www.virtualbox.org)). It is completely graphical.

---

