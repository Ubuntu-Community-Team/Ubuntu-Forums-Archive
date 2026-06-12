---
title: "Copy Windows Hard Drive"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by Ciego on 2006-10-01
I am using the live CD on an old laptop and my goal is to copy the entire hard drive to an external USB hard drive.  I have everything working but I am not quite sure how I can just copy the whole drive over.  Any ideas?

The laptop is running Windows 98. (until I can backup the drive and install Ubuntu)

Thank you

---

### Post by kewldude606 on 2006-10-01
You can see the windows drive and the USB drive on the desktop?  Just double click on both, press Control-A on the windows hard drive, and drag everything to the USB hard drive.

---

### Post by Imsati on 2006-10-01
Do you have an install CD that came with your hard drive? Most of them have an option to do a drive-to-drive data transfer.

If not, I would just do it from Windows. Open My Computer to the destination drive, then open another My Computer to the current drive and just drag the files over.

I learned the hard way though to "COPY" the files, and DO NOT "MOVE" the files. One mistake moving and bye-bye files.

---

### Post by Ciego on 2006-10-01
Actually .... no ... I cannot see the windows drive.  Where is it mounted?

---

### Post by think13 on 2006-10-01
As long as you can read the files from your hard drive, I would try

cp -r (path of the hard drive you want to copy from) (path of hard drive you want to copy to)

I'm kind of a newb, so I wouldn't trust this unless someone more experienced agrees with me.

---

### Post by Ciego on 2006-10-01
The reason I am using the live CD is because Windows 98 will not recognize the USB drive and I figured the Ubuntu live CD would handle the task better than Windows.  (The USB autodetect workd fine with the live CD)

---

### Post by think13 on 2006-10-01
Linux has problems reading NTFS filesystems.  Try doing it from windows like lmsati said.

I'm not sure you can install packages from the live cd, but try looking at NTFS-3g.

---

### Post by Ciego on 2006-10-01
Where can I find the hard drive using the live CD?

---

### Post by gn2 on 2006-10-01
By far the easiest way to do what you want is to remove the laptop hard drive and fit it in a USB enclosure, or use a 2.5" to 3.5" IDE adapter, and copy and paste the contents to another PC.

Hard drive removal from a laptop can sometimes be easier than you might think. Depends on the model.

---

### Post by Ciego on 2006-10-01
I do not have an adapter here and if I could do it that way, then how is that any different than what I am trying to do now?  I would still be trying to copy the windows hard drive from a linux machine onto my USB hard drive.  Can I not do this using the live CD?

---

### Post by Imsati on 2006-10-01
> **Ciego said:**
> The reason I am using the live CD is because Windows 98 will not recognize the USB drive and I figured the Ubuntu live CD would handle the task better than Windows.  (The USB autodetect workd fine with the live CD)

Ahhh..missed that part on the first-read.

Do you have a disk that came with the USB Drive? Have you looked online for drivers that will allow Win98 to support it? Do you have a Home LAN? Can you hook it up and access the files from another computer? If no LAN, have you tried a direct connection with another computer?

The adapter gn2 mentioned is a great thing--I have one I use quite a bit. you can buy from tigerdirect or newegg for around $10 and on ebay for around $3-5 (plus shipping of course)

---

### Post by Ciego on 2006-10-01
I do have a disk that came with the USB drive, but I cannot get anything to work via USB in windows 98.  I do have a home LAN, but I cannot seem to get the laptop on it. (network connections are all messed up on it, and it has been way too long since I messed with those on Windows 98).  I figured there had to be an easy way of just running the Live CD and copying the entire internal drive onto the USB drive.  I have the USB drive showing up using the live CD but I cannot figure out where I find the internal hard drive using the live CD.

---

### Post by think13 on 2006-10-01
The problem is that your hard drive is probably formatted using NTFS a format used by Windows, which Ubuntu can't read or write from by default.  I'm not sure what you can do.

If (if) your hard drive can be seen, it would be in /media

---

### Post by Ciego on 2006-10-01
Thank you for your help everyone.  I just booted back into Windows and actually got the USB hard drive to work.  Now I am just going to backup the entire hard drive so I have important documents and then get this Windows 98 OFF of this computer.

---

### Post by think13 on 2006-10-01
Get it off and replace with Ubuntu (or xubuntu)!

If I had an old computer I could just play around with, thats what I would do.

---

### Post by Ciego on 2006-10-01
That's exactly what I am going to do.  Actually, this is a friend's laptop and they got a new one so I am putting Ubuntu on it for them to mess around with. (they have no other use for it now) I amhonestly not even sure if Ubuntu will fit on the hard drive.  I think  it may be only 5GB.

---

### Post by mjpatey on 2006-10-01
If the drive you want to copy was formatted in Windows 98, it was probably a FAT32 drive, not NTFS.

I'm usually someone who asks questions around here, as opposed to answering them... but I do know that Ubuntu can read and write to a FAT32 drive natively, and can read from an NTFS drive, but not write to it.

To the OP:  I'd do a forum search (or better, a Google search) on mounting a drive in Ubuntu.  There are some very good howtos and tutorials out there, though I'm sorry I don't have any bookmarked links to give you myself.  The mounting process is a little different for NTFS and FAT32 drives, so find out what kind you have before searching.

Good luck!

-- edit: Way to go!  I'm glad you found a way that worked.

---

### Post by think13 on 2006-10-01
The basic install of Ubuntu takes about 2 GB.
I'm not sure with Xubuntu, but it is designed for computers with less stuff, so I would use that.

---

### Post by kidders on 2006-10-01
> **think13 said:**
> Linux has problems reading NTFS filesystems.In actual fact, Linux can read NTFS without any problems, but my guess is you're using FAT32. (You said something about Windows 98, right?)

In any case, if it were me, I'd consider a disk dump. That way, If I wanted to, I could simply dump the data back, and my Win98 install would boot back up as if it had never left. Copying the files back and forth won't always have the same effect.

If you don't care about your Win98 install, and only want your personal files, ignore my suggestion though!

---

### Post by gn2 on 2006-10-01
> **Ciego said:**
> I do not have an adapter here and if I could do it that way, then how is that any different than what I am trying to do now?  

The Windows98 drive in your laptop will be FAT32 File System.

Ubuntu can read and write from/to Fat32.

(And read NTFS)

When you put the W98 laptop drive in a USB enclosure, it becomes a mass storage device. 
When you use a 2.5" to 3.5" adapter it becomes an IDE hard drive.

Connect it to your Ubuntu Desktop PC (mentioned in your signature) and you can copy the files you want to save across.

Once everything you want is on the Desktop PC you can then copy them to your other USB drive if you wish.

Or search Google for the W98 driver  for the USB hard drive you've got (should be on manufacturer's website)

---

### Post by mojaz on 2008-06-30
Hello ,  I am using ubuntu" live" and want to copy my windows file to my external hard drive but get errors " read only ".  Does anyone know how to get around this ?  I am try to get my window files off this machine any suggestions ?  I can only boot the machine using ubuntu live  or rhat ver.
8 .

---

### Post by mjpatey on 2008-06-30
I assume the error is happening on the external drive you're trying to copy to...

1. On Ubuntu's desktop, click "Places" and go to "Home Folder".
2. Click on "File System" on the left side, then double-click on "media".
3. One of the folders listed there should be your drive, if it's mounted.  Right-click it and select "Properties".
4. Up top, click the "Permissions" tab.
5. Under "Others", for Folder Access, select "Create and Delete".  For File Access, select "Read and Write".
6. If the system doesn't let you do this last step, it's because it sees your external drive as having been created by someone more powerful than your current user, and you don't have permission to change these settings.  In this case, in a Terminal, type "sudo nautilus", then repeat steps 2 through 5.

CAUTION:  In step 6, "sudo nautilus" gives you top-level superpowers.  You'll be able to delete anything you want, and if you're not careful you can do harm to your Ubuntu installation and/or your personal data.  As soon as you've successfully applied permissions, CLOSE your superuser Nautilus window and the Terminal window that opened it.

Hope this helps!

-Mark

---

