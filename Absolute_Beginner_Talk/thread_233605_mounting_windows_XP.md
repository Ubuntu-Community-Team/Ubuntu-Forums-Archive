---
title: "mounting windows XP"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by Aravind Kumar on 2006-08-10
I am using Ubuntu 5.04.I edited the /etc/fstab file to include my windows partition. When I try to change the directory to the place where I mounted the partition I get "permission denied" as the response. Is there a way to see my windows partition without using root account? 
I added the following lines the /etc/fstab file.

/dev/hdc5 /mnt/hdc5-e ntfs

Thanking in advance...

---

### Post by davebgimp on 2006-08-10
I usually just run this script:
[http://mjr.iki.fi/ubuntu/winmac_fstab](http://mjr.iki.fi/ubuntu/winmac_fstab)

Then, if I need to tweak anything later I'll manually do so, but the script will set you up and have your XP partition mounted every time you boot.

---

### Post by FenrisAbraxas on 2006-08-10
> **Aravind Kumar said:**
> I am using Ubuntu 5.04.I edited the /etc/fstab file to include my windows partition. When I try to change the directory to the place where I mounted the partition I get "permission denied" as the response. Is there a way to see my windows partition without using root account? 
I added the following lines the /etc/fstab file.

/dev/hdc5 /mnt/hdc5-e ntfs

Thanking in advance...

Add user,users in the options part. It will let normal users use that partition. good luck

---

### Post by Aravind Kumar on 2006-08-11
> **FenrisAbraxas said:**
> Add user,users in the options part. It will let normal users use that partition. good luck

I added user,users but still when I try to go the directory where I mounted the XP partition it says permission denied. Any help???

---

