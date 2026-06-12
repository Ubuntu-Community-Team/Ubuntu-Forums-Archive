---
title: "A noob USB questions?"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by TechStan on 2007-10-08
I have a USB 1.1 board in a pci slot.  Feisty Fawn 7.40 recognizes  it but it fails to work.  I've burned two days on this.   I am going to by a new 2.2 USB board. I have two questions.  First will Ubuntu recognize the new board, or will I have to manually configure the board. Secondly is there a brand i can buy that is known to work with 7.04 Feisty Fawn.

Thanks in advance
TS:popcorn:

---

### Post by corowakid on 2007-10-08
> **TechStan said:**
> I have a USB 1.1 board in a pci slot.  Feisty Fawn 7.40 recognizes  it but it fails to work.  I've burned two days on this.   I am going to by a new 2.2 USB board. I have two questions.  First will Ubuntu recognize the new board, or will I have to manually configure the board. Secondly is there a brand i can buy that is known to work with 7.04 Feisty Fawn.

Thanks in advance
TS:popcorn:

I've got a 4-port USB card in my PC, and Ubuntu detected it after the installation with no problems. As the software that comes with the cards covers the PC, I doubt whether they'd be of any use in Ubuntu.

My card is a no-name, so it seems Ubuntu isn't choosy.

Hope this helps

---

### Post by TechStan on 2007-10-08
Thank you. I was afraid of that. I deduct from this that the card I have in it more than likely will work but was miss configured during installation. I am a noob so please bare  with me is there any way to kill the Usb card and let ubuntu redetect it..

The Device type is VT82xxxxx UHCI USB 1.1 Controller it also states that the vendor is VIA technologies.

On OEM vendor it states wrong ID.

Here is my lspci
00:00.0 Host bridge: Broadcom CNB20LE Host Bridge (rev 05)
00:00.1 Host bridge: Broadcom CNB20LE Host Bridge (rev 05)
00:01.0 RAID bus controller: LSI Logic / Symbios Logic 53C1510 (rev 02)
00:03.0 VGA compatible controller: ATI Technologies Inc 3D Rage IIC 215IIC [Mach64 GT IIC] (rev 7a)
00:04.0 System peripheral: Compaq Computer Corporation Advanced System Management Controller
00:05.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 04)
00:0f.0 ISA bridge: Broadcom OSB4 South Bridge (rev 51)
00:0f.1 IDE interface: Broadcom OSB4 IDE Controller
03:04.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 08)
03:05.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 08)

and lsusb

Bus 001 Device 001: ID 0000:0000

Sorry for the long noob post but I will gladly post more info if needed.

Can anyone please help me.

---

### Post by skymera on 2007-10-08
yeah got a 4 USB 2 adaptor that goes  in a pci slot :D

---

### Post by BertP on 2007-10-08
I have an external hard drive that I used to backup my Windows  Computer which is formatted with the FAT32 format.   All I had to do was plug it into the USB port and everything was there using Nautilus to view my hard drive.   Any "mount" or "unmount" commands must have been automatically taken-care-of by the GUI software so I was able to access my harddrive in  a manner that  felt natural  and easy to a Windows user   

I don't see a corresponding "Add New Hardware" app in Gnome  so I suspect that you will have to install your usb card it with  terminal commands..   I am a newbie here and have no clue how to do this but I expect that there are many here that can help you with that.

Good Luck!

---

### Post by TechStan on 2007-10-08
I am off to take a shower and clean up from my Ubuntu stupor. i will go and pick up a 2.0 PCI card for giggles. [-o<  If this dose not fix it. I am in for some work and will be back to ask some questions?

---

### Post by TechStan on 2007-10-08
Bought a CompUSA USB 2.0 5port PCI card.  I booted up stuck a pen drive in and it showed up instanly.  It recognized the PCI card right away. Thanks to everyone who helped. you guys :guitar:  Much Joy=D>.

---

