---
title: "Brother MFC-5440CN"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by Bigguy2468 on 2006-10-12
I am having a problem getting a new Brother MFC-5440CN to print in ubuntu. I installed the drivers following the instructions that I found here:

[http://www.linuxquestions.org/hcl/showproduct.php/product/3009](http://www.linuxquestions.org/hcl/showproduct.php/product/3009)

Everything is install and System > Administration > Printing shows the printer. The one and only problem that I seem to have is that after clicking print on any program even the "Test Page" I get nothing.

Under CUPS
[http://localhost:631/printers/MFC5440CN](http://localhost:631/printers/MFC5440CN)
I see the printer, but at the top of the heading it says:
MFC5440CN "Unable to lookup host 'usb' - Unknown host"
I don't know why the 'usb' is there anyway because it's hook through a standard patch cable to my HUB and Home Network

The device url is:
Device URI: ipp://usb:/dev/usb/lp0
and that may be where the problem lies. Any help would be appreciated.

---

### Post by Bigguy2468 on 2006-10-15
Hmmm...no replies??

:-k

---

### Post by docshawnc on 2006-10-15
I have the same printer running here on the network.  Give the printer a fixed IP address ex. 192.168.1.100 (you do this by stepping through the configure menu on the printer itself), and then System > Admin> printing and in the printer properties tab, set it to HPJetDirect.  Put in 192.168.1.100 for the host and 9100 for the port.

---

### Post by leonya on 2006-11-13
I just got the printer to work on Ubuntu Edgy. Took me a couple hours (I was ready to give up on it already)!

I had to:
sudo mkdir /var/spool/lpd
sudo dpkg -i --force-all mfc5440cnlpr-1.0.2-1.i386.deb
sudo apt-get install csh
sudo ln -s /etc/init.d/cupsys /etc/init.d/cups
sudo dpkg -i --force-all cupswrappermfc5440cn_1.0.0-1_i386.deb
Then opened [http://localhost:631](http://localhost:631), "Manager Printers"
Should see the MFC5440CN printer, click "Modify Printer"
Device is "AppSocket/HP JetDirect"
Device URI is "socket://192.168.15.102" (printer IP)
Provide PPD file from /usr/share/cups/model/brmfc5440cn_cups.ppd

There is a thread about same topic here:
[http://forums.debian.net/viewtopic.php?t=9917&start=15](http://forums.debian.net/viewtopic.php?t=9917&start=15)

---

### Post by ErrolRay on 2006-11-21
Thank you so much for your information on the MFC5440CN.  Your instructions worked perfectly.
Errol :)

---

### Post by thecure on 2007-04-20
Thanks, worked for me too. "sudo ln -s /etc/init.d/cupsys /etc/init.d/cups" was the piece I was missing to get the install to work correctly.

---

### Post by tnc on 2007-08-09
Hiyas.  Just to add my experience.   MFC5440CN installed flawlessly.  I used the commands at this link [http://forums.debian.net/viewtopic.php?t=9917&start=15](http://forums.debian.net/viewtopic.php?t=9917&start=15) from the above post.  I didi not need the  "sudo ln -s /etc/init.d/cupsys /etc/init.d/cups" command.  Go figure?  My printer is installed on my LAN.  The scan-key tool from brother also works fine.
Thanks for posting the instructions here.
Tim

---

### Post by Cotopaxi on 2008-02-18
I did install, following leonya's instructions, but I only get the information from the cups server: "recoverable: Network host '192.168.15.102' is busy; will retry in 5 seconds..."

Anybody can help me with this? Thanks.

---

### Post by Cotopaxi on 2008-02-18
Ok, I managed to solve it, following the instructions from a Spanish and a German user.

Essentially the instructions are the same as leonya's ones but, at the point of entering an ip-address, these to guys instruct you to enter:

"192.168.1.134"

After doing this, of course I still did not get any result. But then, when I went back to "manage printers" (allways in [http://localhost:631](http://localhost:631)) on the step "Device", instead of choosing "AppSocket/HP JetDirect", I found:

"Brother MFC-5440CN 192.168.0.194".

So I selected this option and in the last step I selected the cups driver from the directory and everything was up and running! :)

This one took me actually more than one week of desperate try and error! ;)

---

### Post by Cotopaxi on 2008-02-19
Now two questions:

1) Is there any similar procedure to set up the scanner and the Fax of this device?

2) Would it make sense to write a "generic" instruction set, so that other people with similer Printers (either from Brother or from other Brands) could succeed in installing their devices?

---

### Post by Cotopaxi on 2008-02-26
Ok guys, I managed to shoot my previous installation into pieces, so I had to re-install Kubuntu 7.10 from scratch.

This time, I installed it as a USB printer and I followed the Brother installation instructions:

In both downloads and installations, users of 64bit systems (Ubuntu/Kubuntu 7.10) will have to install with the "force architecture" option

So, here goes the procedure:

-----------------------------------------------

1) download and Install the lpr-driver:

[http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html]("http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html")

2) download and install the cupswrapper driver:

[http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html]("http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html")

In this installation it can happen that the installation does not take place, because a file is MISSING! read the response of your terminal carefully. Unfortunately, I do not remember any more, which file was missing, so I cannot post it here. 

3) For 64bit systems you have to create some "symbolic links". I don't know, what that means.

[http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#142]("http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#142")

------------------------------------

Once this was done, my printer works! YEAHHH! :)

---

### Post by luvit on 2008-03-14
Hi. I installed my networked Brother MFC-845CW today and it seems to work well on my clean install of v7.10.  I outlined all the steps I took to install it in my blog (see my signature).

My experience is for the MFC-845CW, but I wrote the outline and provided links to Brother's files in hopes it would benefit other models.

Please let me know if the outline is easy to follow. --Thanks! ...and good luck.

I wrote this outline so that USB printers may be able to follow my directions too... just ignore the steps that mention LPR files if you're connecting via USB.;)

---

### Post by iansane on 2008-03-14
I know this is a different printer but it is a multifunction and as far as installing the drivers it is probably similar.

[http://ubuntuforums.org/showthread.php?p=4517506#post4517506](http://ubuntuforums.org/showthread.php?p=4517506#post4517506)

Yeah it goes on and on in some areas but it is very important to create the nessesary directories and the symbolic link before installing the deb's. It's for USB directly connected but seems like the install would be similar.

---

