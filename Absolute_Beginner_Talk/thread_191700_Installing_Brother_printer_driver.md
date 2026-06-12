---
title: "Installing Brother printer driver"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2006-06-07
To my amazement, Brother Industries has written specific printer drivers for my Brother laser printer Model HL-1440.

I have downloaded the "files". But nowhere can I find instructions for what to do next:

Do I have to uninstall some files? and how?

and

How do I install the new drivers?

it does read: Absolute Beginner Talk, sirs.

---

### Post by catlett on 2006-06-07
Either post the link to the page you got the drivers or cut and paste what the page said. From what you posted there is no way to tell what type of file you are using. That is important because different files install differently.

---

### Post by Mark_in_Hollywood on 2006-06-08
This link:

[http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html)

I quote the page, in part, below:

"# To learn which models are supported and to download the appropriate LPR Printer Driver, click here.
# To learn which models are supported and to download the appropriate CUPS Printer Driver or CUPS wrapper driver, click here. "

---

### Post by catlett on 2006-06-08
[http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html) You want to go here and scroll to "Drivers for Debian" and choose your model number.
Download it to your desktop and issue these commands ```
cd /home/[COLOR="Red"]your name[/COLOR]/Desktop
``````
 sudo dpkg -i hl1440lpr-1.1.2-1.i386.deb
``` Then go to System<Administration<Printing to set up your printer. 
I'm off to work, so I can't reply until tonight but others are around if you have issues.

P.S. THis is the Brothers trouble shooting page [http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html](http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html)

---

### Post by bruce89 on 2006-06-08
This printer is already supported in the list of printers at System>Administration>Printing.  If you want to use your own drivers, you can with the add new printer wizard(?).

---

### Post by Mark_in_Hollywood on 2006-06-08
In response to message #4, not the immediately preceeding one, the Terminal returned:

mark@lexington:~/Desktop$  sudo dpkg -i hl1440lpr-1.1.2-1.i386.deb
Selecting previously deselected package hl1440lpr.
(Reading database ... 86723 files and directories currently installed.)
Unpacking hl1440lpr (from hl1440lpr-1.1.2-1.i386.deb) ...
Setting up hl1440lpr (1.1.2-1) ...
mkdir: cannot create directory `/var/spool/lpd/HL1440': No such file or directory
chown: cannot access `/var/spool/lpd/HL1440': No such file or directory
chgrp: cannot access `/var/spool/lpd/HL1440': No such file or directory
chmod: cannot access `/var/spool/lpd/HL1440': No such file or directory
/var/lib/dpkg/info/hl1440lpr.postinst: line 4: /etc/init.d/lpd: No such file or directory
dpkg: error processing hl1440lpr (--install):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 hl1440lpr

Wow!

---

### Post by catlett on 2006-06-08
Bruce says the driver is already available through the ubuntu repository. Which means it will be available when you set up your printer.
Try his way first before we try and install the deb again. Go to the top of your sreen and hit on System<Administration<Printing. When the printer window opens choose "Printer" and then "+ printer" from the menu. Follow the prompts and when you get to the driver section it will ask you to identify your printer from a list. Scroll through the list to your model. If your model is there it means Ubuntu has the driver and it will install it. That will be it.
If that doesn't work we might have to go through the printer setup and then try installing the deb. Hopefully the "printer installation" makes the directories the deb file was looking for.

---

### Post by Mark_in_Hollywood on 2006-06-08
The printer shown is a Brother HL-1440. In windoze, it was easier to print front & back (duplexing). 

Please, accept this apology for the time you have all spent on this. I thought Brother had written an equivalent driver under Linux as an OS.

Thanks to all who looked at this post, never-the-less.

---

### Post by catlett on 2006-06-08
Don't apologise for anything, I love it when a problem gets solved even if noone did anything.:D  I just appreciate you posting and not leaving us wondering what happened.
The toughest thing in linux is hardware support. Drivers are writen by the hardware maker and they do things based on profit. To alot of makers there isn't enough potential profit ion marketing to linux users.
Believe it or not getting any driver from your hardware maker is a big deal in the linux world. The problem is they aren't always as refined or model specific as their windows version.
My advice is to keep your eyes open for linux brother printer posts or threads. Sometimes a group of linux users who share a common hardware product will try and trweak of improve the driver. You might get lucky and find a custom driver that works better.
Glad it worked out, kind of.

---

### Post by ProRodeoAnnouncer on 2008-05-13
HELP.

I am a VERY new ubuntu/linux user. I have just installed it this week and am muddling thru. I was trying to install my printer (a brother FAX-4100) and keep running into problems. I followed the instructions from callet
>
>[http://solutions.brother.com/linux/s...r_drivers.html](http://solutions.brother.com/linux/s...r_drivers.html) You want to go >here and scroll to "Drivers for Debian" and choose your model number.
>Download it to your desktop and issue these commands
>Code:
>
>cd /home/your name/Desktop
>
>Code:
>
 >sudo dpkg -i fax4100lpr-1.1.2-1.i386.deb
>
>Then go to System<Administration<Printing to set up your printer.
>I'm off to work, so I can't reply until tonight but others are around if >you have issues.

but receive the following in the terminal window....


gary@gary-desktop:~/Desktop$ sudo dpkg -i fax4100lpr-1.1.2-1.i386.deb
(Reading database ... 
dpkg: serious warning: files list file for package `fax3800lpr' missing, assuming package has no files currently installed.
101767 files and directories currently installed.)
Preparing to replace fax4100lpr 1.1.2-1 (using fax4100lpr-1.1.2-1.i386.deb) ...
Unpacking replacement fax4100lpr ...
/var/lib/dpkg/info/fax4100lpr.postrm: 3: /etc/init.d/lpd: not found
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: 3: /etc/init.d/lpd: not found
dpkg: error processing fax4100lpr-1.1.2-1.i386.deb (--install):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: 3: /etc/init.d/lpd: not found
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 fax4100lpr-1.1.2-1.i386.deb
gary@gary-desktop:~/Desktop$ 


Would anyone be able to help A NOOB to linux out?



Gary

---

### Post by ubuscout on 2008-05-14
Have u just got a look here ?!?  [http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-FAX_4100](http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-FAX_4100)

---

