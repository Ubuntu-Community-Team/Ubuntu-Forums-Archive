---
title: "More permissions problems"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2006-08-16
I thought I was getting the hang of this but this whole permissions thing has get the better of me once again.
I'm trying to run three "simple" commands related to a partition on a usb hd. These are the commands:

```
sudo mount --bind /dev /media/usbdisk-3/dev
sudo chroot /media/usbdisk-3
sudo mount -a

```

and before I tried these, I ran this command to set the appropriate permissions (or so I thought):

```
 sudo chmod -R 777 /media/usbdisk-3

```

However, I get the following error message after the third command:

```
sudo: /etc/sudoers is mode 0777, should be 0440
```

Google has shown that this is not an uncommon error although no clear manner to overcome this problem is evident (to me, at least).

Note that I have used exactly the same commands before on an identically configured and sized usb hd on the same computer and had no problems.

I'm baffled. Can anybody help....please?

---

### Post by aysiu on 2006-08-16
Reboot into recovery mode.
Type ```
chmod 440 /etc/sudoers
reboot
```

---

### Post by PaulFXH on 2006-08-17
Thanks for your reply and suggestion.
I had actually re-installed Ubuntu before I saw your post. In any event the problem is gone.

---

