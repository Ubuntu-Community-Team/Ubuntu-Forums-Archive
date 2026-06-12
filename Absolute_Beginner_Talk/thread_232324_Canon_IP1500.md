---
title: "Canon IP1500"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by xamfer on 2006-08-08
Ok, I read a couple of posts about how to install the driver for printer Canon PIXMA IP1500.

I read that for some BJC800 or BJC7000 driver would work ok, but with some printinf config problems. I used both, but all I got from my printer was the light to tild, and no printing.

I installed the driver after reading this post ([http://www.ubuntuforums.org/showthread.php?t=93265](http://www.ubuntuforums.org/showthread.php?t=93265)) and ok. But when I try to print, now my printer does not even tild its light (kind of a non responsive answer), and of course, it does not print at all.

Remark: My Pc detecs my printer, I choose IP1500, then select the driver in the list (PIXMA-iP1500-Ver.2.50) and that should be it. But no...

Any help would be highly appreciated!

---

### Post by louis_nichols on 2006-08-08
I have the same problem and would love to see a solution. It seems unlikely that, after about a year from discovering that illusive driver on the japanese site and using it with good results, all is lost because of dapper...

---

### Post by avtolle on 2006-08-08
[http://www.ubuntuforums.org/showthread.php?t=93265&page=5](http://www.ubuntuforums.org/showthread.php?t=93265&page=5), post 49; this mentions the need to download an earlier version of a certain lib package. Have either of you done this? I don't use the subject printer, but thought this might be of some assistance.

---

### Post by xamfer on 2006-08-08
Ok thanks! First of all, I just read your post and start replying. So this is a very uninformed and quick question:

If I have to install anything first, then I should probably then uninstalled the ip1500 driver first? If so, how to uninstall the driver?? I'm an absolute noobe and installing is already a process while I'm still learning some linux - ubuntu, imagine what the word "uninstall" means to me!

Thanks a lot. Will report back if anything happens at all!

PD: Have you tried turboprint with this ip1500?? does it print at all (ip1500) with this driver/program?? Report back!

---

### Post by avtolle on 2006-08-08
As mentioned, I don't have/use subject printer; the thread that I posted the link to indicates that the Turboprint driver will work (albeit at 300 dpi), there needs to be some modification to avoid the logo printing. As to your question about installation, please see the thread and the specific post; hopefully, this will answer your question. HTH.

---

### Post by xamfer on 2006-08-08
Excellent!!!!!!!!!

ok, for everyone out there with a Canon IP1500, here's the deal!

1. Download the following: [http://ftp.debian.org/debian/pool/ma....18-1_i386.deb](http://ftp.debian.org/debian/pool/ma....18-1_i386.deb)

2. Install the downloaded file

3. From Terminal write the following command: 
sudo dpkg -i libpng10-0_1.0.18-1_i386.deb

4. Next, still from Terminal write the following command:
sudo apt-get -f install

5. Download [http://www.ubuntuforums.org/attachment.php?attachmentid=3836&d=1132790081](http://www.ubuntuforums.org/attachment.php?attachmentid=3836&d=1132790081)

6. Open the README file and follow instructions, as follows

7. Extract from the .zipo file the " install-iP500 " file. I did into my Desktop, so next step is just for this case.

8. Open Terminal and write the command cd /home/user/Desktop (remember we are assuming the extracted file is in the Desktop)

9. Write the command sudo ./install-iP1500 , the printer installation begins...

10. " Printers " windows opens. Right click in New Printer and click Add.
You Canon iP-1500 printer should be detected (I dont know why but in my PC and in MY LIST it shows two iP-1500 printers detected, but who cares, select one). Look for the driver (PIXMA iP1500 Ver.2.50).

11. Print Test page... and enjoy.

References:
- [http://www.ubuntuforums.org/showthread.php?t=93265&page=5](http://www.ubuntuforums.org/showthread.php?t=93265&page=5)
- [http://www.ubuntuforums.org/showthread.php?t=93265&highlight=printer+ip1500](http://www.ubuntuforums.org/showthread.php?t=93265&highlight=printer+ip1500)

PD: Ok, this printer driver issue was my last excuse for having windows xp installed in my PC. I'm now free!!!!!!!!


Remark: My Pc sometimes does not detect my printer unless my printer is ON before I boot my PC.

---

### Post by louis_nichols on 2006-08-09
Great news! I'll try it as soon as I get home!

---

### Post by Stingray8989 on 2007-05-30
I have this printer and was just about to follow your steps, but the link in step 1 is no longer active. anyone have an alternative?

---

### Post by ib80 on 2007-06-16
The first link is just the package being installed in step 2 and 3 in the ubuntu packages archives.

But I doubt this works anymore. I admit I haven't even tried yet, but the libpng package is now at version 1.2.15. A long way from 1.0.18 !!

Anyone got this printer working under feisty ?

Thx,
ib

---

