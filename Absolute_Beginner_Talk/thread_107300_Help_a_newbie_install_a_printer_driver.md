---
title: "Help a newbie install a printer driver"
date: 2005-12-22
forum: Absolute Beginner Talk
---

### Post by Dr. E on 2005-12-22
I just got finished installing Ubuntu for the first time.  I've been able to transfer my Thunderbird and Foxfire settings.  The only difficulty I am having is installing the printer drivers.  Ubuntu correctly identified my Lexmark 125.  I found the PPD files for my printer on linuxprinters.org and installed them.  On linuxprinters.org it gives these special instructions for installing my printer, but it is for Red Hat users:


 Because the driver needs to read status codes from the printer, this driver requires special setup which will be shown here for Red Hat systems, on other distributions it should work in a similar way. For Queue type, select Locally-connected, click "Custom Device" and specify /dev/null as the device. If you don't specify /dev/null, nothing will happen when you print because the driver won't be able to connect directly to the printer since the resource will be in use. If your printer has locked up in the past, you may need to unplug it from the power outlet and plug it back in before this driver will work. If your printer is not connected to /dev/usb/lp0, you can specify a different device using the driver options.



Could someone please indicate how to achieve this in Ubuntu?

---

### Post by SickTwist on 2005-12-22
What is the exact model of the Lexmark? Just "125" or does it have a name?

---

### Post by Dr. E on 2005-12-23
[QUOTE=SickTwist]What is the exact model of the Lexmark? Just "125" or does it have a name?[/QUOTE]



Sorry, It's a Lexmark X125

---

### Post by bscbrit on 2005-12-23
you will probably find the correct driver for you printer here:

[http://support.lexmark.com/cgi-perl/selections.cgi?ccs=229:1:0:-1:0:0&target=http://downloads.lexmark.com/cgi-perl/downloads.cgi&&req=:::::](http://support.lexmark.com/cgi-perl/selections.cgi?ccs=229:1:0:-1:0:0&target=http://downloads.lexmark.com/cgi-perl/downloads.cgi&&req=:::::)

---

### Post by Dr. E on 2005-12-23
[QUOTE=bscbrit]you will probably find the correct driver for you printer here:

[http://support.lexmark.com/cgi-perl/selections.cgi?ccs=229:1:0:-1:0:0&target=http://downloads.lexmark.com/cgi-perl/downloads.cgi&&req=:::::](http://support.lexmark.com/cgi-perl/selections.cgi?ccs=229:1:0:-1:0:0&target=http://downloads.lexmark.com/cgi-perl/downloads.cgi&&req=:::::)[/QUOTE]

I have the driver, the problem is implementing the special instructions referred to in the previous post, which are given for Red Hat not for Ubuntu.

---

### Post by bscbrit on 2005-12-24
When you run the setup program - which I assume is in one of the two files that your printer needs downloaded from the link that I gave you - does it not ask for a Queue type?  I cannot answer this part of the problem because I haven't got the printer to install.
I have seen some of the installation for the Lexmark 4039 for example.  There are 2 files in the package downloaded from the website.  The printer PPD files and a 100MB installation file. Thats a BIG file but I haven't got a clue what is inside it because I haven't tried to install the 4039 on my computer. 
You need to download the PPD and installation program for your computer. It might run perfectly but, if not, that is when you can come to this forum and tell people what you expected to happen and what actually happened (quoting any error messages that appear etc) and someone here can tell you how to solve that particular problem.  Only somebody who has already installed the X125 can tell you exactly what you will see while installing it.
You might also get additional help if you start a thread on the Breezy hardware forum ([http://www.ubuntuforums.org/forumdisplay.php?f=98](http://www.ubuntuforums.org/forumdisplay.php?f=98)) specifying your printer type and precise problem in the thread title.  Someone with the necessary expertise with that printer can then provide the help required.
If the downloaded program is _not_ an installation program then you need to tell me exactly what it _is_, and what it suggests that you should do.
This is not meant to sound negative - in fact, quite the opposite - but most of the people who read this thread will not have a X125 and will know nothing about it.  The fact that it has a specific manufacturers driver is both a benefit (Hooray - a driver!) but also a hindrance because we will never have used that particular piece of software.  Please let me know what is in each file that you have downloaded and i'll do what I can.

---

### Post by SickTwist on 2005-12-24
There is a driver already included with Ubuntu for this printer. Have you tried it yet? If so, at what point does it not work? Does the printer respond after a test print? Do you get an error message?

In Ubuntu, many times you'll find that the driver you need is already installed (or it is in the repositories and can be installed very easily).

I have made a screenshot of the printer setup dialog that shows the Lexmark X125 driver:
[ATTACH]4806[/ATTACH]

---

### Post by Dr. E on 2005-12-24
[QUOTE=SickTwist]There is a driver already included with Ubuntu for this printer. Have you tried it yet? If so, at what point does it not work? Does the printer respond after a test print? Do you get an error message?

In Ubuntu, many times you'll find that the driver you need is already installed (or it is in the repositories and can be installed very easily).

I have made a screenshot of the printer setup dialog that shows the Lexmark X125 driver:
[ATTACH]4806[/ATTACH][/QUOTE]

Yes, I tried it from the setup dialog you showed.  The printer does not repsond when I ask it to do a test print.  I get no error message.  Then I went to
 
[http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-X125](http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-X125)

where I downloaded the PPD file.  In the dialog box cited above I installed this driver, then tried to print a test page--Nothing.

On [http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-X125](http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-X125) it gives these special instructions needed to get the printer to run:


 Because the driver needs to read status codes from the printer, this driver requires special setup which will be shown here for Red Hat systems, on other distributions it should work in a similar way. For Queue type, select Locally-connected, click "Custom Device" and specify /dev/null as the device. If you don't specify /dev/null, nothing will happen when you print because the driver won't be able to connect directly to the printer since the resource will be in use. If your printer has locked up in the past, you may need to unplug it from the power outlet and plug it back in before this driver will work. If your printer is not connected to /dev/usb/lp0, you can specify a different device using the driver options.

This is where I need the help.  These instructions are for RedHat and I don't see how to apply them in Ubuntu.

Thanks

---

### Post by Dr. E on 2005-12-24
[QUOTE=bscbrit]When you run the setup program - which I assume is in one of the two files that your printer needs downloaded from the link that I gave you - does it not ask for a Queue type?  I cannot answer this part of the problem because I haven't got the printer.[/QUOTE]

The link you gave me sends me to the main page, but not to anything specific about Lexmark X125 for Linux.  For this reason I couldn't find an installation program even by searching on that site.

---

### Post by Nightwind on 2005-12-24
Dr. E have you looked here: [http://www.ubuntuforums.org/forumdisplay.php?f=100](http://www.ubuntuforums.org/forumdisplay.php?f=100)
I found a good  bit of information there on my printer, I haven't checked to see if there was anything on your model. Hope this Helps.. Merry Christmas

---

### Post by bscbrit on 2005-12-24
Dr E, There is a page for your printer ([http://support.lexmark.com/cgi-perl/selections.cgi?ccs=229:1:0:0:0:0&target=http://downloads.lexmark.com/cgi-perl/downloads.cgi&&req=:::::](http://support.lexmark.com/cgi-perl/selections.cgi?ccs=229:1:0:0:0:0&target=http://downloads.lexmark.com/cgi-perl/downloads.cgi&&req=:::::)) but it does not seem to provide a linux driver.  But, if there is a driver already in Ubuntu, then I cannot imagine that it doesn't work for some people.  Its probably too late tonight to do much more (and I suspect that tomorrow will not be a good day to spend much time on the computer -but  I might be around for an hour or two....).  However, I am happy to continue to try and help you get your printer working.  Sorry that we haven't made much progress this week!

---

### Post by SickTwist on 2005-12-24
Dr E,
It sounds like a [bug report]("https://bugzilla.ubuntu.com/") should be created for the Lexmark X125 driver as it is included in Ubuntu and shoud just work. If you do not wish to do this let me know and I'll do it for you. I realize that this won't help in the meantime but hopefully the issue can be corrected for Dapper.

---

### Post by bscbrit on 2005-12-25
Dr E - yes, I've just crept away from the family gathering for a few quiet moments!  Did you install the driver that was supplied with Ubuntu rather than the one that you downloaded from RH?  The Ubuntu version should install itself taking into account any differences between ubuntu and RH.
If you have used the Ubuntu driver and it _still_ doesn't work then you might want to consider raising a bug report, as a previous poster suggested.
I am having problems understanding this quote "For Queue type, select Locally-connected, click "Custom Device" and specify /dev/null as the device. If you don't specify /dev/null, nothing will happen when you print because the driver won't be able to connect directly to the printer since the resource will be in use."  Where did you get it from?  Is it produced by an installation program when it runs?  The Ubuntu driver should not show you this message at all.

---

### Post by Dr. E on 2005-12-25
[QUOTE=bscbrit]
I am having problems understanding this quote "For Queue type, select Locally-connected, click "Custom Device" and specify /dev/null as the device. If you don't specify /dev/null, nothing will happen when you print because the driver won't be able to connect directly to the printer since the resource will be in use."  Where did you get it from?  Is it produced by an installation program when it runs?  The Ubuntu driver should not show you this message at all.[/QUOTE]

The Ubuntu driver didn't seem to work so I downloaded one from linuxprinting.org.  Those special instructions are from their website.

---

### Post by bscbrit on 2005-12-25
Can you post the output from 

lsmod

please?

---

### Post by Dr. E on 2005-12-25
I now have found some other drivers I'm willing to try.  They come as tar balls.  I have searched the forum on how to install drivers that come as tar balls.  Could you please give me a line by line instructions on how to install these drivers?  They are named x125-drv-0.2.3.tar.gz and x125-drv.2.2.3.tar.gz.

---

### Post by bscbrit on 2005-12-25
And what were the symptoms / error messages when you used the Ubuntu driver?

---

### Post by Dr. E on 2005-12-25
[QUOTE=bscbrit]And what were the symptoms / error messages when you used the Ubuntu driver?[/QUOTE]

No error messages.  The printer just didn't do anything.

---

### Post by bscbrit on 2005-12-25
Yes I can help you install the tar.gz's, but where are they from?  

If you are running gnome, just clicking on them should bring up a window that will allow you to unpack them to your home directory - I wouldn't go any further than that for the time being until we know what is inside each package.  When unpacked, can you provide a 'ls' of each one of them please?

---

### Post by bscbrit on 2005-12-25
Going back to your #18, did you try printing from the commad line i.e. terminal?  You  often get useful error messages from there which are eaten by the GUI.

---

### Post by Dr. E on 2005-12-25
[QUOTE=bscbrit]Yes I can help you install the tar.gz's, but where are they from?  

If you are running gnome, just clicking on them should bring up a window that will allow you to unpack them to your home directory - I wouldn't go any further than that for the time being until we know what is inside each package.  When unpacked, can you provide a 'ls' of each one of them please?[/QUOTE]


OK I clicked on the tar.gz and it made a folder called drv_x125 containing a number of files. The INSTALL file reads:

Installing the printer filter
=============================

cd src
make
su
make install

The easiest way to set up your printer is probably by using foomatic
([www.linuxprinting.org)](www.linuxprinting.org)).

1. Go into your printer configuration, and select the Lexmark X125 
   printer and drv_x125 driver.
2. For the queue, specify /dev/null instead of /dev/usb/lp0.
3. If your printer is not at /dev/usb/lp0, don't do a test page yet.
   Instead, go to the driver options tab and specify the port for
   your printer.  Then print a test page.

Note: If your printer has locked up before or is not working, please try
unplugging it from the power outlet and plugging it back in before trying
this driver.

If it's not working, don't hestitate to ask any questions in the
Open Discussion forum on [http://sourceforge.net/projects/x125-linux/](http://sourceforge.net/projects/x125-linux/)


So I copied the commands into the terminal and got:

dre@ubuntu:~$ cd src
bash: cd: src: No such file or directory
dre@ubuntu:~$ make
make: *** No targets specified and no makefile found.  Stop.
dre@ubuntu:~$ su
Password:

---

### Post by bscbrit on 2005-12-25
You can find the foomatic program in the repos - it is certainly listed in my synaptic.  

When it says change to the 'src' directory I think it is meaning the directory into which you have unpacked the tar.gz.  You can run 'make' as a normal user, but you will have to run 'make install' as root.

e.g.

make
sudo make install

When running the foomatic program - which I have never done - I expect it will ask you for the queue and the other information that you have quoted from the RH page.   You should run foomatic, I presume, after you have built the program above.

Good Luck

---

### Post by bscbrit on 2005-12-25
I have gone through the installation of Ubuntu's X125 driver.  There are 3 possible options for the #1 parallel port, Canon, Epson and standard.  Did you, at some time, try all three?

EDIT:  I would strongly recommend that you give this installation a second try.  It has worked for many other users so I suspect that whatever is different with your installation is fairly trivial.

---

### Post by prizrak on 2005-12-28
Have you tried following [this]("http://www.ubuntuforums.org/showthread.php?t=49714&highlight=lexmark") How-To? It helped me install a z25, its' even shared over the network now ^_^ Substitute the driver for the one you need (they can all be found on Lexmark site) and lemme know what develops

---

### Post by quincunx on 2005-12-29
[QUOTE=Dr. E]I just got finished installing Ubuntu for the first time.  I've been able to transfer my Thunderbird and Foxfire settings.  The only difficulty I am having is installing the printer drivers.  Ubuntu correctly identified my Lexmark 125.
<snip>
Could someone please indicate how to achieve this in Ubuntu?[/QUOTE]


Sounds just like the problem I had.  I just started using Linux again and started with a Fedora distro.  Installing the printer was simple and it worked right away.  I've been using Ubuntu for a few days now, and decided to print something tonight, but after setting up the printer, the test page just left a print job in the queue as "Printing", but it never would.  My printer/driver was recognized by Ubuntu, but there were no results until...

Finally I found [this post]("http://www.ubuntuforums.org/showpost.php?p=608171&postcount=2") that gave me the steps to get my printer working again.  I hope this works for you too!

---

### Post by tagra123 on 2006-04-30
I also posted this on LinuxPrinting.org

How To Install Lexmark X125 on UBUNTU:

There may be a better way but my printer is now printing. See notes at end of this post. I found this to work by trial and error.

Download the X125-drv-0.2.3.tar.gz driver from: [http://sourceforge.net/projects/x125-linux/](http://sourceforge.net/projects/x125-linux/)

Select save to Deskop.

INSTALLING THE DRIVER

*****
Open your terminal using the menu (Applications-Accessories-Terminal)
*****

Type in the following commands:

cd Desktop
mkdir prndriver
cd prndriver
mv ./x125-drv-0.2.3.tar.gz ./prndriver/x125-drv-0.2.3.tar.gz

cd prndriver
tar -xvzf x125-drv-0.2.3.tar.gz

cd src
make (ignore warnings you may see here)
sudo make install

*****
close the terminal
*****

*******
Open your Printers by using the menu (System-Printing)

Click on New Printer

STEP 1
Even though this is a local printer we will set it up as a network printer using LPD by entering the information below.

Choose Network Printer
Select UNIX Printer (LPD)

HOST: localhost
Queue Type: /dev/null

Click on the Forward button.

STEP 2
Specify your printer by using the information below.
Select Lexmark as the manufacturer
Select X125 as the model
Select drv_x125(recommended) as the driver

Click on the Apply button

The printers window should now have the x125 listed as your printer.

Right click on the printer and select properties.
Click on the Advanced tab.

Make sure your device is /dev/usb/lp0

Click on Print Test Page and the printer should print.


NOTES:

BUG?
I've noticed that once the document is printed I have to cancel the job manually in the "X125" window.

To open that window form the menu (System-Printers) then double-click on the X125 printer.

To Cancel a completed print job that is still displaying as printing:
Right-click on the print job and choose cancel.

If anyone knows how to get this to remove a completed job automatically please post

Output:

The output is not perfect but I'm going to check the settings and see if a newer driver is ready.


I hope this helps anyone having trouble getting this printer to print. Post a message I'll check back at least once a week.



Tom Again.  

Here's a followup to my previous HOW TO INSTALL X125 On UBUNTU:

It now prints without having to manually cancel each print job.

Since the last posting KDE Desktop KUBUNTU is installed along with Gnome on my UBUNTU setup. I'm not sure if this installed any additional drivers, so I'm mentioning it.

Next

From a terminal type in:

First make a backup:
sudo cp /etc/cups/printers.conf /etc/cups/printers.conf.bak4x125

Next open the file to edit:
sudo gedit /etc/cups/printers.conf
 
If you've followed the steps above you should have an X125 section. 

Delete the X123 section and replace it with the following.
 
<DefaultPrinter X125> 
Info X125 
Location usb://Lexmark/X125 
DeviceURI file:///dev/null 
State Idle 
Accepting Yes 
JobSheets none none 
QuotaPeriod 0 
PageLimit 0 
KLimit 0 
</Printer> 


Save the file.



Reboot.

It works on UBUNTU and KUBUNTU.


Hope it helps. Tom -- tagra

---

