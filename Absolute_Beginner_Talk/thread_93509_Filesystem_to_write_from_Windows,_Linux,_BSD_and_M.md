---
title: "Filesystem to write from Windows, Linux, BSD and MAC"
date: 2005-11-22
forum: Absolute Beginner Talk
---

### Post by Paloseco on 2005-11-22
I am looking for a filesystem to read and write to from windows, linux, mac and unix. Also a feature that I need is the support for large files. Here is a list of filesystems I have in mind, advice me if other are suitable:

[LIST=1]
[*]NTFS is not writable from Linux.
[*]VFAT does not support bigger files than 4 GB.
[*]Ext2 is the most supported filesystem, linux, bsd and windows with Ext2IFS. Exceptionally latest version of MAC does not support it (you cannot install the program).
[/LIST]
Any ideas about wich filesystem is the best to be able to share data (for example mp3) with those operating systems?

---

### Post by Brunellus on 2005-11-22
FAT 32 is pretty well understood by everyone.

---

### Post by ssam on 2005-11-22
it seems so wrong that the best cross platform format is the one by microsoft. its the same with word processor files. want to move a file from openoffice to abiword, you have to use a .doc (though this should change soon).

what is your situation? work a network file system work? can they all read nfs. they must all be able to use ftp, but maybe not in a normal filesystem way.

---

### Post by frodon on 2005-11-22
I never got any problem ripping DVD (file > 4Go) and using FAT32 partitions.
About ext2/ext3 windows support it works nice for read but write is still dangerous, i hope a full write support will come soon because if FAT32 works really nice, it don't support ownership and unix rights and that's why i woud prefer use ext3.

---

### Post by Paloseco on 2005-11-22
The support for write ext2/ext3 under windows xp does not claim to be dangerous [http://www.fs-driver.org/]("http://www.fs-driver.org/") And one of the reasons not to use FAT32 is that [does NOT support files bigger than 4 GB]("http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/windows/xp/all/reskit/en-us/prkc_fil_cycz.asp"), or tell me how to do it with windowsxp, probably you mean that you split the vobs... like does dvddecrypter.

And [this]("http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkc_fil_tdrn.asp") is false, i have a 90 GB partition with FAT32. What is wrong?

---

### Post by frodon on 2005-11-22
[QUOTE=Paloseco]The support for write ext2/ext3 under windows xp does not claim to be dangerous [/QUOTE] For sure it is for ext3 !
And as i said before i never got any problems with file > 4Go under linux and i'm not alone in this case. But endeed FAT32 is far to be the solution but it still a good idea to use windows and linux for the moment.

---

### Post by Paloseco on 2005-11-22
So you mean that windows limits virtually to those 4 GB and that with Linux you can exceed those bits working the same? I suppossed that was a technical spec of the filesystem and could not be violated, maybe you tunned up something in the kernel, i am going to try it now and see ...

---

### Post by frodon on 2005-11-22
The biggest files i had to handle was DVD rip iso files (4.4Go) and till now i'm able to burn them and move them.
However i never handled bigger files, could you confirm if it works for you ?, i would like to be sure that it works for everybody here.

thanks

---

### Post by Paloseco on 2005-11-22
I will post my experiences. I have booted ubuntu 5.10 live cd and mounted a ext3 and vfat filesystems. I copied a 4.9 GB iso from the ext3 to the fat32 but only 4 GB seem to be copied. I switched to Windows then and the iso on the fat32 weighted 3.99 GB (=4) and after copying that file to the ext3 partition (with different name) only those 4 GB where copied. Also deleting the iso from the fat32 partition frees exactly those 4 GB, not 4.9 (checked with windows explorer and Acronis Disk Director), so i thing that the ubuntu 5.10 or the version of the kernel used have a bug and does not check correctly either if the file suits the specs or not, and cuts it off to the maximunm filesize: 4GB (or 3.99 as says windows xp).

---

### Post by frodon on 2005-11-22
And if you use your iso file does it work ?
However what you said remind me that sometime i noticed some file size differences between windows and ubuntu.
I hope someone more knowledgable could enlighten us on this point.

---

### Post by Paloseco on 2005-11-22
You cannot consider any difference between 3.99 and 4, that may be because one approximates it more or less, if you use quick view. i am sure that if you select properties both windows and ubuntu will show you the same size in bits. Unfortunately, i do not have net at home, but will do further research later.

Check it if you can with SuSE, I think that prevent you from doing such a thing because really detects that the fat32 has a maximun size of 4GB and gives you an error if you try to copy it, but maybe ubuntu skips that initial check. I hope that ubuntu stops writing once reachs those 4GB, if not, consider that you copy a 15GB iso, and contiues writing after the 4GB, will be overwriting the contiguous data, like a buffer overflow or a segmentation fault!!

---

### Post by frodon on 2005-11-22
No i don't think so.

What i mean is that when i create a ghost of my ubuntu partition and make an iso file (about 3Go) , the size displayed by windows is lower than the size displayed by ubuntu.
So my first idea is that when i believe to create a 4.4Go iso file in ubuntu I create a file about 4Go in reality and that's why it works. If not i couldn't explain myself why my dvd rip works !
I think that if i make the same test as you with a bigger file it won't work too.

I will try to get more informations too.

---

### Post by Paloseco on 2005-11-22
Windows and linux always display the same size, maybe you did something wrong.

---

### Post by frodon on 2005-11-22
Hey, really weird windows says my partition is 71.4Go whereas ubuntu says it's 73.2Go :confused: 
I really need to learn more about that.

---

### Post by Paloseco on 2005-11-22
Maybe one divide by 1000 and the other by 1024 :rolleyes:

---

### Post by frodon on 2005-11-22
I think it should be something like that ;)

---

### Post by Paloseco on 2005-11-23
Definitely i have found where the problem is: Linux does not check wheter if the file suits the specs or not, and cuts off the file when you try to exceed the 4 GB. i a missconfiguration that need to be solved as soon as posible.

---

### Post by frodon on 2005-11-23
I agree.

Thank you for the info, i didn't know that ;)

---

