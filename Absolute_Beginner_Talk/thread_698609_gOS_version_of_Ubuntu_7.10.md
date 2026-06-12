---
title: "gOS version of Ubuntu 7.10"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by MachSpire on 2008-02-16
I have Windows XP and gOS Ubuntu 7.10 installed, and I wish to uninstall the gOS, without affecting the XP, so that I can reinstall Ubuntu on that part of the hard drive of my Sony Vaio VGN-FE31Z. How is this done, as I can not do so from either the Live gOS CD or from XP? Please help. Many thanks.

---

### Post by angryfirelord on 2008-02-16
There's no "uninstall" option when you install an operating system. Rather, you just overwrite it. Boot up the Ubuntu CD and when you get to the partitioning step, mount and format those partitions. You may have to designate one / and one swap through the mount points. If you see your Windows partition (ntfs), don't touch it.

---

### Post by Flyingjester on 2008-02-16
> **angryfirelord said:**
> There's no "uninstall" option when you install an operating system. Rather, you just overwrite it. Boot up the Ubuntu CD and when you get to the partitioning step, mount and format those partitions. You may have to designate one / and one swap through the mount points. If you see your Windows partition (ntfs), don't touch it.

+1

---

### Post by LacosteGirl23 on 2008-02-16
I have windows vista on my sony vaio VGN-AR720/b I don't think I am going to try to install Unbuntu. I will just continue to use the disk. With that said, does anyone have a AR series Sony Vaio laptop by chance?

---

### Post by angryfirelord on 2008-02-16
> **LacosteGirl23 said:**
> I have windows vista on my sony vaio VGN-AR720/b I don't think I am going to try to install Unbuntu. I will just continue to use the disk.
Why not? In Vista, it's actually easier to install Linux since Vista can shrink itself.

First, shrink your Vista partition: [http://www.tech-recipes.com/rx/1593/vista_shrink_partition]("http://www.tech-recipes.com/rx/1593/vista_shrink_partition")
Then, boot up the Ubuntu CD and install it. You can even let the installer decide on how much of the free space it should use automatically (or you can do it manually). If you need help, you can look here: [http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon]("http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon")

---

