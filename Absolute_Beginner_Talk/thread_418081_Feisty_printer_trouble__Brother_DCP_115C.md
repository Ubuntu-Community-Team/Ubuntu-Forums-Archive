---
title: "Feisty printer trouble / Brother DCP 115C"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by TURNER on 2007-04-22
Hi all, 

Upon Feisty release I decided to conduct a fresh install of Ubuntu using the new Feisty release. All has gone smoothly aside from one glitch, my printer now refuses to work!

Using the instructions provided below I was able to get my Brother DCP 115C printer working completely fine in Edgy:

```
1. Download "mfc210clpr-1.0.2-1.i386.deb" and "cupswrappermfc210c_1.0.0-1_i386.deb" from brother website

2. Open Terminal (Applications --> Accessories --> Terminal) and do following

3. Install csh, in Terminal type:
a. sudo apt-get install csh

4. Install mfc210clpr-1.0.2-1.i386.deb, in Terminal type:
a. sudo mkdir /var/spool/lpd
b. sudo mkdir /var/spool/lpd/MFC210C
c. sudo dpkg -i mfc210clpr-1.0.2-1.i386.deb

5. Install cupswrappermfc210c_1.0.0-1_i386.deb, in Terminal type:
a. sudo dpkg -i cupswrappermfc210c_1.0.0-1_i386.deb
NB: Ignore any errors, especially if last line is" lpadmin: Unable to copy PPD file!"

6. Turn printer on
```

Followed by:

```

sudo gedit /etc/fstab

ADD:

none /proc/bus/usb usbfs auto,devmode=0666 0 0

sudo umount /proc/bus/usb
sudo mount /proc/bus/usb
sudo mknod -m 666 /dev/usbscanner c 180 48 
```

As mentioned, this was enough to get my printer working in Edgy.....seems Feisty doesn't like it however!

The printer is present under system admin printers, and accepts a test page, which doesn't make it to the printer, interestingly enough my printer does momentarily display "receiving data"....but doesn't attempt to print.

Feistys new auto detection wizard does recognise my printer successfully as a Brother DCP 115, and recommends a driver as part of the set up....however this results in the same story as before!

Any assistance or recommendations??

---

### Post by TURNER on 2007-04-22
bump....sorry but I really need to print a doc....has anyone any ideas regarding my problem?

---

### Post by TURNER on 2007-04-22
Any brave man women or child willing to take on my issue???

Please....:)

---

### Post by TURNER on 2007-04-23
ok one more try....has any one experiencing similar problems? or can anyone shed some light on this issue?

---

### Post by Kynan on 2007-04-24
Hey mate your not the only one. I installed feisty fresh about 2 days ago and i also had my dcp-115c working with the mfc-210c driver in edgy and it doesn't work in feisty doing exactly as you described it sits in the print queue without printing. 
I did hear they were making a driver for this printer for linux, hopefully it will be released sooner rather than later as id like to ditch windows and stop relying on it to dual boot to print... 
Can anyone help?

---

### Post by TURNER on 2007-04-25
Hello mate.

I also posted for assistance on a different thread, I received this reply with an apparent resolution, I am yet to test this:


[http://ubuntuforums.org/showthread.p...90#post2277190](http://ubuntuforums.org/showthread.p...90#post2277190)

cheers

Dale

---

### Post by Kynan on 2007-04-26
Thanks mate, from your advice i was able to get it working. I posted how i managed to get it working aswell on the link you gave me. 
Cheers buddy.

---

### Post by Chilli Bob on 2007-04-26
I followed Turner's link, but it just took me back to the forums main page.  Could someone please check the link and put the correct one up.  I REALLY need to get this printer working. (No dual-boot to fall back on). ](*,)

---

### Post by vanadium on 2007-04-26
Did you try installing the printer using  "add printer" in System - Administration - Printing? Your exact driver is not listed, but there are other Brother DCP models listed that are worth trying. Additionally (try that first) I have found this page from Brother forusing your printer under CUPS

[http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html)

---

### Post by Chilli Bob on 2007-04-26
Yes, System-Admin-Printing adds the 210 printer to the "printers" box, but it doesn't work when you try to print.

I found the correct links if anyone wants them. First download the script for your particular distro from post #283 on this page... [http://ubuntuforums.org/showthread.php?p=2277190#post2277190]("http://ubuntuforums.org/showthread.php?p=2277190#post2277190")

then follow the instructions in post #318 on this page...
[http://ubuntuforums.org/showthread.php?t=105703&page=32&highlight=fiesty+brother+printer]("http://ubuntuforums.org/showthread.php?t=105703&page=32&highlight=fiesty+brother+printer")

This got my printer working. The scanner is still undetectable though, unless I run xsane using sudo, which isn't ideal.  I remember this happened when installing to Dapper, and it was a permissions issue. Will jab at it with a pointy stick on the weekend and let you know if I find a solution.

Thanks to all for the help with the printer!!

---

### Post by Kynan on 2007-04-27
Good to hear you got the printer working, sorry i forgot to mention TURNERS link didn't work and to give the link to where i found it but you seemed to find it ok. 
It seems the scanner is still to be working properly (I can get it to work via running the command sudo xsane in the terminal but this is a pain. printing is a good start. I've got no time to have a stab at getting it working properly till next week but yes, definitely let me know know if you get it working :)

---

### Post by TURNER on 2007-04-27
Hi all....

I am still having trouble :( 

I posted this accros on the other thread too (with the shell script)

****....still no success...

I followed the instructions to a T.

First downloaded the Feisty.sh

gave it the correct permissions

ran sudo /home/"username"/Desktop/Feisty_Brother_MFC-210C_Installer.sh (selected printer only)

followed the prompts, and nothing....

I removed the printer and tried it again.....still nothing.

The printer is there, recognised as MFC210C....but within the properties dialog box (after selecting print test page is the status: Printing: Printer not connected; will retry in 30 seconds...)

I can amend the paper (or at least paper size), and the printer is plugged into a working usb port....


any ideas :confused:

---

### Post by Kynan on 2007-04-27
Hmm thats curious how you can still change the paper size, yet it will not print, whenever i tried with any other method of installing the printer i was always locked out of all the options. Could you get that far before? also the message you are getting is something i've never come across it might be a slightly different problem.  The only thing i can think of is that you completely remove the drivers first (you probably already have already tried this). incase not type in synaptic search 'brother' and completely remove the cupswrapper and the lpr drivers. then try again.

---

### Post by Kynan on 2007-04-28
As another note i worked out how to allow privilages to the scanner. so no more sudo xsane.
refer to post number 5 on this link [http://ubuntuforums.org/showthread.php?t=166944](http://ubuntuforums.org/showthread.php?t=166944)
Hope it works for you as it did for me.

Edit: i noticed (as everyone else that did this on that link) you get 3 error messages when trying to close before it actually closes. still better than before tho.

---

### Post by TURNER on 2007-04-28
Yep, already removed the drivers, however the scanner driver doesn't seem to want to go away....I'll look into it,  give it another bash today..

cheers mate.

---

### Post by Chilli Bob on 2007-04-28
I don't think I mentioned this in my last post.  The script DID install my printer, but it installed it as a network printer, not a local printer.  I had to go into "properties" after right clicking the printer icon and change the check boxes to "local" and then it worked.  Try that and see if it helps.

Sorry, I should have said this before.

---

### Post by TURNER on 2007-04-29
Finally...a working printer.....thanks lads!

The first time I ran the shell I selected to install printer, scanner, fax :(  and then realised that this wasn't advised of!

Then the brother scanner driver refused to uninstall, blocking the further installation of any other programs!

I've now managed to run the shell, and (after reading Chilli Bob's last post) managed to print a test page!

Cheers!! beers on me

---

### Post by balloons on 2007-04-30
Weird, the script actually installs as a network printer on purpose - it wouldn't work (well for me, and I think for most? in edgy) otherwise..

> **Chilli Bob said:**
> I don't think I mentioned this in my last post.  The script DID install my printer, but it installed it as a network printer, not a local printer.  I had to go into "properties" after right clicking the printer icon and change the check boxes to "local" and then it worked.  Try that and see if it helps.

Sorry, I should have said this before.

---

### Post by dawn_to_dusk_[pt] on 2007-06-03
```
dawn2dusk@dawn2dusk:~/Desktop$ ls
cupswrappermfc210c_1.0.0-1_i386.deb
Dapper_Brother_MFC-210C_Installer.sh
Edgy_Brother_MFC-210C_Installer.sh
Feisty_Brother_MFC-210C_Installer(2).sh
sfa
dawn2dusk@dawn2dusk:~/Desktop$ sudo Feisty_Brother_MFC-210C_Installer\(2\).sh 
sudo: Feisty_Brother_MFC-210C_Installer(2).sh: command not found

```

i can't do that ... :\ damm... i've got to print in windows ? that sucks ....

---

### Post by balloons on 2007-06-06
Your code doesn't looks correct. You got the \) to take the character as literal, but no quotes. try it without the '\)" or, rename the installer to just feisty.sh and try.

> **'dawn_to_dusk_[pt] said:**
> ```
dawn2dusk@dawn2dusk:~/Desktop$ ls
cupswrappermfc210c_1.0.0-1_i386.deb
Dapper_Brother_MFC-210C_Installer.sh
Edgy_Brother_MFC-210C_Installer.sh
Feisty_Brother_MFC-210C_Installer(2).sh
sfa
dawn2dusk@dawn2dusk:~/Desktop$ sudo Feisty_Brother_MFC-210C_Installer\(2\).sh 
sudo: Feisty_Brother_MFC-210C_Installer(2).sh: command not found

```

i can't do that ... :\ damm... i've got to print in windows ? that sucks ....

---

### Post by martinp23 on 2007-06-10
> **'dawn_to_dusk_[pt] said:**
> ```
dawn2dusk@dawn2dusk:~/Desktop$ ls
cupswrappermfc210c_1.0.0-1_i386.deb
Dapper_Brother_MFC-210C_Installer.sh
Edgy_Brother_MFC-210C_Installer.sh
Feisty_Brother_MFC-210C_Installer(2).sh
sfa
dawn2dusk@dawn2dusk:~/Desktop$ sudo Feisty_Brother_MFC-210C_Installer\(2\).sh 
sudo: Feisty_Brother_MFC-210C_Installer(2).sh: command not found

```

i can't do that ... :\ damm... i've got to print in windows ? that sucks ....

Try 

```
 
sudo ./Feisty_Brother_MFC-210C_Installer\(2\).sh 

```

---

