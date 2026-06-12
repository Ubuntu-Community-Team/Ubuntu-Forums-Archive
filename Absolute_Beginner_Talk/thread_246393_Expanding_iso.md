---
title: "Expanding iso?"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by linux on 2006-08-29
I downloaded the Desktop ISO for Ubuntu. It said 680MB on the site, and when I downloaded it, it had expanded to 715MB, making it impossible to fit onto my cd.

Suggestions, solutions?

---

### Post by Klaidas on 2006-08-29
I haven't had this problem myself, but I think overburning could help.

---

### Post by steve.horsley on 2006-08-29
Yes, definitely.

The .ISO is an image of the CD as it shoud be. An image of the entire contents including the CD's file system and its boot sector. It is not intended for you to unpack / extract it or anything like that. You don't unpack the contents abd just burn them. Neither do you just put the file onto the CD as though it were data. As a CD image, it need to be treated in a special way, and burned to the CD **as an image**. I think that all CD burning packages shoud have such an option, but can only vouch for Nero, which is what I used to burn my first Linux CD. On Nero, there was a menu option to burn an image file, which then opened a file finder dialog that looked specifically for .iso files. 

Once the image file has been burned, the CD is bootable, and also if you look on the CD you see loads of file and directories, not a .iso file.

Hope this makes sense. Good luck.

---

### Post by toasted on 2006-08-29
I can attest to NTI CD Maker as having the .iso burning option as well. Sounds like the same procedure as Nero

---

### Post by fluteman on 2006-09-05
> **linux said:**
> I downloaded the Desktop ISO for Ubuntu. It said 680MB on the site, and when I downloaded it, it had expanded to 715MB, making it impossible to fit onto my cd.

Suggestions, solutions?


I had the same expanding problem when downloading the Ubuntu ISO image using both using both http & ftp on a Windows XP box.  But I just hapened to also have an Apple iBook and downloaded the ISO image using the iBook and it worked just fine.  What's interesting is that while the ISO image is 698Mb, it actually contains 732Mb of data - so the Windows files system is expanding the image rather than making an exact image of the ISO file that is on the server.  Unfortunately, I wasn't able to figure out how to o ercome this problem using my Windows system.

Good luck

---

### Post by comppsyco on 2006-09-05
For windows, CDBurnerXP Pro is free and will do the job nicely.

EDIT: You can download from download.com

---

