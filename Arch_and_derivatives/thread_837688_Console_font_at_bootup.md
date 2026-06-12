---
title: "Console font at bootup?"
date: 2008-06-22
forum: Arch and derivatives
---

### Post by shearn89 on 2008-06-22
Hey all - just wondering if there's anyway to get your console font to load up earlier than when the Arch logo kicks in? I think i need to regenerate the initrd, but not sure how to, or whether thats right. May need to recompile the kernel?

---

### Post by MisfitI38 on 2008-06-22
Add the 'keymap' hook to /etc/mkinitcpio.conf and rebuild the image: 
# mkinitcpio -g /boot/kernel26.img
See [here]("http://wiki.archlinux.org/index.php/Mkinitcpio") for more.

edit: Added this to the Fonts wiki page.

---

### Post by shearn89 on 2008-06-23
thanks - i've done that, but is there anyway to get it to load before then? ATM, that only kicks in when the initramfs gets loaded. I wondered if there was anyway to recompile the layer before that...

---

### Post by ch_123 on 2008-08-17
A question folks, I set my consolefont to Terminus, but if I go back into the command line from KDM (select Console Login) it reverts to default. Any way around it?

---

