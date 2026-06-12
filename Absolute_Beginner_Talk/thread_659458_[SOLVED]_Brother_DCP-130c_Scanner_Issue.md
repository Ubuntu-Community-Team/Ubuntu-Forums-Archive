---
title: "[SOLVED] Brother DCP-130c Scanner Issue"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by Paul Vega on 2008-01-05
Kia Ora All

I have successfully installed the Printer and am very pleased with the results however I am now experiencing difficulty in getting the Scanner to work. I have called up the FAQ page on Brothers Web page and have the following instructions:

[For Ubuntu Users (version 6.06 or later)]

1. Open the file "/etc/udev/rules.d/45-libsane.rules" with an editor.
2. Add the following description to the file as below:

=================
#brother
SYSFS{idVendor}=="04f9",MODE="666",GROUP="scanner"
LABEL="libsane_rules_end"
=================

3. Restart the OS.

I have found the file using gedit and inserted the description as listed but when I try to save the changes it tells me that:
[B]
Could not save the file /etc/udev/rules.d/45-libsane.rules.[/B]
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

Can someone please explain to me how I can edit this file? 

I also see that there are differences between the existing file format and the requested changes. I have copied and pasted the two existing lines of instruction and the recommended lines.

# Brother MFC 9600
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="0101", MODE="664", GROUP="scanner"
# Brother MFC 7300c
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="0106", MODE="664", GROUP="scanner"
# Brother DCP-130c
SYSFS{idVendor}=="04f9",MODE="666",GROUP="scanner"
LABEL="libsane_rules_end"

There is no apparent product id in the recommended line and it also ends with a LABEL instruction that is not on the others (or on any of the other manufacturers product).
Is this important? 

Paul Vega

---

### Post by gn2 on 2008-01-05
You'll need to use sudo to modify that file.

Try
 ```
 sudo gedit /etc/udev/rules.d/45-libsane.rules 
```

---

### Post by Paul Vega on 2008-01-06
Thank you very much...Scanner now works.

---

