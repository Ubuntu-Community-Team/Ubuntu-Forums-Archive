---
title: "Anyone used TrueCrypt in traveller mode? Need Windows/Linux program."
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by kevdog on 2008-01-18
Here is what I would like to go.

Have a totally encrypted usb drive that I can access the contents in on windows or linux, without installing any software on the host machine.

I pretty much figure this is out of the question, however the next best option I thought would be to create a true crypt container on the USB drive and then copy the true crypt binary to the unencrypted portion of the USB driver, in order to run truecrypt in traveler mode to access the encrypted partition.

Ive read on the TrueCrypt site, however, that you need admin priviledges on the host machine to run in traveller mode.  I dont know if I will always have this -- it seems like a pretty big limitation to me.  I think the admin privileges are needed in order to create a mount point on either the windows or linux box -- correct me if I am mistaken.

Anyone have any workarounds or any other ideas about what scheme I should use.

---

### Post by pytheas22 on 2008-01-18
I did research on this for work and came to the conclusion that there was no reliable way to access a truecrypt volume from a machine on which you don't have admin/root privileges.  We thought a lot about doing what you mention--putting the truecrypt drivers on the unencrypted part of the drive--but couldn't figure out a way to be able to use those drivers as unprivileged users.  Of course, we could have missed something and maybe there is a way to do it, which I'd be very interested in.

If you want a secure USB drive that you can use anywhere, check out Corsair's padlock (susceptible to physical attack, but will protect you from casual intruders, and it's cheap) [http://www.corsair.com/products/padlock.aspx](http://www.corsair.com/products/padlock.aspx)

or Ironkey, which is the most secure way to go, although it's expensive and I think it will only be plug-and-play on a Windows box; on OS X or Linux you need drivers installed [https://www.ironkey.com/](https://www.ironkey.com/)

---

### Post by kevdog on 2008-01-18
Hmm, both those options are not ideal, for reasons that you stated.  I need more than just password protection, but rather true content encryption.  Seems like I shouldn't be the first person to want this.  Its a bummer.

---

### Post by capink on 2008-01-18
Depending on the size of the usb disk, you can install a minimal linux distro on the usb dive ( Separate unencrypted partition ) that would always give you admin privledges. This would only work with recent machines that can boot from usb drive. And it would also need you to reboot which might no be always convenient.

---

### Post by kevdog on 2008-01-19
Yea I suppose, but this doesnt seem very practical in that not all machines can boot from a USB drive.

---

