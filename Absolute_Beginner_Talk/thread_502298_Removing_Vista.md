---
title: "Removing Vista"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by Tim Fox on 2007-07-16
I didn't know where to put this.

I installed Ubuntu Feisty Fawn to dual-boot with Vista a couple of weeks ago. Now I want to remove Vista entirely. When I try to unmount Vista in GParted I get:

Could not unmount /dev/sda1

The partition could not be unmounted from the following mountpoints:

/media/sda1

Most likely other partitions are also mounted on these mountpoints. You are advised to unmount them manually.


Any help?

---

### Post by cotcot on 2007-07-16
Take out the vista partition from your /etc/fstab and reboot.

---

### Post by Tim Fox on 2007-07-16
> **cotcot said:**
> Take out the vista partition from your /etc/fstab and reboot.

Thanks. ;)

---

