---
title: "Running Ubuntu Virtually on Vista"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by Aurora@FleetBuzz on 2008-02-27
I just purchased a Dell Inspiron 1525 with Vista Home Premium.  Before I set it up for dual booting, I was hoping to get Gutsy running virtually.  I've never had any luck on my old box with half a gig of RAM, so I loaded this new machine with 3 gig of RAM, which hopefully will do the trick.  What's the best program to use:  Virtual PC 2007, VMWare Server, or Virtual Box?

Are there any tutorials available on how to do this?

Appreciate any suggestions.  Thanks.

---

### Post by Sordelka on 2008-02-27
Just download the live cd and run from it =)

---

### Post by Aurora@FleetBuzz on 2008-02-27
Thanks, but I need it on the hard drive and virtualization seems to be the way to go.  I may want to add other OS's as time goes by.

---

### Post by Yes on 2008-02-27
I use Virtual Box whenever I need to run something in a vitrual enviorment, I find it to be quite easy.

To install Ubuntu on it, download the Gusty iso from ubuntu.com, then install Virtual Box.  Open it, and click the "New" button.  It'll take you through the setup, it should be pretty self explanitory (It asks you stuff like how much RAM do you want it to use, how big should the hard drive be, etc.).  Once it's set up, it should take you back to the orignal screen.  Now click the "settings" button, and go to CD/DVD-ROM.  Check off "Mount CD/DVD Drive", and then select the "ISO Image File" button.  Click the folder icon next to it and click the "Add" button.  Find the iso you downloaded and select it.  Then all you have to do is click the "start" button and it should boot into Ubuntu.

---

### Post by philidox on 2008-02-27
Virtual Box all the way!

---

### Post by Aurora@FleetBuzz on 2008-02-27
Thanks to all.  Does Virtual Box run on Vista?  I wasn't sure.  How much RAM should be allocated for Gutsy?

---

### Post by oilchangeguy on 2008-02-27
Microsoft also has free virtual software:
[http://www.microsoft.com/downloads/details.aspx?familyid=04D26402-3199-48A3-AFA2-2DC0B40A73B6&displaylang=en](http://www.microsoft.com/downloads/details.aspx?familyid=04D26402-3199-48A3-AFA2-2DC0B40A73B6&displaylang=en)
and it will run on vista.

---

### Post by philidox on 2008-02-27
With VirtualBox you can set the allocation, in other words its up to you

---

### Post by Yes on 2008-02-27
There's a Windows verison, no idea if it'll run in Vista.

If you just want to see what it's like, you won't need much for Gusty (maybe about 512 MB), if you want to do more intensive things (like run Compiz), you should use 1+ GB.

---

### Post by the_doc on 2008-06-06
Ok, sorry for resurrecting an oldish post, but in case anybody else was looking for an answer VirtualBox runs fine in Vista, even adding the guest to an internal network.  I have both Edgy Eft and Hardy Heron running with no problems.

---

