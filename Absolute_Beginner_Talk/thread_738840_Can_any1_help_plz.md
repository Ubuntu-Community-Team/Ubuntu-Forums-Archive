---
title: "Can any1 help plz????"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by NikS on 2008-03-29
Can any1 PLEEEEEEEEEEEEEEESE help me with installing WINE on my ubuntu 7.10 Gusty????

The prblem is i dont have an internet connection, i have to go to netcafe for that, there is no Linux, they use windows!!!

Please tell me where can i find the package With the dependencies???

I downloaded wine from packages.ubuntu.com but the dependencies...... thats very very long list!!! and again the dependencies of the dependencies!!!! that becomes too much..

PLZ tell me where i can find them all!!!

The same is for XMMX and MPLAYER!!!

Plz help!!

---

### Post by paydaydaddy on 2008-03-29
The fact that you are posting tells me that you have internet access. Use the synaptic package manager to install wine. Make sure you have enabled all the repositories and then let synaptic do the work. You will find synaptic under "system", "administration", "synaptic package manager".

---

### Post by NikS on 2008-03-29
Currently I am in a netcafe pal!!!!!!

Not using Ubuntu if u can see the status!!!!

M on windows in a net cafe!!!

Is there a solution??

---

### Post by emshains on 2008-03-29
For wine you must go to [http://wine.budgetdedicated.com/archive/index.html]("http://wine.budgetdedicated.com/archive/index.html")

Then you must download the right architecture deb archive, so you it runs on your kernel. 
Put it on a flash drive and then plug the flash in YOUR computer and you should open it with GDebi package installer, and you should be free to go.
I dont know about the mplayer and xmms thou. I hope this helps.

---

### Post by ubuntu27 on 2008-03-29
Ok. SO your computer does now have INternet Access? That's sad :(

Anyway, what you have to do is to open Synaptic Package Manager [System menu/Administration/Synaptic]

1) Search for the package that you want to download (In this case Wine)

Select Wine to install.

DO NOT click on apply. Instead, 

2) Go to File menu/Generate Package download script
3)Save it to some removable storage device such as USB JumpDrive.

4) Go to a computer connected to the Internet. If it has Windows, Open the saved file (a text file).

5) Copy and paste and URL that are found in that text file to a browser.

6) Download the packages

7) Save the packages to your storage device.

8) Copy it to your Ubuntu Computer. 

9) Install the package


Done.

Enjoy :guitar:

---

### Post by psychobeauty on 2008-03-29
you can also download the package from the wine  pages

 [http://www.winehq.org/site/download](http://www.winehq.org/site/download)


in tar.gz its also have an installation and configuration file there...

---

### Post by paydaydaddy on 2008-03-29
Don't get your panties in a bunch. I thought that you were using your computer to connect to a provided wireless "net cafe". Since that is not the case, I will leave it to somebody else to chime in with the solution. Sorry I can't be of more help. Good luck!

---

### Post by NikS on 2008-03-29
Alright, Thanks every1

I'l try that out..

From what i tried previously, the packages downloaded from wineHQ (.deb) do still require dependencies to be downloaded seperately!!!
The same problem m looking for an answer to, actually, thats where i got my wine package from...

well, i'l try the remaing out..

---

### Post by ubuntu27 on 2008-03-29
> **NikS said:**
> Alright, Thanks every1

I'l try that out..

From what i tried previously, the packages downloaded from wineHQ (.deb) do still require dependencies to be downloaded seperately!!!
The same problem m looking for an answer to, actually, thats where i got my wine package from...

well, i'l try the remaing out..

Try what I wrote on [post Number 5]("http://ubuntuforums.org/showpost.php?p=4609023&postcount=5")

What it does is create a script that tell the computer where to get the files from INCLUDING THE DEPENDENCIES. 

You can open it as a text file with NotePad or any other text editor. When you open that file, you will find:

```
#!/bin/sh
wget -c http://ftp.debian.org/debian/pool/main/w/wine/libwine_0.9.58-1_i386.deb
wget -c http://ftp.debian.org/debian/pool/main/w/wine/libwine-alsa_0.9.58-1_i386.deb
wget -c http://ftp.debian.org/debian/pool/main/w/wine/libwine-cms_0.9.58-1_i386.deb
wget -c http://ftp.debian.org/debian/pool/main/w/wine/libwine-gl_0.9.58-1_i386.deb
wget -c http://ftp.debian.org/debian/pool/main/w/wine/libwine-gphoto2_0.9.58-1_i386.deb
wget -c http://ftp.debian.org/debian/pool/main/w/wine/libwine-ldap_0.9.58-1_i386.deb
wget -c http://ftp.debian.org/debian/pool/main/w/wine/libwine-print_0.9.58-1_i386.deb
wget -c http://ftp.debian.org/debian/pool/main/w/wine/libwine-sane_0.9.58-1_i386.deb
wget -c http://ftp.debian.org/debian/pool/main/w/wine/wine-bin_0.9.58-1_i386.deb
wget -c http://ftp.debian.org/debian/pool/main/w/wine/wine-utils_0.9.58-1_i386.deb
wget -c http://ftp.debian.org/debian/pool/main/w/wine/wine_0.9.58-1_i386.deb

```

Something like that.** Don't copy what I wrote**, that's for my computer, not yours.  I am using Debian GNU/Linux, not Ubuntu.
Your output will be different.

As I was saying, you will find the addres, download individual packages and save it. Then transfer it to your Ubuntu box :)

---

### Post by NikS on 2008-03-29
Many thanks Pal...

---

### Post by ugm6hr on 2008-03-29
Only potential problem with using the Synaptic download script with a computer that has never been online is that the "sources" list will not have been updated since Oct 2007.

So, while it will work, the installed packages may not be the most recent.

If that is an issue - nonetdebs is perhaps a better solution.

[http://nonetdebs.homeip.net/](http://nonetdebs.homeip.net/)

---

### Post by NikS on 2008-03-29
i already tried that!!!

But failed..
The thing is that, in my attempts to install the packages, seems something has updated my status file withoout installing any of the application!!

nonetdebs.homeip.net, says: THE PACKAGES ARE ALREADY INSTALLED!!!

---

### Post by ugm6hr on 2008-03-29
> **NikS said:**
> nonetdebs.homeip.net, says: THE PACKAGES ARE ALREADY INSTALLED!!!

Maybe ask for help from the nonetdebs maintainer?

[http://ubuntuforums.org/showthread.php?t=572819](http://ubuntuforums.org/showthread.php?t=572819)

---

### Post by ubuntu27 on 2008-03-29
> **ugm6hr said:**
> Only potential problem with using the Synaptic download script with a computer that has never been online is that the "sources" list will not have been updated since Oct 2007.

So, while it will work, the installed packages may not be the most recent.

If that is an issue - nonetdebs is perhaps a better solution.

[http://nonetdebs.homeip.net/](http://nonetdebs.homeip.net/)

I haven't though of that...
What could be the solution then? 

Well, I will go to sleep now. It's 1:47 AM here.

---

### Post by NikS on 2008-03-29
I did post a comment n need helpin the 'Problems?' tab on the site..

No reply to it yet..

---

