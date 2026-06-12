---
title: "Installing Linux ATI 8.37.6 Driver"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by rpgaction on 2007-06-13
I would like to preface this plea for help with the statement that this can more or less be considered my first time really using Linux, in the hopes to provide some sort of explanation for whatever completely and utterly obvious error I have committed.

So, basically, I downloaded the .run file from here: [http://ati.amd.com/support/drivers/linux64/linux64-radeon.html](http://ati.amd.com/support/drivers/linux64/linux64-radeon.html)

And I was following the instructions on the Installer Instructions page that the above page links to. However, after I executed the file, no sort of wizard-like installer pops up like the guide says it will. All that happens is a temp folder is made, then deleted, and nothing else happens. Here's the exact output:

```
god@Satan:~/Desktop$ sh ./ati-driver-installer-8.37.6-x86.x86_64.run
Created directory fglrx-install.t13621
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.37.6..................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Detected configuration:
Architecture: x86_64 (64-bit)
X Server: X.Org 7.1 and later releases 64-bit
Removing temporary directory: fglrx-install.t13621
god@Satan:~/Desktop$ sudo sh ./ati-driver-installer-8.37.6-x86.x86_64.run
Created directory fglrx-install.O15409
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.37.6..................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Detected configuration:
Architecture: x86_64 (64-bit)
X Server: X.Org 7.1 and later releases 64-bit
Removing temporary directory: fglrx-install.O15409

```

Thanks in advance for any help.  :D

Edit - Oh! If it matters, I'm using an X1800 XT

---

### Post by AAM on 2007-06-13
need to know whether using Feisty, or what?
Tried to install using Restricted Drivers option under System?

more information please

---

### Post by rpgaction on 2007-06-13
Perhaps I need to rephrase my opening statement more bluntly: I have no idea what you're talking about.

I downloaded the latest version of x64 Ubuntu tonight, which I believe is 7.04, and everything is currently set at default after going through the automatic updates. I'm going to sit down and read the documentation, I'd just prefer to have my video settings configured comfortably first - right now the max resolution is 1024x768, which I can't stand.

All I've tried is what I posted. Any help based on that would be appreciated.

---

### Post by neo.patrix on 2007-06-13
Please DON'T install anything for ATI Cards other than driver available from ubuntu repository.

Maybe there is a newer version available, it is not stable on Ubuntu. The Kernel module will not work properly , in some case won't even integrate. I have tried it and had 2 sleepless nights trying bring my system back to normal.

---

### Post by w4ett on 2007-06-13
This:  [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)  is as about as good a set of instructions as any for the ATI X**** series cards.

---

### Post by shae on 2007-06-13
> **neo.patrix said:**
> Please DON'T install anything for ATI Cards other than driver available from ubuntu repository.

Maybe there is a newer version available, it is not stable on Ubuntu. The Kernel module will not work properly , in some case won't even integrate. I have tried it and had 2 sleepless nights trying bring my system back to normal.

I have never had a problem using the newest from ati's site.  How did you install yours?  The kernel module should work properly if you have the needed programs as it is compiled against your current kernel.  This however does mean you have to recompile it whenever you update the kernel.

I follow the instructions for installing the official driver found here(method 2): [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide")

---

