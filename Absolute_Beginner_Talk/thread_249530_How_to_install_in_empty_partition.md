---
title: "How to install in empty partition?"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by outofdiskspace on 2006-09-02
I have two partitions.  P1 already has Windoze on it and I would like to install ubuntu in P2 to ultimately have a dual-boot system.  

When I run the install program it offers three options:
1) Install at P1
2) Wipe disk and install
3) Manual partition

So my only option is "3".  My problem is the next screen.  How do I tell the install program to leave P1 partition alone and only install in the second partition?

---

### Post by benfindlay on 2006-09-02
After you have picked manual partition, on the next screeen you can choose what to do with the remaining space. You need to set up part as a swap file, and then what you do with the rest is your choice. I personally have part of my HDD mounted as /, and another partition mounted as /home. As long as, on the final screen before you format the drives, you make sure your NTFS partition is unticked (option to reformat), then you will be fine!

You can also choose to mount your NTFS drive at a certain location, such as hdb1, or to just have ubuntu ignore it

Hope this helps!

---

