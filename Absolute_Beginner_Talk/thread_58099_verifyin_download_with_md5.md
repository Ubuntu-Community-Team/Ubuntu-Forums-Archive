---
title: "verifyin download with md5"
date: 2005-08-18
forum: Absolute Beginner Talk
---

### Post by md4life on 2005-08-18
i've just downloaded the both suse live cd for 64bit and the suse 9.3 eval 64bit.  i've been trying to check the validity of the files with the md5sum, but can't seem to execute  correctly.  currently i'm running xp64.  these are the instruction i got when i download the program:  > Put it into your system folder (c:\windows\command for Win95/98/ME or c:\winnt\system32 for NT/2K/XP). Alternatively, you can just put it in the same folder as the ISO and MD5 files. If you do that, though, it will not be available system-wide.

Open Windows Explorer and navigate to the directory containing the ISO file and the MD5 file. Next, open a command window by going to Start -> Run and entering the word "command" then clicking OK. A command prompt should open up, and it should be in the same directory as you were in in Explorer.

Now, type the following command (without the quotes) and then press enter:
"md5sum -c TheOpenCD-v1.4.iso.zip.md5".

before i burn both DVDs, i want to check if i download good copies.  some help please.

---

### Post by JonahRowley on 2005-08-18
I don't understand, what's going wrong?

---

### Post by Buffalo Soldier on 2005-08-18
Looking at your post I'm assuming you're trying to do compare MD checksum while using MS Win.

Are you more comfortable using GUI? If that's the case then [winMD5sum](http://www.nullriver.com/index/products/winmd5sum)  is what I would recommend to you.

---

### Post by heimo on 2005-08-19
Couple more links:
[http://www.openoffice.org/dev_docs/using_md5sums.html]("http://www.openoffice.org/dev_docs/using_md5sums.html")
[http://www.md5summer.org/]("http://www.md5summer.org/")
[http://www.linuxiso.org/viewdoc.php/verifyiso.html]("http://www.linuxiso.org/viewdoc.php/verifyiso.html")

[https://wiki.ubuntu.com/VerifyIsoHowto](https://wiki.ubuntu.com/VerifyIsoHowto)

---

### Post by md4life on 2005-08-19
thanks heimo, your websites gave better instructions on how to execute the commands.

---

