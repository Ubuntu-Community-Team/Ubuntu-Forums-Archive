---
title: "How do i unzip a .tar file......Xarchive wont work"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by Sniper99 on 2006-08-07
i did a download to have an HP printer work on my network....but the .tar file will not unzip....is there any other any way to unzip it without using archiver

---

### Post by dusu on 2006-08-07
Open a terminal, go to the directrory where your dunnowhat.tar file is (using the cd command) and then type
```
tar -xvf dunnowhat.tar
```

---

### Post by deadgobby on 2006-08-07
I notice you have open up a other thread. Is this the same topic? Any hoo.
[http://www.psychocats.net/ubuntu/installingsoftware.php](http://www.psychocats.net/ubuntu/installingsoftware.php)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

 You may save you self a head ache and check you Synaptic for the printer, or go into System>Admin>Printing and check to see when you set up that the driver is there. 

Gobby

---

### Post by Sniper99 on 2006-08-07
that doesn't seem to be working...the exact file name is hplip- 1.6.7.tar.gz....but it is still a .tar file i think

---

### Post by Sniper99 on 2006-08-07
gobby...i dont seem to see a admin menu item...i am running xubuntu

---

### Post by ColdDeath on 2006-08-07
tar zxvf hplip- 1.6.7.tar.gz

---

### Post by Sniper99 on 2006-08-07
i tried that....but this appeared










user1@user1-desktop:~/Desktop$ tar zxvf hplip- 1.6.7.tar.gz
tar: hplip-: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: 1.6.7.tar.gz: Not found in archive
tar: Error exit delayed from previous errors

---

### Post by ColdDeath on 2006-08-07
A) The file isn't there.
B) Its an incorrect filename.

Can you show me the output of:
```
ls
```

---

### Post by Sniper99 on 2006-08-07
sorry..there was a space i accidentally put in...i tried your command line...with the correct filename...and this popped up



gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors

---

### Post by philipacamaniac on 2006-08-07
The file was either corrupted on download or is corrupted on the server. Try to download it again, and maybe try downloading it from a different location.

---

### Post by ColdDeath on 2006-08-07
In future for filenames there is a handy feaure called tab completion. Start writing the filename then press tab, it fills the rest in automagically.

Try writing "hpl" then press tab ;)

---

### Post by starscalling on 2006-08-07
first:
sudo apt-get install rar unrar bzip2
then youll have the stuff needed
btw
you should be able to right click and uninstall using file-roller

---

### Post by Sniper99 on 2006-08-07
hey guys....thank you for helping..it was a corrupt file.....the pheonix arizona mirror is corrupting files for some reason....thanks for all your help!!!!!!!!!!

---

