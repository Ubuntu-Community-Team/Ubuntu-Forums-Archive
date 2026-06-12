---
title: "Brother MFC-240c on Feisty x64?"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by thegreenman on 2007-04-25
I looked at several howto's on this and see several methods, none precicely for My printer model. Any suggestions from someone with the same model?

Thanks again.

[COLOR="Red"]SOLVED... see last post for solution. [/COLOR][COLOR="Red"][/COLOR]

---

### Post by Seisen on 2007-04-25
Install this file first (I attached both files that you need. All you have to do after downloading them is to double click on them.)

```
mfc240clpr-1.0.0-9.i386.deb
``` then this one
```
mfc240ccupswrapper-1.0.0-9.i386.deb
``` then go to System>Admistration>Printing and click on Add Printer and you should find the drivers for you printer in the list.

---

### Post by thegreenman on 2007-04-26
awesome...thx so much Seisen......:guitar:

---

### Post by Seisen on 2007-04-26
Did it work for you then?

---

### Post by thegreenman on 2007-04-26
actually no, I need to force the 32 bit driver to install, and I'm not sure how to do it.  The forums have been down for 45 min tho.

---

### Post by Seisen on 2007-04-26
This might help you let me know.

[http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#115]("http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#115")

---

### Post by thegreenman on 2007-04-26
I installed the cups driver and the other files, still no go. This is gonna take some tweaking. 

I tried to use these instructions, but the folders are not the same on my install. 

> **VladArod said:**
> After a few days I was able to figure out out to install a Brother printer in Ubuntu X64. I have a brother DCP-340CW with a network connection, but using MFC-210c driver.

Here are the how-to:
1. Follow the instructions of the how-to in post #1. Just use flag --force-all when using dpkg. This forces the installation in a different architecture. 

2. Follow Brother recommendation: "However, if you are using an AMD64 bit distribution, we recommend you try copying the file named "brlpdwrapper" from /usr/lib/cups/filter to /usr/lib64/cups/filter."[COLOR="Red"] ***Okay through this part***[/COLOR]
[COLOR="Red"]this is the part I'm having trouble with. VVVVVVV[/COLOR]
3. Download the cupswrapper source code "bh7-cupsw-src.1.0.0-9.tar.gz" using the third link in [http://solutions.brother.com/linux/sol/printer/linux/cups_source.html](http://solutions.brother.com/linux/sol/printer/linux/cups_source.html). And, unpack it.

4. Just in case, in directory /usr/local/Brother/cupswrapper backup file  cupswrapperMFC210C-1.0.0

5. Using the unpacked source files: 
5.1. Include the string mfc210c in file model_list
5.2. Run: make
5.3. Run: sudo sh mk_cupswrapper
5.4. Overwrite cupswrapperMFC210C-1.0.0 with the new wrapper, 
running: sudo cp cupswrappermfc210c /usr/local/Brother/cupswrapper/cupswrapperMFC210C-1.0.0

6. Using any of printer setup tools and the ppd file in /usr/share/cups/model, the printer "should" be working.

Hope it helps,
Best regards

---

### Post by thegreenman on 2007-04-26
[COLOR="DarkGreen"]EDIT FIXED!

used 
```
sudo dpkg -i --force-architecture 
```to  install the driver and cupswrapper while printer was OFF 
then used ```
sudo apt-get install lib32stdc++6
``` to install the libs. 
copied the file which name starts with "brlpdwrapper" in the
      " /usr/lib/cups/filter" to the "/usr/lib64/cups/filter" folder

now all is working fine. [/COLOR]



Brother website tells me to :
> 
    * I'm using an AMD64 bit version of Linux. Can I use the Brother Linux printer drivers?

      Yes, but please note the following conditions:

      For RPM package users:
      If you cannot print, install lib32stdc++6 or ia32-libs.

      For DPKG package users:
      Install the driver using the command option "--force-architecture".
      If you cannot print, install lib32stdc++6 or ia32-libs.[COLOR="Red"]these packages are .deb so I'm not sure what to do with this[/COLOR]



      Also, try copying the file which name starts with "brlpdwrapper" in the
      " /usr/lib/cups/filter" to the "/usr/lib64/cups/filter".[COLOR="Red"]I did this already [/COLOR]

[COLOR="DarkGreen"]Okay once I got the lib32 installed it's working great !!!! Thanks to Seisen!
[/COLOR]

---

### Post by Cuppa-Chino on 2007-05-27
trying to install the cupsdriver gets me this:

```
desktop:~/Desktop/brother$ sudo dpkg -i --force-architecture mfc240ccupswrapper-1.0.0-9.i386.deb 
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 117468 files and directories currently installed.)
Preparing to replace mfc240ccupswrapper 1.0.0-9 (using mfc240ccupswrapper-1.0.0-9.i386.deb) ...
/var/lib/dpkg/info/mfc240ccupswrapper.prerm: 3: /usr/local/Brother/Printer/mfc240c/cupswrapper/cupswrappermfc240c: not found
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 3: /usr/local/Brother/Printer/mfc240c/cupswrapper/cupswrappermfc240c: not found
dpkg: error processing mfc240ccupswrapper-1.0.0-9.i386.deb (--install):
 subprocess new pre-removal script returned error exit status 127
/var/lib/dpkg/info/mfc240ccupswrapper.postinst: 3: /usr/local/Brother/Printer/mfc240c/cupswrapper/cupswrappermfc240c: not found
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 mfc240ccupswrapper-1.0.0-9.i386.deb
```

please help

also is there anybody outthere that has managed to get printing onto the MFC-240C working if the device is attached to a WinXP computer and shared from there? thank you

---

### Post by Cuppa-Chino on 2007-06-06
manage to get past that but I cannot do 

[I] to install the libs.
copied the file which name starts with "brlpdwrapper" in the
" /usr/lib/cups/filter" to the "/usr/lib64/cups/filter" folder[/I]

I have no such file at all anywhere not one

---

### Post by Cuppa-Chino on 2007-06-07
bump please somebody help me

I cannot find the printer on my list, I cannot copy the files - anybody got any idea what the problem could be?

---

### Post by Cuppa-Chino on 2007-06-17
it seems I cannot generate the ppd file - anyhow latest error is:
```
 sudo dpkg --install --force-architecture mfc240ccupswrapper-1.0.0-9.i386.deb 
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 134591 files and directories currently installed.)
Preparing to replace mfc240ccupswrapper 1.0.0-9 (using mfc240ccupswrapper-1.0.0-9.i386.deb) ...
/var/lib/dpkg/info/mfc240ccupswrapper.prerm: 3: /usr/local/Brother/Printer/mfc240c/cupswrapper/cupswrappermfc240c: Permission denied
dpkg: warning - old pre-removal script returned error exit status 126
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 3: /usr/local/Brother/Printer/mfc240c/cupswrapper/cupswrappermfc240c: Permission denied
dpkg: error processing mfc240ccupswrapper-1.0.0-9.i386.deb (--install):
 subprocess new pre-removal script returned error exit status 126
/var/lib/dpkg/info/mfc240ccupswrapper.postinst: 3: /usr/local/Brother/Printer/mfc240c/cupswrapper/cupswrappermfc240c: Permission denied
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 126
Errors were encountered while processing:
 mfc240ccupswrapper-1.0.0-9.i386.deb

```

if anybody has any ideas PLEASE help I am totally at wits end

---

### Post by Carnical on 2007-06-20
I have a similar problem...
While trying to install mfc240ccupswrapper..., the following error occurred.

Now, I can't run any apt-get type commands without receiving an error that:
E: The package mfc240ccupswrapper needs to be reinstalled, but I can't find an archive for it.
I can't open up the mfc240ccupswrapper-1.0.0-9.i386.deb with gdebi gui anymore, can't --force-all --remove it with dpkg, and can't --install it anymore either :(

Can anybody help me out?  I'm at a loss at what to do at this point (and can't install any new programs really sucks)

error log:
```

sudo dpkg -i --force-all mfc240ccupswrapper-1.0.0-9.i386.deb
(Reading database ... 120539 files and directories currently installed.)
Preparing to replace mfc240ccupswrapper 1.0.0-9 (using mfc240ccupswrapper-1.0.0-9.i386.deb) ...
/var/lib/dpkg/info/mfc240ccupswrapper.prerm: 3: /usr/local/Brother/Printer/mfc240c/cupswrapper/cupswrappermfc240c: not found
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 3: /usr/local/Brother/Printer/mfc240c/cupswrapper/cupswrappermfc240c: not found
dpkg: error processing mfc240ccupswrapper-1.0.0-9.i386.deb (--install):
 subprocess new pre-removal script returned error exit status 127
/var/lib/dpkg/info/mfc240ccupswrapper.postinst: 3: /usr/local/Brother/Printer/mfc240c/cupswrapper/cupswrappermfc240c: not found
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 mfc240ccupswrapper-1.0.0-9.i386.deb

```

---

### Post by Carnical on 2007-06-20
Fixed it, just delete all mfc240ccups* in /var/lib/dpkg/info and run sudo dpkg --remove --force-all mfc240ccupswrapper, then you can reinstall correctly (and your apt-get will work again!)
But, the MFC 240c driver still isn't appearing in the list.... MFC240c is appearing as a printer though

---

### Post by elsaturnino on 2007-06-23
> **Carnical said:**
> But, the MFC 240c driver still isn't appearing in the list.... MFC240c is appearing as a printer though

I had the same problem. Everything installed fine but the driver didn't show up as an option. What you need to do is click on the "Install Driver" button then navigate to where the driver's ppd file is located. Mine was in /usr/share/cups/model.

---

### Post by Cuppa-Chino on 2007-06-23
[COLOR="Green"][SIZE="7"]I can finally print![/SIZE][/COLOR]

now to get scanning across the network to work (hahaha - like that will be easy)

---

### Post by miesnerd on 2007-08-04
wow guys, sorry to be an idiot. I tried apt-get for the first two .deb packages, and it didnt work.  Im under a time crunch, can you give me quick instructions how to get this working. Im on a Compaq 5500 running Xubuntu 7.04.

---

### Post by Seisen on 2007-08-05
Here is a how to I put together for to install the printer on X64 computers.

[http://ubuntuforums.org/showthread.php?p=3139634&posted=1#post3139634]("http://ubuntuforums.org/showthread.php?p=3139634&posted=1#post3139634")

---

### Post by McNee on 2007-12-02
Ok, I've been trying to follow what's going on here. I don't have x64, and I can't seem to figure out how to get this working under Gutsy.

Is there another thread that will be of more help... or am I just really screwing up something here...?  The only thing I can really find different than what's been posted is that the cupswrapper on the Brother site is 1.0.0-10 now versus 9

---

