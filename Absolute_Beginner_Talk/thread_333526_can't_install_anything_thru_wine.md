---
title: "can't install anything thru wine"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2007-01-07
i downloaded the wine version for edgy
sudo apt-get install wine

i tried to install dvd decryptor and dvdshrink thru wine and it complains it either can't find c/windows or the other app complains it can't write to c://windows/temp

---

### Post by kepos on 2007-01-07
Are you shure that this programs can be used with wine?
after installing wine, also install aditional installs with winetools. 'winetools' can't be found in repository. You'll have to download .deb package from internet (try with google. i found it there). winetools will install some more things which will make wine more efficient (like fonts, MFC runtime, VBruntime, msdao and many more)

---

### Post by nickburns on 2007-01-07
what command are you using to install? is the install off of a cd?

sometimes I have to copy what I am installing to /home/nickburns/.wine/c_drive/
in order to get it to work.

---

### Post by ajmorris on 2007-01-07
To install those two particular applications, wine must be configured to emulate Windows XP (or I assume Windows 2003, i have only tried with XP) To do this, in a command line type: [PHP]winecfg[/PHP]

Then on the one of the tabs (can't remember which one, but it is easy to find) there is a drop down menu which chooses which operating system.

---

### Post by lime4x4 on 2007-01-07
john@john-edgy:~$ winecfg
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
john@john-edgy:~$

---

### Post by ajmorris on 2007-01-07
i suggest re-installing wine.

---

### Post by Barney on 2007-01-09
Same as with John above (but in Dapper); and I have re-installed Wine.

Suggestions??

---

### Post by Swankyman on 2007-01-09
reinstall but instead add the wine  repository in Synaptic and then install wine, like on their web site 

[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb). 

I then run in a terminal 

winecfg

and then try installing a .exe and have fun!!!!!!
:-k

---

### Post by Barney on 2007-01-09
Swanky,

I did all, &....

barney@homebuilt:~$ winecfg
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
barney@homebuilt:~$

Next suggestion??

---

### Post by Barney on 2007-01-09
I should have asked, when the winecfg window comes open, what should I do?
Which tabs should I "operate?"

I also tried to reinstall Quicken 2005, which appears through the file browser to be in the proper place; and could not - resulting message:

InstallShield
1607: Unable to install InstallShield Scripting Runtime.

????????????

---

### Post by Swankyman on 2007-01-09
In winecfg I normally go to the Drives page and select autodetect, and the click ok. 

Looking at the Wine Application database it looks to me like Quicken 2005 doesn't run in wine and the error you report is just cos it don't work

Quicken 2005 page 

[http://appdb.winehq.org/appview.php?iVersionId=2510](http://appdb.winehq.org/appview.php?iVersionId=2510)

all versions

[http://appdb.winehq.org/appview.php?iAppId=107](http://appdb.winehq.org/appview.php?iAppId=107)

If you have Quicken 2002 that seems to work 

[http://appdb.winehq.org/appview.php?iVersionId=981](http://appdb.winehq.org/appview.php?iVersionId=981)

Rich :-k

---

### Post by Rotodyne on 2007-01-09
I am getting the same error ](*,) so Starcraft won´t install

---

