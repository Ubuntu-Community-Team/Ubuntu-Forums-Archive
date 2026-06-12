---
title: "Scanner not working"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by matchstich on 2006-12-26
> **Illuvator said:**
> To apt-get it you will need to have the other repositories enabled for it to work. Apologies for double posting I hadnt noticed the question above.

To add the other repos to allow the apt-get to install the bluefish follow the guide here:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)

Then in terminal
```

sudo apt-get update
sudo apt-get install bluefish

```

and that should sort you out. To install from the .deb file, merely rightclick on the file on your desktop, go to permissions, allow executing (tick the box) then close that and double click on the file and it should install.
Il

ok, i have a question about the way stated here for installing deb packages. . if i do what you say, will it install where it needs to be. or do i have to tell it  where.  i am a newbie trying to get a scanner to work and am having no luck. the directions on the sane page are greek to me.
thanks

---

### Post by Sef on 2006-12-26
What make and model is your scanner?  Have you tried Applications > Graphics > Sane Image Scanner?

---

### Post by matchstich on 2006-12-26
> **Sef said:**
> What make and model is your scanner?  Have you tried Applications > Graphics > Sane Image Scanner?
it is a acer/benq 620u,  when i go to  xsane image scanner, i get failed to open device, invalid argument
i have everything downloaded on my desktop.  i went to the sane page and the directions there make no sense to me.
tried a few times to get it installed but no luck. i have the firmware from the install disk.
and got the sane backends and front ends. 
thanks

---

### Post by matchstich on 2006-12-26
> **Sef said:**
> What make and model is your scanner?  Have you tried Applications > Graphics > Sane Image Scanner?
it is a acer/benq 620u,  when i go to  xsane image scanner, i get failed to open device, invalid argument
i have everything downloaded on my desktop.  i went to the sane page and the directions there make no sense to me.
tried a few times to get it installed but no luck. i have the firmware from the install disk.
and got the sane backends and front ends. 
thanks

---

### Post by Sef on 2006-12-26
How are you connecting? SCSI, USB, or parallel port?    The first two will work.  The last doesn't.  

Check out the [Sane Project]("http://www.sane-project.org/cgi-bin/driver.pl?manu=acer&model=620&bus=any&v=&p=").

---

### Post by matchstich on 2006-12-26
its a usb, 
thanks
it shows up in device manager

---

### Post by jescis on 2007-05-21
Hi I'm new to these boards and Ubuntu. But I did do something related to this subject. I downloaded and extract the *.BIN file to /usr/share/sane/snapscan, in a round about way. I have acer's 320U scanner. I downloaded and opened the zip file, and extracted the *.BIN file to a folder so I could copy it to /usr/share/sane/snapscan using  sudo from the "command prompt" or er terminal. :)

p.s.  here's the benq address 

[http://www.benq.us/support/downloads/index.cfm?productline=9](http://www.benq.us/support/downloads/index.cfm?productline=9)

---

### Post by neotasic1 on 2007-05-24
> **matchstich said:**
> its a usb, 
thanks
it shows up in device manager

I don't know if you fixed the scanner problem or not, but I read this post by overdrank in response to another question about scanners not being recognised.  I believe this will help me solve the same problem you have outlined with your ACER - i certainly think it will fix my problem that I posted regarding a Vuego 3300 usb scanner.  Unfortunately, I can't test this for a few days.  The link he gave was this:-

[https://wiki.ubuntu.com/HardwareSupportComponentsScanners](https://wiki.ubuntu.com/HardwareSupportComponentsScanners)

Your scanner is listed as supported, and it also gives you instructions on how to go about enabling it.  

Interesting for me was the information on the ACER/Benq 3300 scanner.  After finding out which driver file I needed from the above link, I then googled for a site for download, as I don't know if I still have the firmware file on disk anywhere.  The google search amongst other things returned this site.  

[http://www.wlug.org.nz/Benq3300/4300ScannerSetup](http://www.wlug.org.nz/Benq3300/4300ScannerSetup)

Although this is a different scanner to yours, the instruction should be transportable to your model also with some small changes.  A post of how you go would be appreciated.

---

### Post by dazzled on 2007-05-29
A similar problem was solved here- [http://ubuntuforums.org/showthread.php?t=264850&highlight=benq+scanner](http://ubuntuforums.org/showthread.php?t=264850&highlight=benq+scanner)

Do you have the windows driver CD for the scanner?

---

### Post by JayCee212 on 2008-02-03
**[SIZE="4"]How to set up scanner Acer 320U on Kubuntu 7.10 Gutsy Gibbon[/SIZE]**


1- You need to download the AcerScan320U.zip that contains the  firmware for the scanner, the acerfirm script to upload the firmware and this tutorial in .doc format.  Please note that this firmware is specific for the Acer 320U scanner!

	[URL="http://jaycee212.freeweb7.com/AcerScan320U.zip"]http://jaycee212.freeweb7.com/AcerScan320U.zip
[/URL]

2- Make sure that **sane**, **sane-utils**, **libsane** and **libsane-extras** are installed.  After that, in order to properly identify where your scanner is plugged into, run in a terminal window:  **sane-find-scanner**  The important info will be in the uncommented lines, for example, on my pc the result is:

	[B]found USB scanner (vendor=0x04a5 [Color], product=0x2022 [ FlatbedScanner 13])
	at libusb:001:005[/B]


3- In a console window, login as** root** and copy u34v101.bin  to  /etc/sane.d/ by typing:  **cp u34v101.bin /etc/sane.d/**


4- Edit the snapscan file by entering:  **kdesu kate /etc/sane.d/snapscan.conf**


5- The "firmware" line of snapscan.conf file should be:  **firmware /etc/sane.d/u34v101.bin**


6- Insert a line above the firmware line saying:  **/dev/usbscanner bus=001**


7- Upload the firmware by running the acerfirm script: ** ./acerfirm /dev/usbscanner u34v101.bin**


8- Restart your computer and


9- Happy scanning using Kooka or XSane!  :)


Jay Cee

---

