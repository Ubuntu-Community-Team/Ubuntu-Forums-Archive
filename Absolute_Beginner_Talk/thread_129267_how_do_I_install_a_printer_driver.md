---
title: "how do I install a printer driver?"
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by damianubuntu on 2006-02-13
I feel stupid asking this, but I've looked and can't find anything about it.  I've downloaded a .rpm file for the printer, but I don't know what to do with it!!
Help!

Thanks

---

### Post by darkbullet87 on 2006-02-13
If it's a Lexmark (or most Dell's) there is a great tutorial [HERE]("http://www.ubuntuforums.org/showthread.php?t=49714&highlight=Dell+Printer+Driver"). 

That helped me set up my Dell A920 printer the other day with no problems.

---

### Post by Ubuntuud on 2006-02-13
There are several ways:
First, have you checked if it isn't allready available? Go to system > administartion >printers (it might not be completely correct, I'm translating.) Select "add printer" and press enter. You should follow the steps (which aren't to many (one or two.))

If it isn't in the database you could select the printerdriver in the same window, there should be a button with "install driver" (translating...) Browse to you file and select it. I never tried it, but maybe it will ask for a .deb file. Than you should download "alien". This can be done through synaptic or by typing "sudo apt-get install alien". Then open a terminal an type "sudo alien -d /folder/the/file/is/in/filename.rpm" (you could also type "alien --help" for more information.) A .deb file will be created in the same directory.

If that all fails you could also just try to install it with the .deb file. First type "cd /folder/the/file/is/in", then "sudo dpkg -i filename.deb.

Hope this helps.

---

### Post by bartbes on 2006-02-13
You can install rpm's as Ubuntuud said but it is not recommended, because maybe the software isn't compatible with Ubuntu. But you can give it a shot. I've had a problem because I converted an rpm once..

---

### Post by damianubuntu on 2006-02-13
thanks, I found a tar.gz and used that in the end - I think its OK now, it just keeps telling me the paper tray is empty, but I've had that problem with this printer before.  And yes, there is paper in the tray ;-)

---

