---
title: "Installing scanner hp 4470c ?"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by 2CV67 on 2006-12-24
Hi community!

Having recently installed Edgy 6.10 in dual-boot with XP, I had hoped to be able to use my existing scanner - HP 4470c on USB.

SANE does not see it though, and searching threads I am getting that sinking feeling...

Am I right in assuming that all I can hope for is some gray-scale performance (maybe) if I manage to get through all the complex instructions on the following sites?
[http://www.sane-project.org/cgi-bin/driver.pl?manu=Hewlett-Packard&model=4470c&bus=any&v=&p=](http://www.sane-project.org/cgi-bin/driver.pl?manu=Hewlett-Packard&model=4470c&bus=any&v=&p=)
[http://www.sane-project.org/README.linux](http://www.sane-project.org/README.linux)
[http://hp44x0backend.sourceforge.net/](http://hp44x0backend.sourceforge.net/)
[http://hp44x0backend.sourceforge.net/README.html](http://hp44x0backend.sourceforge.net/README.html)

I really don't see myself tackling all that.

Please tell me I missed some other, better, simpler way...

...or is there at least a chance that it will be available as a Syn-Apt package sometime?

Thanks for any good news!

---

### Post by Sef on 2006-12-24
> SANE does not see it though

So you mean that you tried Applications > Graphics > Sane Image Scanner, and your printer could not be found?

---

### Post by YigalB on 2006-12-24
I am joining for the help request:
I have HP 4400C, same problem - I dont know how to tell Ubuntu to recognize it.
I was sure it will be detected the minute I plug the  USB cable.

Any idea?

Afterwards I am going to connect HP 970 printer. Will I face similiar problem?

Thanks
Yigal

---

### Post by 2CV67 on 2006-12-24
Reply to Sef:

Thanks for your interest!

Firstly, the scanner shows up OK in 'Device Manager' - see screenshot.

But, as you say, when I go Applications > Graphics > XSane Image Saver...
Then I get 'No device available' - screenshot

Then, under 'Help' I get a bunch of possibilities - screenshot
Several of which talk about missing backends...

One possibility is to try looking as root.
When I try to open Xsave as root, I get the sternest warning I have yet seen - screenshot.

Being the kind of guy who even obeys speed limits, I stop there (for the moment).

I would appreciate any enlightened comments please!

Thanks again :)

---

### Post by 2CV67 on 2006-12-28
Nobody?

Should I crash through the doom warning & try from root or is that as stupid as it sounds to a noobie?

Thanks guys!

---

### Post by 2CV67 on 2006-12-29
Still nobody? :( :(

---

### Post by 2CV67 on 2007-01-02
One last "bump" & then I give up....

---

### Post by Bloke on 2007-03-07
While Ubuntu is able to detect that the 4470c is attached via USB, SANE does not support the 4470c scanner at all. Have a look [HERE]("http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD")

The attached screenshot illustrates that the 4470c is skipped by SANE entirely.

---

### Post by fdbuck0 on 2008-01-09
Hi all,

i know this is an old thread, but Google pointed me to it anyway.
So I'd like to update the information here, also because I found an easy way to get my HP 4470c working (at least in grayscale mode at 300 DPI).

The HP 4470c support is included in the following package (installable via apt-get or aptitude) :
libsane-extras

I've installed it with the following command in the terminal :
```
sudo aptitude install libsane-extras
```

I hope this will help others when they find this thread...

Frederik.

---

### Post by bumanie on 2008-01-09
You should be able to geo the HP site and find a self installing package for the printer. In fesity fawn, I found the HP package worked very well, although it took a while to configure/download what it needed.
Go here [http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)
Download the Self-Extracting Archive With Installer
Then follow this
Note

After downloading make sure to put the hplip-2.7.12.run file in the directory you will want the hplip directory to be created. You may want this to be in your /home/username/ directory rather than your desktop.

Step 2: Run the automatic installer.
Open a terminal or command line window. Then run:

sh hplip-2.7.12.run

---

### Post by 2CV67 on 2008-01-09
Thanks for waking me up after a year dual-booting to XP for my scanning!

I did not try either of the suggestions yet (too busy updating from Feisty to Gutsy today...) but I see the HPLIP site says "HP Scanjet single-function scanners are not supported by HPLIP" & sure enough the Scanjet 4470c does not figure in the list of supported devices.

Presumable that eliminates that one?

 Thanks again

---

### Post by fdbuck0 on 2008-02-25
does this work for a scanner as well ?

---

