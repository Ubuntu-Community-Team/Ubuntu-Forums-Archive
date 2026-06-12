---
title: "printing problems"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by eilu on 2006-11-19
I'm finding Ubuntu's printing to be very inconsistent... some days I get exactly what I need, but some days I don't. Here's a run down of what I'm having problems with:
[LIST=1]
[*]quality- I can't seem to get it *just right* specially with images. The quality is always coming out too high or too low. (I have CUPS set to manual so I can change it with each print job)
[*] pdfs and gifs don't come out right- text documents are okay, but when I print a pdf CUPS just starts up and nothing happens. I tried printing a gif and the printer spat out a black page (yes, black as in the color; the whole page was covered in black even if the gif was much smaller)
[*]time- CUPS seems to take forever to load.
[/LIST]

My printer is an EPSON CX5300 all-in-one. All these hiccups make me miss Windows' EPSON driver (or is that Epson's windows driver? anyway...); currently the best way for me to get a decent printing is to reboot and use windows. :(

BTW: I can't reply everyday (but I will try), so just keep the suggestions rolling in

---

### Post by ron999 on 2006-11-19
Hi eilu

I use an old Epson 440. It didn't work very well using the Ubuntu supplied driver but now I use a gimp-print driver it's much better.
Perhaps you should try a gimp-print driver also.
I've looked in the gimp-print file and there is a driver for Epson Stylus CX5300.

To get these drivers do this:-

With Edgy Eft 6.10 it's simple, just install gimp-print using Synaptic.

With Dapper Drake 6.06 it's more difficult. I had to do this:-

Make sure that c compiler gcc is installed by Synaptic.
Download gutenprint-5.0.0.tar.bz from [http://sourceforge.net/projects/gimp-print](http://sourceforge.net/projects/gimp-print) onto Desktop.
Extract the tar to make folder gutenprint-5.0.0 on the Desktop.
At terminal type cd /home/<your-user-name>/Desktop/gutenprint-5.0.0
Then type 'make'
Then type 'make install'
This will compile and install the driver.

Then install the printer like this:-

System>Administration>Printing

Double-click on 'New Printer'.

Printer type: 'Local Printer' button.

'Use another printer by specifying a port' button.

Printer port: Parallel Port #1(EPSON).

FORWARD

Manufacturer: Epson

Model: Stylus CX5300

Driver: High Quality Image (Gutenprint) (en)

FORWARD then APPLY

Then CLOSE

I hope this cures all your printing problems.


8)

---

### Post by Coburn on 2006-11-19
I already have a gutenprint 5.0 driver installed on Dapper. From the repos.
Then again, my CX5000 is not working yet.

How do you figure, connecting to a parallel port, when my CX is USB?
It is detected, by the way.

So far all I have gotten it to do is go into a loop of spitting out blank pages.

Well, the night is young...

Update:

Got a test page to print by installing the gutenprint-en CX4800 driver instead of the CX5100.

---

### Post by Sef on 2006-11-19
Read [LinuxPrinting]("http://linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_CX5300").

---

### Post by Coburn on 2006-11-20
The thing that stood out to me from the LinuxPrinting page was using [http://localhost:631/admin](http://localhost:631/admin) to use the webadmin tool. It has a lot of features I need.

I can't add printers using that page, because for security, admin is disabled, and their directions for enabling it are incomplete--but I guess that is good.  Unless you know enough to figure that out, you probably shouldn't disable the security!

Adding it using Gnome worked fine, anyway.

---

### Post by eilu on 2006-11-21
well, I tried downloading, unpacking and compiling gimp-print and this is how far I got:
$ make
make: *** No targets specified and no makefile found.  Stop.
$ make install
make: *** No rule to make target `install'.  Stop.
:confused:

---

### Post by ron999 on 2006-11-21
Make sure that c compiler gcc is installed by Synaptic.

---

### Post by eilu on 2006-11-23
yes, gnu c compiler is installed- synaptic lists these as installed when I search for gcc:
[LIST]
[*]gcc v4:4.0.3-1 
[*]gcc-3.3-base v1:3.3.6-10
[*]gcc-4.0 and gcc-4.0-base (both are version 4.0.3-1ubuntu5)
[*]gcj-4.1.base v4.1.0-1ubuntu8
[/LIST]

---

### Post by ron999 on 2006-11-23
When you download the tar.bz file unzip it to give the folder gutenprint-5.0.0 on your desktop.
Then open the terminal and change directory to that folder by typing
cd/home/username/Desktop/gutenprint-5.0.0
(use your own username!)
Then type make
Then type make install

---

### Post by eilu on 2006-11-24
that's exactly what I did the last time. I tried it again, it still returns:
```
foo@bar:~/Desktop/gutenprint-5.0.0$ make 
make: *** No targets specified and no makefile found.  Stop.
```

---

### Post by eilu on 2006-11-26
okay, I've now maanged to install gutenprint by 
```
./configure
make clean
make
sudo make install
```
I hope this works...

---

### Post by Coburn on 2006-12-01
never mind... didn't see last post...

---

### Post by eilu on 2006-12-04
well, that seems to have solved the problem. Thanks everyone!

(on a somewhat-related note, I read somewhere there's a non-opensource Epson driver from Epson itself... might there be any difference if I try that one? Kinda miss all the (unessential but ooooh-shiny) bells and whistles my printer had on windows)

---

