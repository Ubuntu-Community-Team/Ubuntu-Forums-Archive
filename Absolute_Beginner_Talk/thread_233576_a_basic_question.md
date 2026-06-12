---
title: "a basic question"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by redmond on 2006-08-10
I have Ubuntu server installed and franly have bitten off WAY more than I can chew at the moment!! more postings about that another time.. I need help!!

But I digress.. my question this time is a simple one.. am I able to install the desktop version of ubuntu on another partition, keeping the server one I have setup? I have the room and a blank partition.. I assume grub will find it and add it to the boot options.. well the server I guess as the new install will replace the current boot loader I'm assuming..

I have also setup the home directory on the server on a seperate partition.. can they "share" this directory.. the server and desktop versions? or will the desktop remove everything there whne I install it (assuming I change the default option and set the same partition as the home)

I'll leave the server questions till i do a bit of research and answer some questons myself..

Red

---

### Post by kaffelars on 2006-08-10
I'm pretty sure you can have more than one installation if they have their own /-partition (though I have never tried).

I'm absolutely sure that the /home-partition can be shared, as long as you choose **not** to format this partition during the install. However this can give some unwanted effects, as all your settings etc. are stored here. 
A simple example: if you have some applets installed on the desktop installation, you will most likely get error messages on the server installation if these applets are not installed there.

For documents, images etc. this shouldn't be a problem.

---

### Post by Tomosaur on 2006-08-10
The problem here is that normal Ubuntu CD doesn't give you the OPTION of installing Grub, it just does it anyway. Lots of people are having problems because of this (because Grub gets confused as to which menu.lst file it's supposed to use), and you need to fiddle with both files to get it back to normal. Try using the so called 'alternate' CD - I hear that gives you the option of whether to install grub. Select on if you already have it installed, then run 'sudo update-grub' on the server install to detect your new Ubuntu install.

---

### Post by Kobalt on 2006-08-10
You can install as many distros as you want as long as you have enough space, installing Ubuntu Desktop on another partition is possible and safe. 
But if you want to share your /home partition you will have to be careful not to store any file and data that might interact with your Server needs. It just requires to be careful but again it's possible. Everything is possible with Linux ;) 

Cheers ! :rolleyes:

---

### Post by redmond on 2006-08-10
thanks guys.. I've seen the alternate CD.. is it the same as the main one.. baring the grub option?

I might just leave the home directory as default.. I've done my head in with the server and don't want to make things harder!

---

