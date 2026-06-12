---
title: "booting"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by gamehunter101 on 2007-06-24
I am dual booting xp,vista and Ubuntu.I want to boot directly into vista with out going through grub/the linux selection os menu.How can I achieve this task.Thanks for your help!

---

### Post by ajmorris on 2007-06-24
> **gamehunter101 said:**
> I am dual booting xp,vista and Ubuntu.I want to boot directly into vista with out going through grub/the linux selection os menu.How can I achieve this task.Thanks for your help!

so you want the windows loader to have the linux entries?

---

### Post by logos34 on 2007-06-24
either put grub on a boot floppy or cd, and restore vista bootloader to mbr; OR continue to boot to vista through grub but enable the 'hiddenmenu' option and 'timeout  0' in menu.lst (with vista as 'default' boot OS),; OR add linux to vista bootloader using something like easyBCD or openBCD editor.

---

### Post by gamehunter101 on 2007-06-24
> **logos34 said:**
> either put grub on a boot floppy or cd, and restore vista bootloader to mbr; OR continue to boot to vista through grub but enable the 'hiddenmenu' option and 'timeout  0' in menu.lst (with vista as 'default' boot OS),; OR add linux to vista bootloader using something like easyBCD or openBCD editor.

 how do i go about doing that?i am a linx nub that doesn't know the linux commands

---

### Post by logos34 on 2007-06-24
> **gamehunter101 said:**
> how do i go about doing that?

[URL="https://help.ubuntu.com/community/GrubHowto/BootFloppy"]
https://help.ubuntu.com/community/GrubHowto/BootFloppy[/URL]

[http://neosmart.net/dl.php?id=1]("http://neosmart.net/dl.php?id=1")
(you'll have to google for the specifics on adding linux to menu)

---

### Post by gamehunter101 on 2007-06-24
> **logos34 said:**
> [URL="https://help.ubuntu.com/community/GrubHowto/BootFloppy"]
https://help.ubuntu.com/community/GrubHowto/BootFloppy[/URL]

[http://neosmart.net/dl.php?id=1]("http://neosmart.net/dl.php?id=1")
(you'll have to google for the specifics on adding linux to menu)

thanks a ton for your help as well as the others. ;)(doesn't have floppy drive or floppy /will try to use a usb drive)

---

### Post by logos34 on 2007-06-24
Copy and post your menu.lst:

Open a terminal and type:

> c**at /boot/grub/menu.lst**

---

### Post by logos34 on 2007-06-25
Since you don't have a floppy drive here's a howto for a **Grub boot CD**:

[http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD_002dROM.html]("http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD_002dROM.html")

Note: **stage2_eltorito** can be found in /lib/grub/i386-pc


OR just use [SuperGrub CD]("http://supergrub.forjamari.linex.org/") to boot ubuntu

---

### Post by logos34 on 2007-06-25
well, I was waiting for you to post your menu.lst.

You can do this:

**sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup**
**gksudo gedit /boot/grub/menu.lst**

Change the following lines thus:
> 
**default   saved**

Or,
Count the number of 'Title' lines (without a hash #) from the first ubuntu kernel to the windows entry.  Start counting at 0.  So if windows is the 5th title line (0,1,2,3,4), use '4':
> 
**default   4**

Change timeout:
> **timeout   0**

Remove the '**#**' from hiddenmenu:
> **hiddenmenu**

Make sure there is a **savedefault** option n the windows entry at the bottom of the page.  

Now you should boot into windows vista as quickly as possible without seeing the grub menu.

edit: to boot into ubuntu instead, hit the** ESC** key as soon as you see 'grub loading...' at bottom of screen to pull up menu, then choose the first kernel

---

### Post by Computer Guru on 2007-06-25
The Linux-Vista directions for EasyBCD can be found in the docs @ [http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
 
Cheers! :)

---

### Post by logos34 on 2007-06-25
> **Computer Guru said:**
> The Linux-Vita directions for EasyBCD can be found in the docs @ [http://neosmart.net/display/EBCD/Linux](http://neosmart.net/display/EBCD/Linux)
 
Cheers! :)

Actually the '/wiki/' got left out of that link.  Here's the correct URL:
> [http://neosmart.net/wiki/display/EBCD/Linux]("http://neosmart.net/wiki/display/EBCD/Linux")

Thanks Computer Guru!

---

### Post by Computer Guru on 2007-06-25
Ouch.. Sorry about that, and thanks for correcting me back there, logos34!
 
I fixed the original link (and that stupid typo!) in the post lest anyone stumble upon it by accident.
 
I went ahead and added the Linux-Vista documentation link to the Ubuntu Wiki/Help page at the bottom in the references section... figured it might come in useful there.

---

