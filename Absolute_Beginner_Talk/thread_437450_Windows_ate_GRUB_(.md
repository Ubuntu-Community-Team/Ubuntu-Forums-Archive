---
title: "Windows ate GRUB :("
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by Gorthus on 2007-05-08
My Windows installation died, so I reinstalled it, and apparently it ate grub, so I can no longer get into Ubuntu :( ...

What do I do?

---

### Post by mojo123 on 2007-05-08
use the GRUB rescue cd

---

### Post by Happy_Man on 2007-05-08
Yeah, Windows's NTLDR will overwrite GRUB. Use the Super Grub disk (downloadable off the GRUB website) to fix it... simply burn the ISO and restore GRUB! Simple!

---

### Post by Gorthus on 2007-05-08
My friend actually helped me do this...

He told me to SUDO GRUB and then some other things :)

Thanks anyways guys.

**[RESOLVED]**

---

### Post by trmentry on 2007-05-09
What did you do to get it fixed without the Super Grub cd?

My setup is 2 hard drive system.  1 drive for windows, 1 for ubuntu.

/dev/sda = windows
/dev/sdb = ubuntu

I need to reinstall windows so know it will eat Grub, so have been grep'ing for solutions.

This is what I came up with using a livecd

```

sudo grub
grub> root (hd1,0)  <-- /boot is on 2nd drive along with /
grub> setup (hd0) <-- which mbr to install to
grub> quit

```

Am I on the right track?

Is this pretty much what Super Grub will do?

Thanks

---

