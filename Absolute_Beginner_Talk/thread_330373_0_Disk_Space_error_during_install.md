---
title: "0 Disk Space error during install"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by indemnity on 2007-01-03
I am trying to install a scientific program from a CD and have been having problems. 

When I tried to ./ the program from the /CDROM it gave me a Permission Denied error, even when I logged in as root.  I had to copy the CD to the hard disk and 'chmod +x' the files.  Now the installer loads with ./ from the hard disk but I get more errors.  

The first is below; it appears in the terminal 
> Starting the VnmrJ installation program...
Warning: Cannot convert string "-b&h-luxi sans-medium-r-normal--*-140-*-*-p-*-iso8859-1" to type FontStruct

Then the separate installer launches and looks fine.  There are options to select various modules and at the bottom is a box for entering text with the home directory name, '/home/vnmrj' and a button to install.  When I click the button, the following error appears.

> Not enough disk space, 0 Bytes available from the selected partition.

When I quit from the installer, the following text appears in the terminal

> java.io.IOException: java.io.IOException: /home/nmr1/vnmrj/code/kill_insvnmr: cannot execute

I don't have any problems installing other programs and there is approximately 22 GB of memory spare for this 223 MB program.  I am new to Linux and also don't understand the error messages yet.   Any help would be appreciated.

---

### Post by aberry5555 on 2007-01-03
try doing everything you have done so far but with "sudo" before it. this runs it as root, though from the sounds of some of the errors I don't know if it will help. Good luck!

---

### Post by indemnity on 2007-01-03
I still get Permission Denied errors with sudo when trying to install from the CD, but it is okay from the files I copied to the hard disk and ran with 'chmod +x'.

---

### Post by aberry5555 on 2007-01-04
I think the reason why is that the installation uses it's local folder to compile etc. That means that if it was on the CD It had no-where to organise itself before it installed to the point you specify. In this way linux installs slightly differ from windows installs, as they have to (in some cases) modify the source in order to run properly, rather than simply copying and pasting an executable file. There are some Installations that will run off of a cd in linux but presumably that program was one that was burnt to a cd, rather than designed to install off of one.

---

### Post by s56vpe on 2007-06-04
So did you manage to run vnmrj on ubuntu (or something else than radhat)?

---

