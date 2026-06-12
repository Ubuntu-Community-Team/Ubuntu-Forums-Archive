---
title: "Not recognizing my PCI sound card."
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by HarrisonHopkins on 2006-06-24
For some reason, Ubuntu doesn't reconize my sound card. I can tell this because when I do lspci in terminal, no sound card is listed. This is all taht comes up:

0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bri dge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridg e (rev 03)
0000:00:0f.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev  78)
0000:00:14.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:14.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:14.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:14.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:01:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G200 AGP (rev 01)


How can I get my sound card to be recogized.

---

### Post by Apple 101 on 2006-06-24
What brand and model is it?  Also, have a look at the [Alsa Sound Project]("http://www.alsa-project.org") to see if it is supported in a new release.

---

### Post by HarrisonHopkins on 2006-06-24
I have no clue, I'd have to open the case to check that.

EDIT: Just opened, from the looks of it, it is just a Generic. I see no brand on it anywhere.

If it helps, it doesn't look like it is in a standard PCI slot. It is in a slot that is about an inch longer than the PCI.

---

### Post by Apple 101 on 2006-06-24
Do you any other OS's to check what it is?

---

### Post by HarrisonHopkins on 2006-06-24
No, when I got this computer the Windows 95 that was on it was too messed up to do anything right, so I instantly installed Xubuntu Alternative onto it.

---

### Post by Apple 101 on 2006-06-24
Try this (I'm using Ubuntu so the location may be different):
System --> Preferences --> Sound

There should be a card listed somewhere on the bottom of that window.

---

### Post by HarrisonHopkins on 2006-06-24
Applications->Settings->Mixer Settings

Nothing really special here at all, just a dropdown box that has nothingbut default in it and a useful controls box with nothing in it.

---

