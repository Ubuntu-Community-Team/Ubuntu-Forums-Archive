---
title: "dual boot two hard drives"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by northernjohn on 2008-02-25
i am completely new to this!
I really want to move to ubuntu, but am scared of losing the windows that my wife insists on using- and would make my life hell if it didn't work.
I have two hard disks in my laptop. can i make one windows and one ubuntu? ( one is currently unused both are 50+GB:confused:)

---

### Post by mkoehler on 2008-02-25
Sure you can, just make sure that all of your windows data is on one HDD and download the live cd.  Restart your computer with the live cd in it, then you can run the installation script.  From there, you will be able to select which partition / HDD that you'd like to use for the installation.

Good luck, and ask if you have any more questions!

---

### Post by northern lights on 2008-02-25
You absolutely can.

Upon the end of any K/X/Ed/Ubuntu install a bootloader will be written to your MBR, it goes by the name of [GRUB]("http://www.gnu.org/software/grub/"). If Windows was previously setup, it will automatically appear in the newly created bootmenu.

Just make sure you install Ubuntu on the second HDD (or alternatively a partition on the first), and do not choose "Use entire disk" or format the first partition of your first harddrive (the windows partition).

---

### Post by Duck2006 on 2008-02-25
Some reading on installing.

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

What ver of windoze is on your laptop?

---

### Post by incen on 2008-02-25
I have this on my computer as well. If you're worried about this setting, then you know it's definitely fine. I have one hard drive with Windows XP and the other one Ubuntu.
However, make sure you have Windows installed first (I think you won't remove the old one, right?) and then install Ubuntu with the LiveCD.
While installing, just change the partition with the other drive and leave Windows drive as what it is now. :)

---

### Post by northernjohn on 2008-02-27
so it's really that simple? the ubuntu installation will partition the hard drives when i nstall it? will i be able to access my music and pictures?
Really how technical will i need to be? setting up wireless internet connections etc concern me

---

### Post by northernjohn on 2008-02-27
it's xp media centre. is all my wireless internet stuff easy to do?

---

### Post by markbusu on 2008-02-27
Yup it is really simply... i just did this myself and new to Linux Operating Systems...

You do not need to be worried by modifying Grub (Boot Loader) also... since its handled during the installation of Ubuntu...

When Booting... you will just need to simply select which OS you wish to boot... Ubuntu or Win Xp..

With regards to Connecting to a wireless Access Point... the only thing you need to be concerned is with finding the correct driver for your Wifi Card... 

Generally using Restricted Drivers should sort your issue... What Wifi Card do you have??

---

### Post by Duck2006 on 2008-02-27
> **northernjohn said:**
> so it's really that simple? the ubuntu installation will partition the hard drives when i nstall it? will i be able to access my music and pictures?
Really how technical will i need to be? setting up wireless internet connections etc concern me

Setting up ubuntu is, easy, but setting up the wireless internet may be a bit more work. What wireless card are you trying to set up?

---

