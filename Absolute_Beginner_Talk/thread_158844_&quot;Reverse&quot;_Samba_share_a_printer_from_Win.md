---
title: "&quot;Reverse&quot; Samba share a printer from Windows to Linux"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by zerhacke on 2006-04-11
Hello.

My wife's computer is running Windows (I know, she won't switch).  On it there is a Lexmark Z611 printer shared as Lexmark, so the path to the printer should be smb://192.168.0.1/Lexmark.

How would I set up my Linux box to use her shared printer on my computer?  I have already found out that it is most likely that the printer will not work on Linux as nobody seems to know how to set up a Lexmark Z611 on Linux.  I was hoping that it wouldn't need to be set up on this machine since it's being shared by smb:// much in the same way that you don't have to have native write support for an NTFS drive if the drive is shared by SMB.

Before you guys tell me that this should go on a Windows forum, please remember that people on a Windows forum will tell me to post it to a Linux forum.

Thank you all very much in advance.

---

### Post by Ozitraveller on 2006-04-11
Have you got samba all setup so that both machines can see each other? And the printer is shared on windows? What version of windows is it? What version of Ubuntu are you using?

---

### Post by zerhacke on 2006-04-12
[QUOTE=Ozitraveller]Have you got samba all setup so that both machines can see each other? And the printer is shared on windows? What version of windows is it? What version of Ubuntu are you using?[/QUOTE]
Samba is not set up on the Ubuntu box because there is nothing on the Ubuntu box I want to share.

On the Windows machine, the printer is shared along with a couple directories.

Windows is Windows XP Service Pack 2.  Ubuntu is Ubuntu 5.10.

---

### Post by Smika on 2006-04-12
"My wife's computer is running Windows (I know, she won't switch)."

I talked with my wife this weekend and i said to her that she get a new computer form me if she want swich to Linux. Now this week i will install Linux for her. Meaby you must do the same :D ! Because we must kill M$ :evil:

---

### Post by zerhacke on 2006-04-12
If I cannot get the printer shared to the Linux machine, there is no hope of her switching to Linux.  She will not do it.  I've had her test drive Linux for a month after a Windows crash and she still refuses to change.

Most of her college work requires Internet Explorer, so it's not really an option to switch her anyways.  If the college would stop requiring the use of badly made Active X controls life would be so much easlier.

---

### Post by zerhacke on 2006-04-12
Anyone?  Beuhler?  Beuhler? Beuhler?

---

### Post by joshrobinson on 2006-04-12
[QUOTE=zerhacke]Anyone?  Beuhler?  Beuhler? Beuhler?[/QUOTE]

apt-get install samba
apt-get install samba-common
apt-get install smbclient
apt-get install smbfs

you can add all the names into one apt-get command if you want 
like
apt-get install samba samba-common etc
i do them ususally one at a time so i dont forget anything or mess up

then go into system administration, then printing.. and try to add a network printer
and hope it works

---

### Post by zerhacke on 2006-04-13
I got it to work, Samba is NOT required to print to a printer that is shared on a Windows box.

---

### Post by Ronbo on 2006-04-14
I am having the same problem, what did you do to get it to work?  I can see the printer in the steup of add printer, I go through all the steps, select the correct drivers,  but after I click finish no printers appear in the window.  Only thing there is 'Add Printer' option.

---

### Post by zerhacke on 2006-04-14
I wrote a howto just in case others with a Z611 printer wanted to know how to do it.  The howto is found at [http://ubuntuforums.org/showthread.php?t=159704](http://ubuntuforums.org/showthread.php?t=159704)

Though, if you did everything outlined in that already and the printer is not showing up, I have no idea how to help you.

---

