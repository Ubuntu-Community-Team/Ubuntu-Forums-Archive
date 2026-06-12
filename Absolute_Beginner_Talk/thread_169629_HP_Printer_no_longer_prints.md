---
title: "HP Printer no longer prints"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by yager on 2006-05-03
Okay, my printer problem is back.  Last time, I re-installed Breezy from scratch to clear up this problem and I am refusing to do this again.  A little help please.

Problem:
The printer is an HP G85 multifunction printer.  I have successfully installed this from scratch during the initial install and printed test pages and from Open Office with no issues.  It works fine in Windows XP so there is not a hardware problem.  For some reason it stops working after the initial installation.  Not exactly sure how long it stays working as I dont normally print every day.

Symptoms:
Using HP-Toolbox, I was able to see that the printer is communicating with Ubuntu.  This is version 0.9.5.  Printing a test page does not work.  When I turned the printer off, Ubunt lost communication with the printer but when the printer was turned back on, HP-Toolbox could not see the printer anymore.

Using cups, I set up a PDF printer in addition to the HP printer and successfully created a PDF file.  I take this to mean that cups and the PDF printer work and therefore cups is functioning as a server.  I can not log in to cups because I can not find the user or password to enter so I can not check the details of the setup.  A little help and I will provide more info tomorrow.  Looking at the cups config files did not reveal any obvious flaws to me but I will be glad to post the contents of any file needed to solve the problem.

From System>Administration>Printing, I have added and deleted the printer at least 4 times.  The only change that has occurred is that during one of them, the printer was listed twice which I later found is because HPLIP and cups see the printer and provide 2 different names.  Any idea how to turn either or both off so I can sort out if it is a conflict?

A review of the forums seems to indicate that printing in general is an issue in Ubuntu.  Anyone know how to get a subforum set up under hardware for printing issues?

---

### Post by yager on 2006-05-03
If you talk to yourself long enough, you will eventually break down and answer.

The following thread worked perfectly.

[http://www.ubuntuforums.org/showthread.php?t=169099&highlight=hplip](http://www.ubuntuforums.org/showthread.php?t=169099&highlight=hplip)

The link to the HPLIP site was great.  It had a step by step set of instructions on exactly what to do and even had specific directions in several areas for Ubuntu.  Cut and paste into terminal almost all the way through.

---

### Post by yager on 2006-06-01
Continuing my conversation with myself.... I just tried to upgrade to Dapper and things went horribly wrong again so I had to reinstall from scratch.  Overall the reinstall went very well with no issues other than the perpetual printer problem.  I had to come back to this same fix again but there is an update.

Skipping all the discussion, here was the source of the fix for my Officeject G85.  [http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)

There was only a single error in the Ubuntu step 2 instructions.  The instructions were written for Badger and the packages listed are not all available.  Replacements are easily found.
Here is the bad line in the instructions in the setting up the Linux environment.
```
sudo apt-get install python2.4-dev python2.4-qt3 libcupsys2-dev libsnmp5-dev libjpeg62-dev lsb libtool  automake libusb-dev
```

To correct, find the latest package for each item in the list and the remainder of the directions are perfect, or:

```
sudo apt-get install python2.4-dev python2.4-qt3 libcupsys2-dev libsnmp9-dev libjpeg62-dev lsb libtool  automake1.9 libusb-dev
```

The only downside is that I am sure that I used to be able to fax with this driver, now my G85 is no longer capable according to the supported printer list.  Funny thing is less capable machines are capable and the same printer if I have the duplex option installed?.  No idea how I lost this feature but hopefully this will come back since my Winmodem card is useless.

---

### Post by 11hjpphty76lkjj on 2006-06-08
The HPLIP website docs are being updated and will be available soon with the correct dapper steps.

Sorry for the inconvenience.

Aaron

---

### Post by yager on 2006-06-10
That is great news.  While they were being updated, I thought I would at least let everyone know what I did to make it work.  Only a minor error and it was quickly sorted out.

---

### Post by fonsv on 2006-06-11
Hi,

I tried to do the same, but my compile stalled in the make part. It ended with:
d.cpp' || echo './'`io/hpiod/hpiod.cpp
hpiod.o:1: error: Cannot open input file
make[1]: *** [hpiod.o] Error 1
make[1]: Leaving directory `/download/hplip-0.9.11'
make: *** [install-recursive] Error 1

Any idea?

Greetz

---

### Post by yager on 2006-06-11
I am not an expert in this area.  Just in case an expert does not find your problem here, you may want to start a new thread to draw some professional attention to your issue.  I wish you Good luck in resolving your issue.

---

### Post by sundman on 2006-06-26
[QUOTE=kalosaurusrex]The HPLIP website docs are being updated and will be available soon with the correct dapper steps.[/QUOTE]

The updated instructions are very clear and works perfectly.

Now I have a working usb connected printer again with hplip 1.6.6. It stopped working when upgrading to Dapper.

---

### Post by 11hjpphty76lkjj on 2006-06-26
lol sorry not clear on your message.  Everything is working now? :)

A

---

### Post by eeried on 2007-03-02
Someone in our young and small LUG had the same problem. When I first installed Dapper on his computer I set up his HP G85 Printer in the standard way and so used the driver included in Dapper (hpjis 0.97). The printer worked fine for a very short time and then it didn't work anymore.

I read several message on the subject of G85 not printing, and I'd like to offer this piece of advice: Keep It Simple.

As has been said already this printer requires a new version of the driver.

Remove the printer in menu System > Administration > Print

Don't remove the HPLIP packages you may have in Synpatic (I did and that was totally needless and I wasted a lot of time). Just leave everything alone.

Just go to  [the HPLIP download page]("http://hplip.sourceforge.net/downloads.html"). I wouldn't bother about the manual install (I tried it unsuccessfully) -- Keep it Simple, and have faith in HPLIP good work.
Download self-extracting file, and follow the very simple instructions. Don't forget to run the command script as sudo ```
sudo sh hplip-1.7.2.run
``` .

Be patient because the script does several things for you. 
it downloads and installs all the required dependencies (the files Yager has notes down),it compiles the driver and finally sets up the printer

Just follow the very few instructions on the terminal: once you're asked to press <enter> or quit (you don't want to quit, of course) and at the end of a lot of activiity on the terminal a dialog box springs up, and then you realize the script is going to help you set up the printer as well.

The setup process is even simpler than the standard one through System > Admin > Print. Make sure you choose the right version of the driver but that's easy because the script highlights the new version (the bad option is the second  line ending up with "0.97", that's the old driver). So again, keep it simple: it is simpler to press the button "next" rather than make an effort and choose the wrong option.

Don't bother about the panel that allows you to type in  the location and description of the printer; that's only for perople who have several printers on a network.

At the end of the set up you see that the dialog box has the option "Make a Printtest" (or sth like that) checked. Leave it alone and press "Finish".  The printer should spurts out a nice print test page.

Now just try to print a page from Firefox and OOo, and it should work fine.
:guitar: 

BTW the G85 printer is very good and rock-solid. That one has been printing many thousands  pages over the many years it's been in use.

Someone in France wrote a book entitled  *As Simple as Ubuntu*. We tend to go the hard way, and make things complicated when the solution is simple because some nice people like the HPLIP team make it simple. When dealing with Linux we tend to act as if the system was complicated beacause that's the image of Linux. Many people won't shift to Linux because they think you need to feel at ease with Windows first -- a model of simplicity, is it not? :mad: -- before making the move -- such a misconception! --,  and then they feel too exhausted to move to Linux.

What's not very clear to me however is why Ubuntu Dapper doesn't keep its drivers updated. Too many drivers I suppose but for a LTS version it's a bit of a problem.

Anyway, many hearty thanks to the HPLIP team :guitar: 

The only remaining problem our LUG member has been having is scanning the way he used to on Windows but that's another kettle of fish.

---

### Post by 11hjpphty76lkjj on 2007-03-02
eeried:

If you don't mind, please tell me what problems you had with the manual install instructions.  It would be greatly appreciated. :)

Thanks!

---

### Post by eeried on 2007-03-02
I'm not sure I quite remember. I followed the instructions for Ubuntu, step by step. I think everything went off all right until the setup dialog box popped up. Then the mouse cursor shifted to is  the "I'm busy, just wait" icon for a seemingly endless length time. So I simply gave up and installed the installer version on top.

The terminal output was about something like "bad device". However I got  a similar message with the script and yet the setup process worked like a charm.
Actually I get a similar message on another Dapper-run computer with another programm, eg Psi (IM):
 ```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```

Cheers,

---

### Post by 11hjpphty76lkjj on 2007-03-02
ah.  This is not a problem with HPLIP. It's a problem with xserver.

See:

[http://ubuntuforums.org/showthread.php?p=1264009](http://ubuntuforums.org/showthread.php?p=1264009)

---

