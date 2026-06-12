---
title: "Dual Booting"
date: 2011-08-23
forum: Any Other OS
---

### Post by raven2099 on 2011-08-23
I have windows 7 dual booted...
but i'd like to access my photos and videos on my windows partition via Ubuntu and vice vers to show me the easiest way this can be done

---

### Post by Basher101 on 2011-08-23
You will be able to access windows files from ubuntu, but not the other way around. Ubuntu can read and write NTFS, but windows does not detect ext4, so if you want to have those files on both, make a shared NTFS partition where you store them. Or if your windows takes up 90% of the space, you could then just copy your ubuntu files to windows over. Otherwise a shared partition is the best solution for this (i also use this setup, i have a 640 gb HDD, (which i can only use 598 gb in the binary system), gave windows 30 gb, ubuntu 15, 4gb swap and the rest as a huge shared storage partition.

---

### Post by garvinrick4 on 2011-08-23
+1 with Basher101
 It is so much nicer to have indendent /home in its own partition and a data partition in NTFS
to use for sharing with Windows. And if there is ever a problem with an install and you want
to do a clean install you will not touch /home or data paritition, but always keep backups of
/home and data partitions is very wise. We are dealing with a HDD and they do go bad at times.

---

### Post by drawkcab on 2011-08-23
Or you can just install the ntfs-config package that lets nautilus read/write to your windows parition.  The only thing is that you're going to have to do the file transfers from within ubuntu.

Btw, windows can access ext3 using fs-driver.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

Even so, the partitioning solution that others have offered is probably best in the long run.

---

### Post by Megaptera on 2011-08-24
Another useful guide here: [http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

Quote: "... redirect the other commonly used folders like Documents, Downloads, Music, etc. to another partition, one that can be read by Windows.  Then, you can add these folders to your Windows 7 Libraries and mark them as the default save location.

This isn&#8217;t a proper workaround.  Your program-associated configuration files and other user-related settings will not be in the same place for this setup.  If you have to reinstall either OS, you will have to perform a separate backup of your user settings.  That being said, however, most people are really just concerned about their documents, music, videos, and so forth.  This solves that issue by pointing both OSs to look in the same place for them."

---

### Post by mips on 2011-08-24
[http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/](http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/)
[http://www.linuxjournal.com/article/9449](http://www.linuxjournal.com/article/9449)

You would be better off with some of the other suggestions above though than those links I posted.

---

