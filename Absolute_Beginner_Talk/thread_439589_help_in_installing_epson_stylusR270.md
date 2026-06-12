---
title: "help in installing epson stylusR270"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by like0537 on 2007-05-10
Hello!!!This is my first time to post a problem so if anybody want to help a people like please do so hehehehe....My problem is that i can't install the driver of Epson stylus R270 i have no idea on how to install it im a newbie in linux,so guys im begging of your help.....:lolflag:

---

### Post by benanzo on 2007-05-10
You have to install the PIPS-lite driver

Go to this site: [http://www.avasys.jp/english/linux_e/dl_ink.html](http://www.avasys.jp/english/linux_e/dl_ink.html)

Scroll down and toggle the button next to "Stylus Photo R260/R265/R270"
Then for Distribution select Debian
For Version select Others

Then answer the questionnaire at the bottom and select Next

Download the RPM package for CUPS  (pipslite-cups-1.0.0-1.i386.rpm)
(I know, it's stupid, you select Debian and they give you an RPM...)
Save it to your desktop.

You need to convert the RPM to a DEB so you can install it.
This will be done with a utility called alien

Open a terminal (Applications>Accessories>Terminal)

```
sudo apt-get install alien
```

```

cd $HOME/Desktop

```
```
sudo alien pipslite-cups-1.0.0-1.i386.rpm
```

This will create the .deb file on your desktop.  Double click it to install.

Now, in order to get this driver to find your printer on Ubuntu, you'll have to change a few things.

open /etc/ekpdrc

```
sudo gedit /etc/ekpdrc
```

Find the line
```
PrinterDevicePath = /dev/usb/lp0
```
and change it to 
```
PrinterDevicePath = /dev/usblp0
```

(make sure your printer is plugged in and turned on)
then restart ekpd
```
sudo /etc/init.d/ekpd restart
```
run /usr/local/EPAva/LITE/pipslite-install
```
sudo /usr/local/EPAva/LITE/pipslite-install
```

this will create a PPD file in /usr/share/cups/model

Open gnome-cups-manager (System>>Administration>>Printing and select New Printer and add "Photo Image Print System (EPSON Inkjet)"
as the new printer, *not* the USB printer it also lists.
Select Epson and scroll down until you see your printer (which should be
in the list now that the PPD is in the cups directory.)
If you don't see you printer select Install Driver and navigate to
/usr/share/cups/model and select the PPD file that we created earlier.
hit Apply and you're set. Right-click the new printer and select
Make Default. Go to properties and tinker if you want.
You should now be able to print.

---

### Post by like0537 on 2007-05-10
Thanks for the great help you've given me i will try it immidiately once i come to the office "currently her in the internet cafe..."God Bless You:)

---

### Post by benanzo on 2007-05-11
No problem, I toiled endlessly with my printer and it was a nightmare.  Feel free to post here again if it's not working right.

---

### Post by like0537 on 2007-05-11
hi now i'm install epson stylus r270 im having some difficulty in installing the driver there is an error and iit tells that can't create .ppd make sure your pc is on which is already on and detected allso...What could be the problem of it by the way im using ubuntu as my OS...Thanks and hoping for your fast reply

---

### Post by benanzo on 2007-05-11
Just to be sure that the device is created properly when you plug in the printer:

Be sure your printer is connected and powered on.
Open a terminal (Applications -> Accessories -> Terminal)
and put this:
```
ls /dev | grep usblp
```

If it comes back with this:
```
usblp0
```
then we'll move on and try something else.

If you don't get anything returned then try this:
```
ls /dev/usb | grep lp
```

You'll probably get:
```
ls: /dev/usb: No such file or directory
```

but if you get:
```
lp0
```
then go back and edit the /etc/ekpdrc file again.
```
sudo gedit /etc/ekpdrc
```

and change:
```
PrinterDevicePath = /dev/usblp0
```
back to:
```
PrinterDevicePath = /dev/usb/lp0
```

then restart ekpd:
```
sudo /etc/init.d/ekpd restart
```

then try the installer again:
```
sudo /usr/local/EPAva/LITE/pipslite-install
```

---

### Post by strabes on 2007-05-12
I have followed your guide up to this step: 

> run /usr/local/EPAva/LITE/pipslite-install
```
sudo /usr/local/EPAva/LITE/pipslite-install
```

When I run that, I get this: > alex@alex-laptop:~$ sudo /usr/local/EPKowa/LITE/pipslite-install
sudo: /usr/local/EPKowa/LITE/pipslite-install: command not found

This is really frustrating because every other printer that I've installed in linux has been practically plug and play.

Here's ls -a /usr/local: > alex@alex-laptop:~$ ls /usr/local/ -a
.  ..  bin  EPKowa  etc  games  include  lib  man  sbin  share  src

---

### Post by benanzo on 2007-05-12
Just to be sure you're running the command correctly:

It should install in a directory called EPAva under /usr/local, not EPKowa

```
sudo /usr/local/EPAva/LITE/pipslite-install
```

you can find it manually by doing:
```
sudo updatedb
```
then:
```
locate pipslite-install
```

---

### Post by strabes on 2007-05-12
I actually found another thread that fixed my problem without all that extra work. I simply went to localhost:631 in firefox and added it manually there. It was extremely easy and now my printer is working perfectly. I definitely showed this printer who's boss.

---

### Post by jerryhazard on 2007-07-29
Tons of great information on here, thanks to everybody that contributes - you're making my
introduction to Ubuntu all the less painful ;)

My issue, is the Epson R260, and the lack of reliable support for it - anywhere.  At least,
for me that is. (I'm on the latest Feisty Fawn...)

Tried Turboprint first.  That lasted about one print - as soon as I saw the horrendous watermark,
I moved on to searching...

I've tried to install the latest version of gutenprint that claims to have a ppd for the
260, however, when it was installed - none of the ppds updated, and there's no 260 ppd listed 
anywhere.  In fact, I don't see any new PPDs listed...

Tried to install through CUPS and localhost, nothing changed in there - no 260 ppd listed.

Also came across the avasys solution.  Was able to download the Epson rmp, convert it to a deb,
and install that.  Checked and edited the ekpdrc file, and tried to run the pipslite-install,
but when the window for it comes up that says "PPD file need to be created for the printer to 
CUPS - Please make sure that the printer is connected to your comptuer and turned on!" - the
only option enable it "Cancel".  The Continue button is greyed out.

I changed ekpdrc back to it's original path, and still got the same response (the computer does recognize the printer - both through CUPS and also if I just use System > Admin > Printing...

(Note: I read in a previous response about a command calling for an ekpd restart:

sudo /etc/init.d/ekpd restart

I dont have a file called "EKPD" in the init.d folder...?  this just reinforces the fact that I've
screwed something up ;))

One would think (*as uneducated about linux as I am*) that you could download just the PPD file
for the Epson 260 from somewhere, rather than having a script generate it.  Why can't one just
download one that can be placed in to the PPD folder along with all the other drivers?

Anybody willing to share?  :D

I'm sure that, by now, I've pressed so many buttons and typed so many commands that I probably 
don't understand - I've probably ruined the chance of ever getting this printer running. 

Just wondering if anybody knows what I'm missing - or if there's a source yet where you can 
download the actuall PPD FILE that is required?  

Thanks again for the information so far, 
Peace,
Jerry

---

### Post by yekibud on 2007-08-10
I was in the same boat as you, Jerry.  Then I ran the shell script in the same directory as pipslite-install.  I think something may have happened in the rpm->deb package conversion, and not everything was put in the right place.  In any case, after I ran the script, pipslite-install built my PPD for me.  Then I just had to restart cupsd and walk through the gnome printer wizard.  And, voila.

Now I'm just coming to terms with the expected: the photo quality of this printer is terrible.  (Note that I'm using the R260, however.)  In fact, I even prefer the red-dot/comicbook images produced by my 3-ink printer to the muted/shiny images produced by this so-called photo-printer.  I think if you want any real photo qualty printer, you probably need to hoc up the dough and get a laser or some other kind of hi-tech photo-ink printer.  You really get what you pay for for these cheapy photo-printers - so don't expect much.  (Thankfully, mine was free on a cannon rebate.)

---

### Post by jerryhazard on 2007-08-10
Thank you for the reply yekibud, I really appreciate it.

I ended up learning that Guetnprint 5.1.3 - released date June 17, 2007 includes a PPD for the Epson R260.  I uninstalled and undid all the mess I created, re-installed the latest gimp, and then installed Gutenprint.  Just for kicks, I rebooted my system.

When I opened an image in gimp, I clicked print, and about - just make sure the correct version of Gutenprint was present, and it was.  I was then able to locate the PPD for the Epson, and added it to my printers list.

Sorry to hear the quality you're getting from the 260 is less than optimal.  Mine prints better than I expected actually.  I've used the Epson 870 and 1270 in the past, and at work we have a wide format 10700 that does fine art quality work.  On the Epson Heavyweight matte paper, I am getting comperable, if not better results.  

I think the PPD that was generated for you maybe faulty?  *shrugs*  Give the latest Gutenprint a try maybe?

Thanks again for the response and take care,
Jerry

---

### Post by Maff88 on 2007-09-04
Hi I and trying to gte my R265 printer to work, its works fine until this bit.

> **benanzo said:**
> 
(make sure your printer is plugged in and turned on)
then restart ekpd
```
sudo /etc/init.d/ekpd restart
```
run /usr/local/EPAva/LITE/pipslite-install
```
sudo /usr/local/EPAva/LITE/pipslite-install
```


When i do the "retsrat ekpd" i get this message

"sudo: /etc/init.d/ekpd: command not found"

Can anyone help me with this?

Thanks,

---

