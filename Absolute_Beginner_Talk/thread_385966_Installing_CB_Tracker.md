---
title: "Installing CB Tracker"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by lwalper on 2007-03-16
I've found CheckBook Tracker (a Linux Quicken alternative) --- have unzipped it to a folder on my desktop. The folder has a file called cbtracker (with the typical executable file icon and the file properties tell me it's an executable file), but when I double click on it nothing happens. Is there another step in the process that I'm missing? Do i need to have the folder somewhere other than the desktop?

---

### Post by lwalper on 2007-03-22
I downloaded the file cbtracker-1.0-src.tar.gz

Unzipped the file to my desktop into the folder cbtracker with the following list of files resulting:
----------------------------------------------------------------

btncat.lrs
screenshots
unitdaterange.lrs
buttons.lrs
setup.lds
unitdaterange.pas
cbtpack
splash.lrs
unitenterdep.lfm
cbtracker
startsplash.lrs
unitenterdep.lrs
cbtracker.desktop
test.file
unitenterdep.pas
cbtracker.list
test.file.backup
unitfrmenterwithdrawal.lfm
cbtracker.lpi
TODO
unitfrmenterwithdrawal.lrs
cbtracker.lpi.tony
transpics.lrs
unitfrmenterwithdrawal.pas
cbtracker.lpr
unitabout.lfm
unitmain.lfm
constants.pas
unitabout.lrs
unitmain.lrs
graphics
unitabout.pas
unitmain.pas
header.lrs
unitbalancehist.lfm
unitsettings.lfm
help
unitbalancehist.lrs
unitsettings.lrs
icons.lrs
unitbalancehist.pas
unitsettings.pas
libofx.pp
unitbalance.lfm
unitsplash.lfm
license.txt
unitbalance.lrs
unitsplash.lrs
mainicon.lrs
unitbalance.pas
unitsplash.pas
mainlogo.lrs
unitcatreport.lfm
unitsplash.tony
menupics.lrs
unitcatreport.lrs
unitstarting.lfm
ofx.pas
unitcatreport.pas
unitstarting.lrs
printer.pas
unitconfirm.lfm
unitstarting.pas
printers.pas
unitconfirm.lrs
unitworking.lfm
README
unitconfirm.pas
unitworking.lrs
scales.lrs
unitdaterange.lfm
unitworking.pas

------------------------------------------------
I navigate to the new folder and type ./configure, but am told 'no such file or directory'

What's next?

---

### Post by maniacmusician on 2007-03-22
that response is normal if there's no configure script. 

Have you tried reading the README file?

Also, it would be helpful if you posted a link to where you're downloading this from so others can download this and see if it works for them and then help you out.

---

### Post by cowlip on 2007-03-22
could you also try running the file you're trying to open in a terminal, so we can see the output and any errors?

Just put a "./" in front of the program to execute it, you may have to run chmod +x on the file first, or set it to executable in gnome/kde "file properties" though

chmod +x cbtracker
./cbtracker

---

### Post by BLTicklemonster on 2007-03-22
> **maniacmusician said:**
> that response is normal if there's no configure script. 

Have you tried reading the README file?

Also, it would be helpful if you posted a link to where you're downloading this from so others can download this and see if it works for them and then help you out.

Perhaps the finest and most civil RTFM I have seen to date. 

Someone get M an award!

---

### Post by lwalper on 2007-03-22
I did actually read the README file -- it's a list of all the development issues and bug fixes. It does also say:

This is the ELF executable (that means, you run the program "cbtracker" from the command prompt or make an icon for it with the included icon file in your desktop environment.)

When I run cbtracker from within the cbtracker folder I receive the following error:

./cbtracker: error while loading shared libraries: libgdk_pixbuf.so.2: cannot open shared object file: No such file or directory.

I downloaded the file from:

[http://tony.maro.net/](http://tony.maro.net/)

---

### Post by cowlip on 2007-03-22
ok it looks like you need a package with the file "libgdk_pixbuf.so.2"

try "apt-file *libgdk_pixbuf*" in a terminal

some packages that look like might work:
sudo apt-get install libgdk-pixbuf-gnome2

---

### Post by lwalper on 2007-03-22
In a terminal I tried

apt-file *libgdk_pixbuf*
bash: apt-file: command not found

and . . .

sudo apt-get install libgdk_pixbuf-gnome2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libgdk_pixbuf-gnome2

as well as . . .

sudo apt-file *libgdk_pixbuf*
sudo: apt-file: command not found

Any other suggestions? They're certainly welcome.

---

### Post by cowlip on 2007-03-22
Instead of sudo apt-get install libgdk_pixbuf-gnome2

Can you try this instead? (no underscore).  It's in universe, so you have to enable that repository in Synaptic:

sudo apt-get install libgdk-pixbuf-gnome2


I wasn't treally sure on howo use apt-file but I guess you'd have to install it first.  Anyways it's OK since I just searched through Ubuntu's package repository: [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libgdk-pixbuf-gnome2&searchon=name&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libgdk-pixbuf-gnome2&searchon=name&subword=1&version=all&release=all)

---

### Post by lwalper on 2007-03-23
OK. That fixed it, thanks!!

---

### Post by maniacmusician on 2007-03-23
> **BLTicklemonster said:**
> Perhaps the finest and most civil RTFM I have seen to date. 

Someone get M an award!
:D

> **lwalper said:**
> OK. That fixed it, thanks!!
Just out of curiosity, how is that piece of software? Any good?

---

### Post by lwalper on 2007-03-23
Well, so far, so good. I've only made a few entries so far, but it seems to automatically increment check numbers, allows withdrawals with debit cards, and etc. and keeps a running tally of remaining balance. Haven't looked at the end-of-month reconciliation process yet, but it does have that feature. It will also allow download of bank OFX files (if your bank will allow it -- some will nowadays) so you can do reconciliation -- whenever you want instead of just the end of the month. Pretty handy!

I was just now reading the "Contents" (a basic 'how it works' file). The app seems to be fairly comprehensive for practically any home money management issue. It's probably all 99% of us need to be able to keep things straight.

I've been using QuickBooks, but it was really far more comprehensive than what I ever used. This looks like it will work great and do just what I need. I'll use it for a bit and see if it suits me, then try to figure out how to make a 'donation' to the author for all his work.

---

### Post by maniacmusician on 2007-03-23
wow, that's awesome! I hope you do donate some money, OSS developers are always hard for cash :). I'm sure he/she will appreciate it very much. Consider sending a nice e-mail as well, as that always helps to boost morale and perhaps encourage further development on a project.

---

