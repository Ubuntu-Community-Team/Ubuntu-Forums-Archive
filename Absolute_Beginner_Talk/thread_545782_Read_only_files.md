---
title: "Read only files"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by Jk5812 on 2007-09-08
I just use Ubuntu for few days...I was using Windows and openoffice.org as my spreadsheet before on windows..After i changed to Ubuntu,i try to open my documents,and edit it..But i can't because it is READ ONLY and owned by ROOT...do somebody know how to "open" this read only file??I need to edit this document everyday,and it makes me frustrated..Thank;s a lot:confused:

---

### Post by sapo on 2007-09-08
Is this document in the windows partition?

If it is, you will have to copy it to your ubuntu partition, because linux can't write in ntfs partitions (wich i believe should be your windows partition type).

If it is already in your ubuntu partion, just open up a terminal and type this to change the owner of the file:

```
sudo chown yourusername yourfile
```

change yourusername and yourfile to whatever is your ubuntu username and your file name.

you can also just use:

```
chmod 666 yourfile
```

even if it seems evil (heheh) it will give permission to all users to write on the file.

Hope it helps.

---

### Post by Baarhisveiki on 2007-09-08
> **Jk5812 said:**
> I just use Ubuntu for few days...I was using Windows and openoffice.org as my spreadsheet before on windows..After i changed to Ubuntu,i try to open my documents,and edit it..But i can't because it is READ ONLY and owned by ROOT...do somebody know how to "open" this read only file??I need to edit this document everyday,and it makes me frustrated..Thank;s a lot:confused:

Use "ntfs configuration tool" . It lets u edit files on an windows partition(windows left over on ntfs) on which ( i guess) your documents are still stored. U dont have to copy them to the linux partition

Check this out

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

it works for me...it should for you

or type directly in your terminal                 sudo apt-get install ntfs-config

---

