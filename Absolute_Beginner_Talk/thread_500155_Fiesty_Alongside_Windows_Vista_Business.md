---
title: "Fiesty Alongside Windows Vista Business"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by Darklighter137 on 2007-07-13
Could someone please bring me up to speed on how successful installing Ubuntu next to Vista people are?  I would really like to use both, but I cannot endure a loss of time with Vista due to development obligations.  From what I've read, it seems to be a mixed bag.  Thanks!

---

### Post by Inxsible on 2007-07-13
> **Darklighter137 said:**
> Could someone please bring me up to speed on how successful installing Ubuntu next to Vista people are?  I would really like to use both, but I cannot endure a loss of time with Vista due to development obligations.  From what I've read, it seems to be a mixed bag.  Thanks!

I use a dual boot with Vista Home Premium. Seems to work fine. Although the only time I booted into Vista, was after I installed Ubuntu...to check if everything worked in Windows. :)

I don't need Windows at all ....except during Tax Time when I use TurboTax :). 
I don't like the idea of using the online TurboTax version.

---

### Post by confused57 on 2007-07-13
> **Darklighter137 said:**
> Could someone please bring me up to speed on how successful installing Ubuntu next to Vista people are?  I would really like to use both, but I cannot endure a loss of time with Vista due to development obligations.  From what I've read, it seems to be a mixed bag.  Thanks!
First, you should use Vista's partitioner to resize your Vista partition:
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

Here's a guide for using Vista's bootloader to boot Ubuntu:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

---

### Post by Darklighter137 on 2007-07-13
Hey, thanks guys.  I'm a CS major working with .NET seriously, so I certainly need Windows.  My heart lies with open source, and even my Mom and Dad are beginning to become interested.  Thank you for helping me get Ubuntu running once more on  my machine.  =)

---

### Post by Darklighter137 on 2007-07-13
Two quick questions:

1. If I install using the LiveCD and use the largest free space option, will it ask me where to put the boot loader?

2. Can I let Ubuntu do the partitioning of the free space for me, or will it mess up Vista (assuming I first made the free space in Vista)?

---

### Post by Inxsible on 2007-07-13
> **Darklighter137 said:**
> Two quick questions:

1. If I install using the LiveCD and use the largest free space option, will it ask me where to put the boot loader?

2. Can I let Ubuntu do the partitioning of the free space for me, or will it mess up Vista (assuming I first made the free space in Vista)?

I have always found it easier (and safer -IMHO) to select the manual partitioning. That way I know exactly where stuff is being installed.

Call me a stickler..

---

### Post by sailor2001 on 2007-07-13
answer #1 yes  answer#2 defrag vista first and no problem........ also set your boot order via sudo gedit /boot/grub/menu.lst

---

### Post by ReaderRat on 2007-07-13
> **Darklighter137 said:**
> Two quick questions:

1. If I install using the LiveCD and use the largest free space option, will it ask me where to put the boot loader?

2. Can I let Ubuntu do the partitioning of the free space for me, or will it mess up Vista (assuming I first made the free space in Vista)?

1.) No. I did not for me.

2.)Yes. Assuming you make space with Vista first.

EDIT: Sorry, I mis understood #1. I'm wrong.
And, as he says, defrag first.

---

