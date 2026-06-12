---
title: "Canon PIXMA MP210..How to make it work?"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by needspeed on 2007-09-22
Hi all,
I have just purchased a Canon PIXMA MP210. I run virtualbox to make windows stuff work and hence the MP210, but has anyone attempted to make the MP210 print in Feisty?? Can you let me know of anything that might work.
Thanks
:confused:

---

### Post by Amazona aestiva on 2007-09-22
I have got a MP160.

It works with Feisty. (printing)
But scanning is difficult a bit:
We need a driver/software called ScanGear to scan. I've found a Redhat package for my MP160, and alien has created a debian package from it. Now it works well.

The bad new:
Canon haven't created a linux version of ScanGear for MP210. (yet)

However there might be a solution.

And you might try another version of Scangear. Perhaps mine... Maybe it'll work.
Do you want a how-to about it?

---

### Post by cotcot on 2007-09-22
This printer is not supported neither by gutenprint nor by Canon. 
The printer is obviously a new model. Keep an eye on gutenprint, turboprint for linux (payable +- 25 euro for a driver) and the Canon website. I guess some of them will show up with a driver coming year. 
Have a look to Vuescan for the scanner part.

Selling your Canon and buying an Epson or HP is an alternative to think about.

---

### Post by needspeed on 2007-09-22
Amazona, I am pretty new to linux/ubuntu, So any how to's are welcomed. Ubuntu actually discovers it as a MP210 but no driver options. A little quirky. What printer option do you suggest? Ill try getting scangear in the meantime.
Thanks:)

---

### Post by Amazona aestiva on 2007-09-22
Setup:
1. Connect and turn on the printer.

2. ```
sudo gnome-cups-add
```

3. First picture:
There You can see my printer is detected. Select yours and Next.

4. Second picture:
Now there is the configuration that I use. There are many of them. One must be right for You too. First try mine. After setup finished You can print a test-page to see it's all right.

5. Last stage:
Fill those if You want.

6. Type:
```
gnome-cups-manager
```
Third picture should appear.
There right click on your printer and choose properties.
There is the test page button. (Forth picture)

I hope I could help!;)

---

### Post by Amazona aestiva on 2007-09-22
[COLOR="Red"]Note: This scanner driver isn't for MP210, but it might work.[/COLOR]
So:
1. Go [here]("http://www.canon.com.au/support/wsss.aspx?id=mp160&m=DR&r=http://www.canon.com.au/products/all_in_one_printers/all_in_one_printers/mp160.aspx?m=support&h=http://www.canon.com.au/products/all_in_one_printers/all_in_one_printers/mp160.aspx?m=support"), choose "MP160 Scanner Driver Ver. 1.00 (Linux)" and download the 2 ones which I indicated on the attached picture.
[COLOR="Red"]Save[/COLOR] the files to Your desktop.

2. From now We need terminal.
```
cd Desktop
```
```
sudo apt-get install alien libpng3
```
```
sudo alien scangearmp-common-1.00-1.i386.rpm
```
```
sudo alien scangearmp-mp160-1.00-1.i386.rpm
```
```
sudo dpkg -i scangearmp-common_1.00-2_i386.deb scangearmp-mp160_1.00-2_i386.deb
```

3. To run ScanGear:
```
scangearmp
```

If nothing works uninstall them:
```
sudo apt-get remove scangearmp-common scangearmp-mp160
```

Is it working?????? I hope it is!;)

---

### Post by needspeed on 2007-09-22
Amazona,
THANKS for the effort, but to no avail. Printer still no go and scanner... cannot find device.
I can only guess canon might release their drivers for MP210, until then ill just virtual box it instead.
Thanks Again:confused:

---

### Post by Amazona aestiva on 2007-09-23
Yeah You have to wait I think... sorry.

---

### Post by 944jon on 2007-11-19
I got my MP210 to work just now. I used this guide [URL="http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP160_descargar_drivers"]
http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP160_descargar_drivers[/URL]
at openprinting.org for the MP160.
I haven't tried testing the scanning yet but printing works fine.
The driver can be downloaded from Canon Asia ([http://www.canon-asia.com](http://www.canon-asia.com)). Printing and scanning are working.
All of the steps worked fine for me except 7a. Doing [sudo apt-get install libgtk-1.2] it could not find this package. I googled and downloaded the deb package. Then installed it using this command 
[sudo dpkg -i libgtk1.2_1.2.10-18_i386.deb]

I'm running 7.04 ubuntu
gutenprint 5.0.0 installed by synaptic(didn't need to use 5.0.1)

Hope this helps someone. It took me a while to get printing. I'll work on the scanning another time.

---

### Post by dioporco on 2007-12-25
excuse me, I am using ubuntu 7.10 server edition with KDE installed. I have this printer (Pixma MP210) and I would like to know if there is an howto like this for K desktop. Thanks

I already have Gnome on my notebook running feisty and I would like to know also how to make this printer shared between computers. 
Thank you

---

### Post by quickstep on 2007-12-26
There are drivers for the MP210 (and MP220 and other new models) on the Canon Australia web site [http://www.canon.com.au/drivers/default.aspx](http://www.canon.com.au/drivers/default.aspx).

Use the drop downs to get to the driver download thus (ignore the search box it isn't useful):
 1. "All-In-One Printers" -> 2. "All-In-One Printers" -> 3. "PIXMA MP210 - Everyday" (or whatever your model)

Similar to the earlier post: Download the Linux **.deb** packages for the printer AND scanner drivers, as well as the "common" package for each.  I recommend downloading and reading the "guides" as well (since I may have missed a pre-requisite step here and can't be bothered reading it again).

For the MP210 the installs were:
```
sudo dpkg -i cnijfilter-common_2.80-1_i386.deb cnijfilter-mp210series_2.80-1_i386.deb
sudo dpkg -i scangearmp-common_1.10-1_i386.deb scangearmp-mp210series_1.10-1_i386.deb

```
I did this but didn't have the printer turned on - rebooted then turned the printer on and it auto-detected immediately and I was able to print straight away.

Scanning worked straight away too - but only through the GIMP as per the instructions in the guide. Sane/xsane doesn't support the MP210 (yet?).

---

### Post by dioporco on 2007-12-26
thank you! :KS

---

### Post by vervelover on 2007-12-27
Still no linux drivers for the mp220. Do you think the ones for the mp210 should also work with the 220?

---

### Post by orangebug73 on 2007-12-27
Thank you quickstep :)
But due to its advanced copy funktions I'm thinking about giving my mp210 (still packaged :-k ) back and buying a mp220 instead. Therefore I'm also interested in if the mp220 works with the drivers of the mp210. Or will Canon publish linux drivers for the 220 as well??

---

### Post by dioporco on 2008-01-04
the instruction show MP210 and MP220 also. I think drivers will be the same.
If I'm correct, windows and mac drivers with the cd supplied works for both printers. give a try

---

### Post by vanden12 on 2008-01-06
Umm I cant seem to find the dirvers for this....


I checked the link above but all they got is vista xp and osx..Nothing out linux...


Also I tryed sudo dpkg -i cnijfilter-common_2.80-1_i386.deb cnijfilter-mp210series_2.80-1_i386.deb

And got this

vanden@vanden-laptop:~$ sudo dpkg -i cnijfilter-common_2.80-1_i386.deb cnijfilter-mp210series_2.80-1_i386.deb
dpkg: error processing cnijfilter-common_2.80-1_i386.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing cnijfilter-mp210series_2.80-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 cnijfilter-common_2.80-1_i386.deb
 cnijfilter-mp210series_2.80-1_i386.deb

---

### Post by quickstep on 2008-01-08
This link should be easier: To get the MP210 printer and scanner drivers go here [http://www.canon.com.au/products/all_in_one_printers/all_in_one_printers/mp210_support.aspx](http://www.canon.com.au/products/all_in_one_printers/all_in_one_printers/mp210_support.aspx) then click on the "Driver Downloads".  Then the rest as per my previous post.

If you tried the commands in my previous post and got the message **"No such file or directory"** then either you had not downloaded the files, or you did not run the commands in the directory to which you had downloaded the files.

My apologies there aren't Linux drivers for the MP220.  Maybe someone could see if the MP220 works with the MP210 drivers and post the answer back here.

---

### Post by iTripped on 2008-01-31
I followed your steps and everything went well - right up to the point where I got errors on installing due to the fact that I have the 64 bit version of ubuntu. You don't happen to know if a) there are drivers compiled for my OS or b) there is some way to install these i386 drivers and make them work?

I know it's a long shot, but would appreciate any help.

Thanks,

iT

---

### Post by quickstep on 2008-02-01
Sorry, thats beyond me.  Maybe you could post a more general question "how to run/convert i86 code for 64 bit OS" elsewhere on these forums...

---

### Post by plafuro on 2008-02-21
Hi,

Not really a solution, but might be a feasible workaround for you.

The last VirtualBox version (1.5.6) runs fine all scanner tools under a XP guest OS. I'm using it this way at the moment. The only problem i found is that trying to use the whole scanner surface will return an error, but scanning up to 80% of the scanner area works.

Good luck, and if you have any news please share :)

---

### Post by arxaggelos on 2008-02-28
wonderful thread indeed, I finally got the 210 to work (huge canon fan, would be really disappointed if I didn't)
just one thing; I can't get it to print both sides of a page (you do this manually with a 210 after configuring the Print Options).  The tab "Duplex" in the OpenOffice Word is in grey, isn't selectable at all. 

any suggestions pls?

---

### Post by ellalan on 2008-03-05
Hi arxaggelos
Could you please tell me how you managed to make MP210 work in your system.
I have managed to download the printer driver and scangear(common &MP210), it will be nice if you could help me,BTW I am using Gutsy7.10. Thank you.

---

### Post by ellalan on 2008-03-06
I have downloaded the drivers and scangearmp from canon site, when I install them using Synaptic Package Manager my printer is not recognised.
I would like to install them using Terminal but I do not know the commands, could someone help me how to install the drivers using Terminal please. Thank you.

---

### Post by ellalan on 2008-03-08
Hi
I have found a solution for MP210 printer and got my printer working, I got the printer drivers from Canon-Aus and scan drivers from Canon-europe. I downloaded drivers ending with .deb 2 for printer, 2for scanner to the desktop.
Then I installed them using synaptic package manager. Then I went to the Synaptic Package Manager and installed "gnome-cups-manager". Thats all I had to do.
I am very happy that I joined this forum because I found a lot of useful information here, I would like to Thank all you guys for making such a wonderful contribution.
Happiness eezz Ubuntu.

---

### Post by 512mattw on 2008-03-27
thanks 
this worked perfectly
i can now print

Matt

---

### Post by yeats on 2008-04-13
Hello,

I'm at a breaking point with this and could use some help, please.  I was just given a brand-new, very nice Canon Pixma MP210 All in one.  After trying to install it myself and having no success, I came across this thread - thank you to all of you who have posted here.  Following advice here, I went to the Canon Australia web site ([http://www.canon.com.au/products/all_in_one_printers/all_in_one_printers/mp210_support.aspx](http://www.canon.com.au/products/all_in_one_printers/all_in_one_printers/mp210_support.aspx)) and found the deb packages for printing and scanning functions.  I downloaded them with Firefox and opened them with the gdebi package installer.  They seemed to work successfully, but when I turned the printer on to have Ubuntu recognize it, the drivers were not automatically applied, and I could not find them anywhere using the System > Administration > Printing tool.  

I then deleted the printer from the list (to allow the "auto-recognition" feature to work again), and following advice I was reading, I rebooted, turned on the printer and hoped the drivers would be recognized - they weren't.  In order to attempt what ellalan had done, I then UNinstalled the drivers to re-download them to the desktop to use Synaptic instead of gdebi.  I then could not open the downloaded packages from inside Synaptic, and deleted THOSE downloaded packages.  Then, when I attempted to re-download these packages using gdebi, I got an error message on the scanner driver that said "Error:  Dependency is not satisfiable: scangearmp-common."

I've tried everything I know how to do, but I'm in over my head here!  Could someone kindly walk me through:

1) How to correct the "Dependency is not satisfiable" problem?

2) How to connect the printer with the drivers?


Also, does anyone know a good tutorial aimed at former windows users that explains how & why Linux download & install features are different than windows?

Any help would be appreciated!

Thanks,
Chris

Oh - I'm using Gutsy Gibbon.  Please let me know if I need to provide more info.

---

### Post by yeats on 2008-04-14
**UPDATE - I was able to reinstall both the printer and scanner drivers using gdebi.  I didn't do anything special - I just started up my computer this morning and they worked.

I'm still not able to apply what I've downloaded to the printer, however - and I'm trying hard!

From within the default printer manager (System > Administration > Printing) I am able to see the printer, but there is not any sort of "Have Disk" option (like Windows) that allows me to point to the downloaded drivers.  It only lets me browse a database that does not have my particular printer model listed.

---

### Post by arbeedee on 2008-04-15
I'm very new to Linux and will probably mess up just trying to post this - but here goes. I have a Canon MP220 all in one printer. I have downloaded the print drivers for the MP210 from Canon Australia as per previous posts - and the printer works when printing, for instance, from OpenOfiice.

Photo printing seems to be a problem however. I have tried Photoprint and GIMP (ie. Gutenprint) and in both cases it will not offer me the choice of printer model I need (OK I'm not going to get the MP220 up - but where's the MP210?)

Help?

---

### Post by themunkee on 2008-04-16
chrissharp123:

First go to:

[http://www.canon.com.au/products/all_in_one_printers/all_in_one_printers/mp210_support.aspx](http://www.canon.com.au/products/all_in_one_printers/all_in_one_printers/mp210_support.aspx)

Under the linux section you need to download four files:

* IJ Printer Driver Ver. 2.80 for Linux(debian Common package) - cnijfilter-common_2.80-1_i386.deb
* IJ Printer Driver Ver. 2.80 for Linux(debian Package for the MP210 series) - cnijfilter-mp210series_2.80-1_i386.deb
* ScanGear MP Ver. 1.10 for Linux(debian Common package) - scangearmp-common_1.10-1_i386.deb
* IJ Printer Driver Ver. 2.80 for Linux(debian Package for MP210series) - scangearmp-mp210series_1.10-1_i386.deb

Note that the last link is actually for the scangearmp-mp210series_1.10-1_i386.deb file - it's not a printer driver as they have labelled

Just load up the standard gnome file browser in and double click the following files in order:

* cnijfilter-common_2.80-1_i386
* cnijfilter-mp210series_2.80-1_i386.deb
* scangearmp-common_1.10-1_i386.deb
* scangearmp-mp210series_1.10-1_i386.deb

You'll be prompted for your password. You might need to restart your computer.

Let us know how you get on.

---

### Post by themunkee on 2008-04-16
arbeedee:

OK, first load up System > Administration > Printing.

I initially had two printers there - one which detected a printer on the port with the wrong driver, and another with the wrong port right driver. I deleted both and added a new printer.

The connection I used was 'Canon MP210 Series USB #1'.

I selected a printer from the database, having first installed the driver there was a 'Canon MP210 Ver 2.80' listed.

The printer now works fine. Under that same menu I can set paper type, margins etc. Unfortunately, I've not managed to work out how to change it when printing from most applications.

Gimp took a little bit more work...

Once I'd loaded an image I selected 'Print with Gutenprint'. I created a new printer and just selected the MP210 print queue. Presto!

One method of getting full settings when I print is to  use the following on the terminal:

cngpij -P MP210 image.jpg

where MP210 is the name of the printer I created. This way gives you pretty much everything - print quality, colour intensity, scaling, maintenance - nozzle cleaning etc.

---

### Post by yeats on 2008-04-16
Thank you.  I'll let you know how it goes!

:-)

---

### Post by yeats on 2008-04-16
themunkee:

Thanks again for your advice.  Printing is now working, but the scanner is still not recognized.  I actually started a [separate thread]("http://ubuntuforums.org/showthread.php?t=756736") and got some other options there for what to do.  I'll check on those.  In the meantime, if you have any ideas about why SANE isn't seeing the scanner, please let me know!

Thanks!

---

### Post by themunkee on 2008-04-17
chrissharp123:

Did you try the scanner from within Gimp? File>Acquire>Scangear MP...

It doesn't work with any Sane frontends because (i think) of the USB protcol used which isn't compatible with libsane. However, there have been some exchanges with them and Canon resulting in new updated drivers.

See:

[http://mp610.blogspot.com/2008/02/canon-mp210-and-mp520-join-party.html](http://mp610.blogspot.com/2008/02/canon-mp210-and-mp520-join-party.html)

---

### Post by yeats on 2008-04-17
You rock, dude:guitar:

The GIMP worked.  I'll take a look at the XSane blog too, but I think the GIMP is the solution!

Thanks so much!

Chris

---

### Post by KeSha on 2008-06-15
I had the problem at MP210 too. the printer was working, but the scanner doesn't. I found this way to solve the problem: I have just installed this two packages

scangearmp-common_1.10-1_i386.deb

scangearmp-mp210series_1.10-1_i386.deb

Link: [http://software.canon-europe.com/software/0028481.asp](http://software.canon-europe.com/software/0028481.asp)
 
after that the program "scangearmp" works fine on my computer. But I don't like it. I Like Image Scanner programs, such as "Xsane Image scanner", "kooka" and etc.but the new problem I have, is that neither of this programs can find the device. what to do to find the device in this programs?

---

### Post by vlam21 on 2008-07-10
> Printing to 'MP210_series' failed with error code: 1034
is the printer paused ?

I get that error when I try printing a test page using gnome-cups-manager. Printing with OpenOffice doesn't work either. It just says, "Error while printing" when I attempt to print with MP210_series.

In the properties for the printer, however, it says that the driver for the printer is "text-only". Perhaps my drivers didn't install correctly? I followed a method that worked for several.

Any ideas? Thank you!

---

### Post by Fatfool on 2008-07-11
> **vlam21 said:**
> I get that error when I try printing a test page using gnome-cups-manager. Printing with OpenOffice doesn't work either. It just says, "Error while printing" when I attempt to print with MP210_series.

In the properties for the printer, however, it says that the driver for the printer is "text-only". Perhaps my drivers didn't install correctly? I followed a method that worked for several.

Any ideas? Thank you!
you could try to use the MP180's CUPS driver instead. It works perfectly fine for my MP220. Everything is printed out as it should be but there are no advanced options.

---

### Post by Ohwii on 2008-07-13
Thanks

---

