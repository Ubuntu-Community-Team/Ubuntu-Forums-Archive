---
title: "Kubuntu- Edgy eft iso?"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by Ryupower on 2006-10-29
Hi, downloaded Kubuntu Live CD, 
Now, pasted it on the Disc, two options:
" create from Image"
or
"Create with file"?


silly question I know

---

### Post by taurus on 2006-10-29
Before you burn it to a CD, run checksum to check on the integrity of it!  If it doesn't pass, then don't bother and download it again...  However, I recommend you delete both files and download it over again.  If you have a fast network connection, DSL, it shouldn't take too long.  ;)

---

### Post by meng on 2006-10-29
The ISO should be 700 MB, so I suspect you still have a partial download, perhaps your download manager is able to complete the download given those two files.

---

### Post by Ryupower on 2006-10-29
> **taurus said:**
> Before you burn it to a CD, run checksum to check on the integrity of it!  If it doesn't pass, then don't bother and download it again...  However, I recommend you delete both files and download it over again.  If you have a fast network connection, DSL, it shouldn't take too long.  ;)

....ho do you run that? XD
terminal: Checksum -xxxxxx? ( didn't work )

---

### Post by Ryupower on 2006-10-29
> **meng said:**
> The ISO should be 700 MB, so I suspect you still have a partial download, perhaps your download manager is able to complete the download given those two files.


It says it's: 694.9 MB
close enough? :D

The manager claimed it's done ( axel )

---

### Post by maniacmusician on 2006-10-29
if you use K3b, there is a checksum option before you start burning. That's what I've always used.

edit: also, clarify; are you using windows or linux?

---

### Post by meng on 2006-10-29
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)
has instructions for checking md5sum in windows
in linux: md5sum [name of file]

---

### Post by Ryupower on 2006-10-29
> **maniacmusician said:**
> if you use K3b, there is a checksum option before you start burning. That's what I've always used.

edit: also, clarify; are you using windows or linux?

I use ubuntu's default nautilus. Where you just drag and drop...ubuntu. ^^

> **meng said:**
> [http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)
has instructions for checking md5sum in windows
in linux: md5sum [name of file]
It's working! Is it normal that it takes forever until it makes a script?
Because it's....sorta not doing anything


nvm, it did something: 1f9baed847eff89b03c754fcaea8070e  
O_o

---

### Post by taurus on 2006-10-29
> **Ryupower said:**
> Hi, downloaded Kubuntu Live CD, 
Now, pasted it on the Disc, two options:
" create from Image"
or
"Create with file"?


silly question I know
Create from image.  In other words, you want to burn that .iso as an image file, not a data file or you won't be able to boot...

---

### Post by meng on 2006-10-29
4f5a12059e1a7f729c396601081ba7f1  kubuntu-6.10-alternate-amd64.iso
23347e2e519f0f638cf0161ae65f17f8  kubuntu-6.10-alternate-i386.iso
e7f605ca5134dcdbcbb56e7fc0ceffee  kubuntu-6.10-alternate-powerpc.iso
0b5b707fda9a7cda9868447df497f36d  kubuntu-6.10-desktop-amd64.iso
1f9baed847eff89b03c754fcaea8070e  kubuntu-6.10-desktop-i386.iso
f2ce77ef53e85c7bf281ee71f3ec8414  kubuntu-6.10-desktop-powerpc.iso

Lucky you, it's a match.

---

