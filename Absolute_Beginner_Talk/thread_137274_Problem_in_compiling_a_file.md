---
title: "Problem in compiling a file"
date: 2006-02-27
forum: Absolute Beginner Talk
---

### Post by Soran on 2006-02-27
Hi all!

I've some problems with my ADSL modem: the CD my provider sent me predictably doesn't have a driver for Ubuntu. When I'm at home my only access to the net is by means of that modem, so now I really need to solve this problem.

On a web site I've found the driver for my modem compatible with Linux, but it has to be compiled and I don't know how to do that... Any advice?

Thanks all pals!

Live long and prosper! ^°_°^ :-D :-D :-D

---

### Post by darth_vector on 2006-02-27
first you need to install a compiler and assorted libraries, so run```
sudo apt-get install build-essential
```then look in the source directory of the driver. there should be a file called README. in all likelyhood it will tell you to run the following commands from inside that directory```
./configure
make
sudo make install
```but double check the README file for confirmation.

there may be dependencies that you need to install before you can compile the driver. this will be detailed in the README file also.

if you have any problems, post back and we will help you :-)

---

### Post by taurus on 2006-02-27
What kind of modem do you have because there may be a binary copy for Ubuntu (or Debian) that you just install on your machine...

---

### Post by Soran on 2006-03-01
[QUOTE=taurus]What kind of modem do you have because there may be a binary copy for Ubuntu (or Debian) that you just install on your machine...[/QUOTE]

Hi and thanks a lot for the help.

I'll try your advice. Btw, my modem is a "Fastrate USB 100" and it is the one provided by the Italian Internet provider Alice di Telecom Italia. If anybody knows if there is already something working for ubuntu, please, let me know!

Grazie to all of you!
Live long and prosper

---

### Post by daredevil on 2006-03-01
If u use an Ethernet modem then try to integrate ur username and password with the modem itself. that is wat i did

---

