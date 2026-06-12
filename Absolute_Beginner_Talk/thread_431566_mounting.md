---
title: "mounting?"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by Jdratcliffe on 2007-05-03
i looking to take plunge on an old laptop, but one thing keeps coming up this "mounting " of drives cd and other im no noob (using and working with pc for 5-7yrs i only 19!) but this is a phrase i have not heard.

---

### Post by Stephen Howard on 2007-05-03
'mounting' is just unix-speak for the process whereby the operating system makes storage media (eg harddrive partition, cd, dvd, ipod) accessible to the user.

---

### Post by Jdratcliffe on 2007-05-03
r ok

---

### Post by steve.horsley on 2007-05-03
Like Stephen Howard says. 

You should know that when a new disk becomes available in *nix, rather than appering as a different "drive" like in windoze, it gets grafted on to the one-and-only directory tree. This is the act of mounting a drive or partition. It actually replaces an existing directory, making the original contents inaccessible until the drive is unmounted again. This is not at all intuitive - it's just one of those things you have to have explained to you. You can't mount a drive to a directory that doesn't already exist either - you have to replace one. 

The act of unmounting a drive removes it from the tree to reveal the original contents of the "mount point" folder, but also causes any disk cacke contents to be written out to the physical disk. This is why you should always unmount a USB stick before pulling it out (windoze has a similar "safely remove hardware") function.

Originally, *nix had to have drives mounted by hand command, but many now have a background process that watches for the insertion of removable media and the auto-mounts it.

---

