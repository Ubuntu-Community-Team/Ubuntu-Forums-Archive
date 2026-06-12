---
title: "network printer"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by rlutker on 2007-04-01
I installed Ubuntu 6.06 on my computer.  All other computers on my home network have windows xp on them.  One of the windows computers have a Lexmark x73 printer  connected to it.  I have successfully networked the computers together.  I have not had any problem sharing files beetween the computers.  I have been having a lot of difficulty printing from my ubuntu computer.  I used ubuntu print setup wizard to setup printing to a network printer.  When asked for a model, I picked the lexmark z42  so I could use the z42 with cups and gutenprint v5.0 drivers.  Setting up the printer went smoothly with no errors an it seemed to find the printer with no problem, but when I try to test print a page or print a document the printer sends through a blank sheet of paper.

---

### Post by dstew on 2007-04-01
In order to share a printer on a Windows network, you need to use Samba. If you have not installed Samba yet, you can do this from Add/Remove programs or Synaptic.

If you have Samba installed, you need to access the shared printer using Samba. I access my printer which is plugged into my wife's XP computer using this name:

smb://MARYS/Printer2

The smb:// means that this printer will communicate using the Samba protocol. MARYS is the server name, and Printer2 is the shared printer's name.

---

### Post by rlutker on 2007-04-01
I have already installed samba.  I used samba to setup my network and share files.
I had also shared my windows printer as you stated.  Everything went well until I tried to print. All I got from my printer was a blank paper.  The windows computer with the printer even went through the motions of telling be when the printing started and when the printing was complete.

---

### Post by dstew on 2007-04-02
Did you create your CUPS printer as a samba share also? (smb://server/printer)

---

### Post by rlutker on 2007-04-02
yes

---

### Post by david_kt on 2007-04-02
Have you tried to select drv_z42 driver instead of Gutenprint? Mostlikely it is driver related problem. And if there is bidirectional support ( I am not sure whether or not your printer have bidirectional support), try to disable it.

Normally for network printing we do not even need to install samba.

DK

---

### Post by dstew on 2007-04-02
I think Samba is required for Windows sharing, but not for using a true network printer.

I remember something else. When I first installed my printer, it printed funny, because its default page size was A4, and I had US letter in the printer. Maybe it is some setting like that.

---

### Post by rlutker on 2007-04-02
I tried the z42 driver first.  The printer did nothing and when I checked the what was happening with the job, I noticed that it said job-stopped.  I also tried messing with page size with no success.

---

### Post by david_kt on 2007-04-02
> **rlutker said:**
> I tried the z42 driver first.  The printer did nothing and when I checked the what was happening with the job, I noticed that it said job-stopped.  I also tried messing with page size with no success.

Have you checked bidirectional support on your printer? If it has bidirectional support, you should try to disable it.

DK

---

### Post by rlutker on 2007-04-03
Yes.  I've unchecked bidirectional support and still had the same problems.

---

### Post by compmodder26 on 2007-04-03
If this printer is connected to a Windows box, then any job you send it from the Ubuntu box should also pass through the windows driver.  Try setting the printer up as Raw in Ubuntu and see what happens.

---

### Post by david_kt on 2007-04-03
> **rlutker said:**
> Yes.  I've unchecked bidirectional support and still had the same problems.

What you could do is to try other printer driver. Try generic printer driver for example, and choose the one similar one to your windows driver (for example PCL5 e, your windows printer name have pcl5 e).

DK

---

### Post by rlutker on 2007-04-03
As far as installing other printer drivers other than the ones I have to select from or setting the printer up as raw I am unsure as to what to do.  Help with either is appreciated.  My printer is a Lexmark X73 and it is connected to a windows XP computer through a usb port. I am using ubuntu 6.06 operating system.

---

### Post by compmodder26 on 2007-04-04
To choose raw printing, in the printer setup dialog where you choose the make and model of your printer, instead of selecting Lexmark, choose "Raw", the select "Queue" from the list.  As for selecting a different driver for your make and model of printer, there should be a drop down box near the bottom of the dialog where you can select different drivers.

---

### Post by rlutker on 2007-04-04
I tried setting up printer as raw.  After I click print a test page, the computer indicates printing one job and nothing is happening.  When I tried to find the jobs so I could cancel it, there was no job to cancel.  With the job still running, I am unable to remove the printer setup.  How can I cancel the printing job?

---

