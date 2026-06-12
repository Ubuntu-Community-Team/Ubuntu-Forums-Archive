---
title: "Upgrading"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Vinn on 2007-06-15
I've got Ubuntu 6.10 on one of my laptops. Can I upgrade it to 7.04 with the cd? The internet doesn't work on it, so I can't do it that way.

---

### Post by w4ett on 2007-06-15
No you need the internet to upgrade, but a fresh install  from the cd is the preferred method anyway...just backup your data.

---

### Post by Vinn on 2007-06-15
It's dual booted. Can I reinstall without taking up more drive space?

---

### Post by Outrunner on 2007-06-15
Well, actually, you can use the Alternate CD to upgrade. I'm not sure how it's done, however.

EDIT

[Upgrade using the Alternate CD]("http://www.ubuntu.com/getubuntu/upgrading") - It's at the end of the page.

---

### Post by Vinn on 2007-06-15
Where is the alternate cd?

---

### Post by w4ett on 2007-06-15
I'd use the same ext3 partition from your previous installation...or use gparted on the live cd to erase that partition and then reinstall.

---

### Post by Vinn on 2007-06-15
Alrighty then, I'll give that a go. Thanks.

---

### Post by Outrunner on 2007-06-15
> **Vinn said:**
> Where is the alternate cd?

Text install CD(no GUI) for older machines. [Get one from here.]("http://releases.ubuntu.com/7.04/")

---

### Post by Vinn on 2007-06-15
It keeps saying I need to set up a root when I do the install hdd config manually. What am I doing wrong?

---

### Post by zvacet on 2007-06-15
If you have separate home partition you only need to install root.i belive it is free space you have when you deleted previous install.Click on free space and that will leed you to the next step where it wil ask you about format(yes) and moutnpoint( / ).Scroll down and select partition finished (or something similar).Do not format home partition,because you will lose all your data.

---

### Post by Vinn on 2007-06-15
Is it possible to do this without formatting my Windows install? Bump

---

### Post by Vinn on 2007-06-15
Bump

---

### Post by zvacet on 2007-06-15
Yes,because you will see all your partitions and don´t tuch ntfs one.You will install on your previous Ubuntu partition wich is ext3 format.

---

### Post by Vinn on 2007-06-18
So help me out here:
I select Manual when installing, check "format" for the old Ubuntu "ex3" partition, and do the whole root thing it asks me to do, then I just keep hitting next?

I'm not sure if I should delete the partition cause then I might mess up grub and not be able to boot into Windows again.

---

