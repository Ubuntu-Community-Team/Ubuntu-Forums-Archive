---
title: "Install ubuntu on dell dimension 6150"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by Neilisgreat on 2008-02-18
Hi, I want to install Ubuntu on a Dell Dimension 6160 but also keep XP.
when I go throught the install i get a number of partitions and i chose
NTFS but i get the message invalid boot loader or something like that.
any ideas?:confused:

---

### Post by Joeb454 on 2008-02-18
You need to shrink the large NTFS partition. And then install in the newly available free space.

For more information try [http://www.psychocats.net/ubuntu/index.php]("http://www.psychocats.net/ubuntu/index.php")

---

### Post by Tatty on 2008-02-18
> **Neilisgreat said:**
> when I go throught the install i get a number of partitions and i chose
NTFS 

Be careful, that NTFS partition is probably your windows partition, if you install to that then you will erase windows.

In addition to Joeb454's link, you might want to check out [https://help.ubuntu.com/community/HowtoPartition?highlight=%28partition%29]("https://help.ubuntu.com/community/HowtoPartition?highlight=%28partition%29")

---

