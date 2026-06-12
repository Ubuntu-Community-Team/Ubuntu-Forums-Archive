---
title: "External Hard Drive problems"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by MonuMan5 on 2007-08-21
My external hard drive was coming up as read only.  So I tried to mount my external hard drive using the NTFS Configuration Tool.  But by random chance, my computer froze during this process.  

Now when I start my computer, the hard drive wont even read.  When I try the NTFS Configuration Tool program it gives me a dialog that says:  

$Logfile indicates unclean shutdown (0, 0) Failed to mount '/ dev/sdc1': Operation not supported Mount is denied because NTFS logfile is unclean.  Choose one action:  Boot Windows and shutdown it cleanly, or if you have a removable device then click the 'Safely Remove Hardware' icon in the Windows taskbar notification area before disconnecting it.  Or Run ntfsfix version 1.13.1 on Linux unless you have Vista.  Or Mount the NTFS volume with 'ro' option in read-only mode.  

Problems with this:  
1.  I don't have windows.  
2.  I cannot find a program called ntfsfix version 1.13.1
3.  I don't know how to mount with the option of read only

If i could get this thing just reading again, i'd be semi happy.  It'd be nice to be able to write and read though.  

Please help a noob out.  Thanks.  =o)

---

### Post by ddrichardson on 2007-08-21
Do you need the data on it?

---

### Post by MonuMan5 on 2007-08-21
Yeah, the data is very important.

---

### Post by bodhi.zazen on 2007-08-21
First, if you do not run windows you should convert to a linux native file system.

Second, I would bring the disk to a Windows box and repair it from there.

If that is not possible, take a look at something like test disk. Test disk is in the repositories and available on several live CD's.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

	[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by ddrichardson on 2007-08-21
Further to Bodhi's post - download [system rescue cd]("http://www.sysresccd.org/Main_Page") and create an image before you tinker with anything.

btfsfix is part of ntfsprogs - which is on the repositories.

---

