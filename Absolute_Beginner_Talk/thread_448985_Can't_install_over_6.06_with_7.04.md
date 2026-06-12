---
title: "Can't install over 6.06 with 7.04?"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by Bragador on 2007-05-19
Ok I received my 7.04 ubuntu cd yesterday and I wanted to install it tonight. I have put the cd in my cd drive and I have retarded my computer. I then selected stat/install ubuntu and then when the desktop booted I selected install. The problem is that my computer refused to format my first partition in ext3 (I selected guided install, full hard disk install mode). An error occurred while trying to format the first partition and the installation was canceled. All I wanted was to do a fresh install and format everything so I'm wondering if ubuntu has some form of protection to forbid that kind of thing...

Can anyone help?

Thanks for your time...

---

### Post by justin whitaker on 2007-05-19
> **Bragador said:**
> Ok I received my 7.04 ubuntu cd yesterday and I wanted to install it tonight. I have put the cd in my cd drive and I have retarded my computer. I then selected stat/install ubuntu and then when the desktop booted I selected install. The problem is that my computer refused to format my first partition in ext3 (I selected guided install, full hard disk install mode). An error occurred while trying to format the first partition and the installation was canceled. All I wanted was to do a fresh install and format everything so I'm wondering if ubuntu has some form of protection to forbid that kind of thing...

Can anyone help?

Thanks for your time...

There is no protection that I know of, although I never tried upgrading or installing with the desktop cd: I usually use the alternative cd. 

I know, what a luddite!

You could try booting the system in repair mode, and format the disk from scratch. I think you can cfdisk from repair...

---

### Post by RedSquirrel on 2007-05-19
You could wipe the drive clean with [KillDisk]("http://www.killdisk.com/downloadfree.htm") just to be sure there's nothing there before you do the feisty installation.

---

### Post by Bragador on 2007-05-22
Thanks guys.

I tried again this morning and I couldn't boot in safe mode on the live cd so I tried again with the "normal mode". I don't know why but this time it worked. It must have been a random bug the first time I tried. :/

I'm now on feisty fawn :D

---

