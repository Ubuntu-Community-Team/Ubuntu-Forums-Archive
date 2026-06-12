---
title: "Installing a Brother MFC-210C on Feisty"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by Killtown on 2007-05-29
I there a current instruction guide for this?  I tried the older guides on these forums and installed on the files they said to, but my printer isn't working.  The printer seems to be recognized in System > Admin > Printing  and when I try to print something, the printer reads "transmitting data", but won't print anything.


**[SOLVED]** See [here]("http://ubuntuforums.org/showpost.php?p=2925204&postcount=12").

---

### Post by Chilli Bob on 2007-05-29
OK, there is a script written now to set this up, makes it easy.  Try going to [this]("http://ubuntuforums.org/showthread.php?t=418081") page and scroll down me at post #10 where I explain how I set up my similar-but-different printer. It uses the same script I believe.

Oh, yeah, and the script installs it as a network printer, so if like me you need it set to a local printer you will have to go into the printer properties and change it manually.

---

### Post by Killtown on 2007-05-29
Ok, I've done the following:

Downloaded the script you suggested:
[http://ubuntuforums.org/showpost.php?p=2539199&postcount=10](http://ubuntuforums.org/showpost.php?p=2539199&postcount=10)

Then did the following:

> 1. Make sure your printer is connected to your computer.

2. right click on the downloaded file and goto properties and the tab permissions click allow executing file as program.

3. go to the terminal and type
sudo /home/"username"/Desktop/Feisty_Brother_MFC-210C_Installer.sh

4. A box should come up, asking what you want to install (beautiful), choose to install just the printer first because when i tried doing both at the same time nothing worked for some reason.

5. Follow the pop up messages.

6. Once completed the print box should appear and now right click on it and select properties, if you can change the paper type you should have no troubles printing, Try printing a test page, if it doesn't work then try again it took me 2 attempts to get it to work.

7. Try installing the Scanner (mine still doesn't work but maybe it will work for you)

[http://ubuntuforums.org/showpost.php?p=2537762&postcount=318](http://ubuntuforums.org/showpost.php?p=2537762&postcount=318)


So now when I tried to print something, it popped up the printer icon and printer says "receiving data", but still won't print for some reason.

The printer is set to "local", however I noticed there is no info in the "Paper" tab or "Advanced" tab in the Printing properties box.  There is also nothing listed in the "Resolution" line.

---

### Post by Killtown on 2007-05-30
Still requesting help with this.

---

### Post by lazyart on 2007-05-30
I have a Brother 7820N and I was totally impressed at Brother's Linux support.

The instructions and links to the drivers are all [here]("http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install.html").

For scanning, get the br2scan driver and instructions [here]("http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html").  You can even set up the scan key if you want-- look for the scan key tool as well.

---

### Post by Killtown on 2007-05-30
> **lazyart said:**
> I have a Brother 7820N and I was totally impressed at Brother's Linux support.

The instructions and links to the drivers are all [here]("http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install.html").

For scanning, get the br2scan driver and instructions [here]("http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html").  You can even set up the scan key if you want-- look for the scan key tool as well.
I downloaded it before, but maybe i didn't do it correctly.

The instructions say:

> Make a temporary directory on your HDD and download both the LPR driver and cupswrapper driver to that directory.

I'm such a NOOB, where/how do I make a temp directory?

---

### Post by lazyart on 2007-05-30
Eh, just right click on your desktop and make a new folder there.  Just know that you can delete it once everything is set up.

---

### Post by Killtown on 2007-05-30
> **lazyart said:**
> Eh, just right click on your desktop and make a new folder there.  Just know that you can delete it once everything is set up.
And they just couldn't say make a temporary folder?!

On to part 3:

> 3. Install the LPR driver.

(i.e)
For Debian Users:
dpkg -i --force-all mfc210clpr-1.0.0-1.i386.deb

What's the terminal command, "sudo dpkg -i --force-all mfc210clpr-1.0.0-1.i386.deb"?

---

### Post by lazyart on 2007-05-30
mfc210clpr-1.0.0-1.i386.deb is the driver file
dpkg is the package installer.  Type```
dpkg --help
``` to sort out all the switches.

---

### Post by Killtown on 2007-05-31
So I had to wait until my linux guru buddy was available to walk me through it and finally got my printer and scanner working.  

Those instructions were *not* NOOB friendly.

---

### Post by lazyart on 2007-05-31
Agreed, they are involved but they do work.

---

### Post by Killtown on 2007-06-27
Working instructions for setting up the Brother MFC-120C printer on Ubuntu 7.04 Feisty Fawn:


1.  Follow the original instructions [here]("http://ubuntuforums.org/showpost.php?p=587083&postcount=1").

2.  If you run into the problem I did in the [above post]("http://ubuntuforums.org/showpost.php?p=2744361&postcount=3"), download the following script (originally found [here]("http://ubuntuforums.org/showpost.php?p=2277190&postcount=283")) to your desktop: 
[URL="http://ubuntuforums.org/attachment.php?attachmentid=30031&d=1176933547"]
Feisty_Brother_MFC-210C_Installer.sh[/URL] (click link and then select "Save to Disk")


(Original directions to the following below are found [here]("http://ubuntuforums.org/showpost.php?p=2537762&postcount=318"), but there was one mistake.)

3. **Important:** right-click mouse on the file you just downloaded to your Desktop, go to "Properties", then "Permissions", then **check the** "Execute" box.

4. Open your Terminal and change your directory to Desktop (make sure you capitalize "D"):

```
cd Desktop
```

5. Then paste **this code** into Terminal and enter, then your password and hit enter:

```
sudo ./Feisty_Brother_MFC-210C_Installer.sh
```

A small window should pop up:  *Brother MFC-120C Beta Installer*

6. **Only check** the "Printer Driver" box (or it may not work), hit "OK" and it will do the rest for you.

Your printer should now show all the configure options in your MFC120C icon in your *Printers* box in System/Administration/Printing and should now be able to print.


(Instructions also found [here]("http://ubuntuforums.org/showpost.php?p=2925114&postcount=356").)

---

### Post by snares on 2007-07-28
I have used this script dozens of times and it works everytime! Great script. I only found one problem...

For some reason in order for the printer to work properly I need to remove the printer that is set-up and re-set-up the printer. Not sure why...but the script does install the drivers properly 100% of the time. Just setting-up the printer doesn't work. Just something you might want to look into.

---

