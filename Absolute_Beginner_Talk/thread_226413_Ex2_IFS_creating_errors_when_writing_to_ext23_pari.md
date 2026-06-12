---
title: "Ex2 IFS creating errors when writing to ext2/3 paritions ?"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by ovimunt on 2006-07-31
Hi,

I'm using ***Ext2 IFS*** to access my linux partitions from Windows and I've been regularly copying files from my NTFS partition to the linux one which is ext3. 

Recently I have noticed various strange errors in Kubuntu after writing files to the etx3 partition from Windows. Most noticeable is the fact that Kubuntu can't reboot or switch users anymore which is quite a problem...

Yesterday the problems got actually worse. When booting linux it went into ***fsck*** fixed some errors on the drive and then restarted. The computer booted again and went fine into linux. Yet when I booted Windows I couldn't access the ext3 partition anymore... it would say it's an unknown partition. Kubuntu still works though, with the errors mentioned before. 

Any ideas if this is because of Ext2 IFS or maybe it's something else I'm doing wrong?

---

### Post by ajgreeny on 2006-07-31
Are you meaning you boot into windows and then copy files from the ntfs file system to the ext3 file system, ie you write to ext3 from within windows?  I can explore my linux partitions (ext3 only, not reiser) using explore2fs, but it doesn't allow me to write to the ext3 partition.  I can copy/extract files from linux and then write them to the ntfs partition when I'm in windows, and of course I can read windows files from linux by simply mounting the windows partition, but I can't write to ntfs (not safely anyway).  Perhaps if you are writing to ext3 from an ntfs boot it is upsetting the linux partition, hence the fsck on booting.

Bear in mind, I have no experience of the ext2 IFS that are talking about, but just making possible suggestions for the reason for your problems.

Edit:  I've just googled for ext2 IFS and see that it seems to support writing to an ext3 partition so all this post may now be of little consequence, but I'll leave it as food for thought, in any case.

---

### Post by ovimunt on 2006-07-31
*bump*

---

### Post by Cuppa-Chino on 2006-10-16
another bump!

can anyone tell me if it is SAFE to write to ext3 with IFS from windows - or does this mess up the journaling and subsequently causes problems?

is it better to have ext2 exchange Linux <-> Windo$ partition?

thanks

just found it in the [FAQ of FS-driver]("http://www.fs-driver.org/faq.html#acc_ext3") - still can anybody report issues or things to be aware of?.

thanks

---

### Post by aarbear26 on 2006-10-16
I am definaylt having similar problems with ext2 ifs.  It happened once and I thought it was a fluke, not it happened a second time to the same files. I write quite regularly to my ext3 drive from windows to update certian files. It always screws something up that somehow makes firefox in linux no longer save settings. It's the strangest thing since I do NOTHING with my linux firefox in windows.  I think ext2 IFS has some major problems and I would NOT recommend using it.  I'll keep searching to see if I can fix it. So far I've done a complete removal of Firefox and reinstalled and it still has the same problems!

---

