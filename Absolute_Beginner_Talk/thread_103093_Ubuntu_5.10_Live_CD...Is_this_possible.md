---
title: "Ubuntu 5.10 Live CD...Is this possible?"
date: 2005-12-13
forum: Absolute Beginner Talk
---

### Post by RKCole on 2005-12-13
Hello, everyone.

I finally received the Ubuntu CDs I ordered from the ShipIt site, and I am very impressed.  I have only worked with the LiveCD, and although my vision is quite bad, I was able to figure out where most things were available.  I am looking forward to the installation of Ubuntu which I intend to do later this week.

My question (I know that I am very ignorant in this, but I am really wanting to learn anything and everything I can about Linux as I eventually plan to drop Windows...Cannot really say the same for my wife's enthusiasm, though...).  I have some floppy disks which are formatted with the FAT filesystem.  I was just wondering if it was possible (using the live CD) to mount the floppy disk and to save things such as OpenOffice documents to it?  If so, how would I do this?

Any help would be greatly appreciated.

Thanks and take care.

---

### Post by linbetwin on 2005-12-13
[quote=RKCole]Hello, everyone.

I finally received the Ubuntu CDs I ordered from the ShipIt site, and I am very impressed.  I have only worked with the LiveCD, and although my vision is quite bad, I was able to figure out where most things were available.  I am looking forward to the installation of Ubuntu which I intend to do later this week.

My question (I know that I am very ignorant in this, but I am really wanting to learn anything and everything I can about Linux as I eventually plan to drop Windows...Cannot really say the same for my wife's enthusiasm, though...).  I have some floppy disks which are formatted with the FAT filesystem.  I was just wondering if it was possible (using the live CD) to mount the floppy disk and to save things such as OpenOffice documents to it?  If so, how would I do this?

Any help would be greatly appreciated.

Thanks and take care.[/quote]

I haven't tried it, but I think it's possible. You can save the documents to /media/floppy or sth like that.

---

### Post by RKCole on 2005-12-13
Thanks, linbetwin.

So would I have to mount the floppy drive in that area or is it already mounted automatically when the disk is inserted?

Sorry for all of the questions...I feel ignorant, but with time I'm sure I'll get the hang of it, and I am definitely looking forward to it.

Thanks for the help and take care.

---

### Post by kane77 on 2005-12-13
OK you do it like that...
1. open "Places" menu
2. select "Computer"
3. right click on floppy
4. slect mount volume....
5. you're done, you're able to copy files onto it. And it doesn't matter if it's fat formated...

---

### Post by az on 2005-12-13
Fat or Vfat or msdos filesystems have an open spec and have full linux support.  When you click on the floppy, it will mount it and detect what filesystem it has and mount it.

---

### Post by RKCole on 2005-12-13
Thanks, everyone.  I rally appreciate the help.  I am just curious now (sorry for all of the questions):  Is there also a way to format the floppy disk into a FAT format or am I pushing it?  I'm reading through some books to learn the various commands and terminal methods, but I'm only coming along slowly.

Thanks again.

Take care.

---

### Post by sjh on 2005-12-13
[QUOTE=RKCole]Is there also a way to format the floppy disk into a FAT format or am I pushing it?  
[/QUOTE]

I use this:

  Applications>System Tools>Floppy Formatter 

Enjoy
SJH

---

