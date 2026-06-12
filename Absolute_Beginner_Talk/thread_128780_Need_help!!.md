---
title: "Need help!!"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by naveents on 2006-02-12
I have got the new Ubuntu Linux!! It is Gr8..I need to know how can you transfer data from Ubuntu linux to Windows Xp and vice versa!! I am a beginner in this field!! So,i would be happy if any1 could explain this topic to me in detail!!
Thankx......

---

### Post by manicka on 2006-02-12
[http://doc.gwos.org/index.php/Share_files_using_Samba](http://doc.gwos.org/index.php/Share_files_using_Samba)

---

### Post by orlox on 2006-02-12
I share a fat32 partition between both os's to keep my shared files and it works perfectly...

---

### Post by cjm5229 on 2006-02-12
Samba works great to transfer files from a Windows Computer to a Linux computer on a network. If you are dual booted and want to transfer files from your Windows Partition to your Ubuntu Partition the best way is to use a fat32 partition. You can use Gparted to create this partition by booting a live CD and running Gparted from the Applications Menu. Make it what ever size you wish, then make sure it's mounted in both Windows and Ubuntu. It should show up in My Computer in Windows and Aisus has a great Howto on mounting partitions in Ubuntu. Should be able to find it in "Customization and Tips" Or in Aisus sig in one of his posts. He also has a great how to dual booting. Good Luck. :D

---

### Post by Coax on 2006-02-12
Hi I just started using Linux a couple days ago, and ran into this problem with sharing.  I have 2 computers networked through a linksys router.  I've been trying to get Samba to work and followed the walkthrough given in the link a couple posts up.  I finally got my windows pc to see the workgroup labeled Workgroup When i go into it I get my server but when i click on it i get a very rude windows pop up saying...

\\SERVER_NAME blah blah is not accessible.  You might not have permission to use this network resource.  Contact the administrator of this server to find out if you have access permissions. 

The parameter is incorrect.  

Im kinda stuck at this point.  not sure if i have to turn the samba program on first or how to do that  any help would be apprecitated thanks.

---

