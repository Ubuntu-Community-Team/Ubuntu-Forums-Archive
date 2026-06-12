---
title: "Dual Installing Ubuntu"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by shooting_rubber on 2008-02-26
Hello Everyone,

I am wondering how I can dual-install Ubuntu 7.10 when Windows XP is already installed on my computer.  I dont want Ubuntu to be my main OS, but I want to be able to use it.  I have Ubuntu 7.10 on a disc and I am able to use Ubuntu from the disc, but I am not completely sure how to dual-install.  I have already re-sized my main partition and I now have unallocated disk space.  I dont know how to create the two partitions needed to install Ubuntu.  I have 3 primary partitions already on my computer and the maximum allowed is 4.  You need to have 2 partitions to install Ubuntu and I dont know how to do this.

I really want to be able to use Linux Ubuntu 7.10. 

I really appreciate your help.

Thanks.

---

### Post by ZeroFive1 on 2008-02-26
Why do you have three partitions?

---

### Post by Locutus_of_Borg on 2008-02-26
What are the three partitions other than XP?


You could create out of the unallocated space an extended partition and inside of that a logical partition in which one is your ubuntu file system, and the other your Swap partition.  

When you get to the partitioning section of th install, choose manual, the select the free space and click new, create extended partition with file system type ext3, leave about 1-2 GB for Swap, and mount it at /.  Then do the same for the 1-2 GB left over after that and format it as Swap space.

Continue with the install and everything should be fine.


But why do you already have three partitions?

---

### Post by jhenager on 2008-02-26
You won't have to worry about creating another primary partition. Use the guided mode of partitioning.
It will ask you if you want to use the free space and resize the partition. Just don't select the option to use the entire disk.
It's a lot easier than it sounds.

Edit: Note that if you have seriously critical data on your system, you should already have a current backup anyway. If not, I'd do that before I did anything else.

---

### Post by shooting_rubber on 2008-02-26
> **Locutus_of_Borg said:**
> What are the three partitions other than XP?


You could create out of the unallocated space an extended partition and inside of that a logical partition in which one is your ubuntu file system, and the other your Swap partition.  

When you get to the partitioning section of th install, choose manual, the select the free space and click new, create extended partition with file system type ext3, leave about 1-2 GB for Swap, and mount it at /.  Then do the same for the 1-2 GB left over after that and format it as Swap space.

Continue with the install and everything should be fine.


But why do you already have three partitions?

To be completely honest, I have no clue what the other 2 partitions are for.  They are just there.  Okay, I am very new to Linux and Ubuntu, but what is mounting?  How do I do that?

Thanks Again.

---

### Post by shooting_rubber on 2008-02-26
> **jhenager said:**
> You won't have to worry about creating another primary partition. Use the guided mode of partitioning.
It will ask you if you want to use the free space and resize the partition. Just don't select the option to use the entire disk.
It's a lot easier than it sounds.

Edit: Note that if you have seriously critical data on your system, you should already have a current backup anyway. If not, I'd do that before I did anything else.

Oh, and when I get to the partitioning part of the installation there is only 2 options.  There isn't an option other than manual and use the entire partition, so I dont know whats wrong there.

Thanks.

---

### Post by Locutus_of_Borg on 2008-02-26
Well, that is strange that you would have extra partitions without you're knowledge of them.  How are you aware of their existence if I might ask?

mounting at / just means that when you are in the installer and are choosing where to install linux, you specify / as the mount point (it is one of the options along with size and file system type) The partition you create that you set to mount at / will be your root file system, you can have a separate partition for just your personal files, but at this point in your experince i dont think its wise to bother with that yet.

Just choose manual, and it will show you your partitioning layout of your disk, Windows will be the one marked as NTFS, just leave that one alone, or you can make it smaller if you want by choosing "Edit", but Id just leave it and focus only on the parts that are marked as free space. Then do as I said in the last post and all ought be alright.

---

### Post by shooting_rubber on 2008-02-26
> **Locutus_of_Borg said:**
> Well, that is strange that you would have extra partitions without you're knowledge of them.  How are you aware of their existence if I might ask?

mounting at / just means that when you are in the installer and are choosing where to install linux, you specify / as the mount point (it is one of the options along with size and file system type) The partition you create that you set to mount at / will be your root file system, you can have a separate partition for just your personal files, but at this point in your experince i dont think its wise to bother with that yet.

Just choose manual, and it will show you your partitioning layout of your disk, Windows will be the one marked as NTFS, just leave that one alone, or you can make it smaller if you want by choosing "Edit", but Id just leave it and focus only on the parts that are marked as free space. Then do as I said in the last post and all ought be alright.

I went to Disc Management and they are there.  And I also have a program that I load from a disc on startup that shows me my partitions and they are there and I dont know why.  So when I'm in the installer where do I choose to mount it?

Thanks.

---

### Post by SonicSteve on 2008-02-26
What kind of computer is this? Those unknown partitions are likely restore partitions that contain the data to restore windows XP in the event of software crash. It's just a guess but it seems reasonable. If they are restore partitions and you destroy them your ability to re-install windows will be gone unless the pc manufacturer also gave you restore CD's.

---

### Post by shooting_rubber on 2008-02-26
> **SonicSteve said:**
> What kind of computer is this? Those unknown partitions are likely restore partitions that contain the data to restore windows XP in the event of software crash. It's just a guess but it seems reasonable. If they are restore partitions and you destroy them your ability to re-install windows will be gone unless the pc manufacturer also gave you restore CD's.

It's A Dell Inspiron 1501, and I do have restore CD's for Windows XP.  I've already re-formatted the disc once by using the re-installation CD's that came with the purchase.

Thanks.

---

### Post by shooting_rubber on 2008-02-26
Does anybody know what would happen if I deleted the 2 partitions that I have no clue why they're there?

Thanks.

---

### Post by shooting_rubber on 2008-02-26
Now I have dual-installed Ubuntu, but I dont know how to get my wireless internet working.  I am on my Windows XP Home Edtion right now.  Can anybody help me on how to get my wireless internet connection working from Ubuntu?

EDIT: I dont know if this helps you, but I have a Dell Inspiron 1501, Broadcom 440x 10/100 Integrated Controller, and a Dell Wireless 1390 WLAN Mini-Card.

Thanks.

---

### Post by shooting_rubber on 2008-02-26
Anyone?

---

### Post by Locutus_of_Borg on 2008-02-26
Try this: [https://help.ubuntu.com/community/WifiDocs/Driver/1390](https://help.ubuntu.com/community/WifiDocs/Driver/1390)

I followed that on my wife's computer and it all works, I did have to do some tweaking afterwards, and due to some bug, in order for it to work right, she has to turn her wireless switch on her laptop off then on before it will connect

---

### Post by shooting_rubber on 2008-02-26
Now, when I try and load Ubuntu from the screen when I load my computer, it won't load?:(  It just stays blank for a while and does nothing.  So now I don't know what to do.  It was working before, but not anymore.

EDIT: I have Ubuntu 7.10.

Any ideas?

---

