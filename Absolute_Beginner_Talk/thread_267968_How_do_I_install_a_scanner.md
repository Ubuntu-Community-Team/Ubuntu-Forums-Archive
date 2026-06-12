---
title: "How do I install a scanner?"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by limitedmage on 2006-09-29
Hi,

I have a HP Deskjet All-In-One F380 printer/scanner/copier. I installed the printer on Ubuntu and it works fine. But I can't seem to be able to install the scanner part. I open XSane Image Scanner and I get a 'no devices available' dialog. I searched the HP website, and it only has drivers for Windows and Mac OSX. Any ideas?

---

### Post by pseudonym on 2006-09-29
Try plugging it into a different USB port. That's helped me in the past.

Also, how new is your scanner? To check linux support you can go to the xsane website [www.xsane.org](www.xsane.org) .

---

### Post by Fedz on 2006-09-29
If you goto:
Applications > Graphics > Gimp Image Editor:

When open goto File > Acquire > XSane

Is their a device listed (scanner need not be active to see)?

Also in System > Administration > Synaptic Package Manager > search for Xsane.

Is libsane, Xsane and Xsane-Common installed?

Also in search look for hplip OR Hpaio and install.

Does this resolve the problem ;-)

---

### Post by limitedmage on 2006-09-29
It still hasn't worked. libsane, xsane, xsane-common and hplip are all installed. Well, looks like I'll have to use Windows to scan. Either way I'm going to edit the images in Photoshop.

EDIT: Ok, I found the problem. The scanner required HPLIP 0.9.9+, Ubuntu came with 0.9.7 and did not upgrade this package. I installed the latest version (1.6.7, i think) and now it works perfectly!

---

