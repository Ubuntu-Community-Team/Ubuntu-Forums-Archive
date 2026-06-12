---
title: "Uninstall openoffice"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by Thorun on 2007-08-30
I have made a clean install of Ubuntu FF v7.04 with the OpenOffice and all. 
Now, i have recived a kernel update which is allright. But the Update Manager allso wants to install "openoffice.org-core" and several other openoffice things. I have tried to update all those updates twice with the same result: OpenOffice stalling when opening a Spreadsheed document. 
I haven't tried installing the components one at the time though. 

I thought: Maybe i can un-install the Ubuntu-OpenOffice totally, and then get a clean install of OpenOffice from the original openoffice.org website. Which i hope wery much then would work.
(i don't even know if i have to un-install the Ubuntu-version of OpenOffice - but i think that the two installations will interact with eachother and just continuing stalling the program).

My real question is thereby:
1.
Is it nescesary to un-install the Ubuntu-OpenOffice if i want to install the version from openoffice.org?

2. 
How to un-install the Ubuntu-openoffice?

3. 
How to install the new openoffice?

---

### Post by rsambuca on 2007-08-30
It might be easiest if you try just re-installing OpenOffice first.  Why don't you open your Synaptic Package Manager and then select openoffice.org right click it and select "mark for Reinstallation"

---

### Post by scrooge_74 on 2007-08-30
1. Yes becauser they may not be the same version
2. sudo apt-get remove openoffice.org (or go into synaptic and find all relate open office packages and remove them is just as easy)
3. download the tar file and follow their instructions for install

---

### Post by Thorun on 2007-08-30
Hi again. 
And thank you both for wery quick reply. 

I have tried to follow scrooge_74's method. I got to synaptic and removed everything with relation to OpenOffice.
Now i've stuck with the installation of the new version. 
I have downloaded the .tar.gz file and extracted them on my desktop. 

Now i'm following the pdf-install-guide from the openoffice.org site. Without luck. 

My code to install is as follow:
```
dpkg -i -&#8211;force-overwrite openoffice.org*.deb \
 desktop-integration/openoffice.org-debian-menus*.deb

```

And the output is:
```
root@dell-x1:/home/rune/Desktop/DEBS# dpkg -i -&#8211;force-overwrite openoffice.org*.deb \ desktop-integration/openoffice.org-debian-menus*.deb
dpkg: ukendt tilvalg -  (translated: unknown choice)

Skriv "dpkg --help" for hjælp vedrørende installation og afinstallation af pakker [*];
Brug 'dselect' eller 'aptitude' for en mere brugervenlig pakkehåndtering;
Skriv "dpkg -Dhelp" for en liste over værdierne i dpkg's aflusningsflag;
Skriv "dpkg --force-help" for en liste over gennemtvingningstilvalg;
Skriv "dpkg-deb --help" for hjælp vedrørende manipulation af *.deb-filer;
Skriv "dpkg --license" for ophavsrettigheder og mangel på garanti (GNU GPL) [*].

Tilvalg markeret med [*] giver mange uddata - led dem gennem 'less' eller 'more'!

```

"Skriv" means write. The last line says: Choices marked with [*] gives a lot of data - led them thorugh 'less' or 'more'!. 


Could you guide me thorugh the right code to install the .deb packages?

---

### Post by Thorun on 2007-08-30
Well. Found a guide that just told me to:

```
apt-get install openoffice.org
```
which i did. And it did install someting allright. But not the language which i wanted :(
Now i see, that it's version 2.2.0. 

I tried to open some spreadsheets which worked wery well. Then i opened a .pps  file, and then openoffice froze all over again.. :(:(:(

Heck- what's the deal with this OOo?!

---

### Post by rsambuca on 2007-08-30
Just so you know, the command you just executed does exactly what I suggested to you back in post number 2.  In any event, I don't know why your OO isn't working.  Mine works fine.

---

### Post by Thorun on 2007-08-30
rsambuca 
I think there's a lot of different ways to install OOo but i didn't know that it was the same to re-install than  to apg-get install it. I chose to remove all of the OOo before installing it just to avoid any complication that might could be. 

Now i have played a lot with the program. It seems that it's every third document i open with the OOffice that makes it freeze. I can minimize the window and use the rest of the computer well enough. I just cannot maximize the openoffice window and continue editing the document. 

In the System Monitor I'm able to shut the program down: Ending the process "soffice". And the process is "sleaping". 

Well. Will try to install the exact same thing on my stationary computer and leave my laptop for a while. It's drives me nuts with this error / defect....:confused:

---

### Post by Irihapeti on 2007-08-30
Thorun:
The Ubuntu version of OpenOffice is known to do some odd things. It comes up from time to time on the OpenOffice forums.

For further info on installing the "official" version:
[http://ubuntuforums.org/showthread.php?t=413392&highlight=Open+Office&nojs=1#goto_threadtools](http://ubuntuforums.org/showthread.php?t=413392&highlight=Open+Office&nojs=1#goto_threadtools)
I've used it successfully.

Irihapeti

---

### Post by Thorun on 2007-08-30
Irihapeti

Wohooo :D

This time I managed to install the correct version of OpenOffice. I realized, when this version was installed, that with my previous command ```
apt-get install openoffice
``` i just installed the old Ubuntu-version of OOo - and not the "official" one. 

Now - i have installed the official one and with new fancy icons. Even with a registration-document when opening the writer for the first time. 


I just think I'll cite what he/I did for the future - so i can come back at anytime and see, what i did. 

> Cleaned out open office through Synaptic
Installed alien through synaptic
Download the tarball from the open office web site to the desktop and extracted it
Renamed the extracted folder to something easier, like office
Then in terminal:


```
cd Desktop
cd office (or whatever you called the extracted folder)
cd RPMS
sudo alien --scripts --keep-version *.rpm
sudo dpkg -i *.deb
cd desktop-integration
sudo dpkg -i *.deb
```

Worked fine for me and solved the database problem

---

### Post by Thorun on 2007-08-30
Ok. It's not working anyway. I can't even complete the registrationprocess at the wery beginning without OOo gives me this error: OOo is shut down because an unnamed error. "Wait" or "Force Quit". 

Ok - now It doesn't freeze anymore. Which is very good. Now it just tells me, that something is bugged in my computer. And OOo doesn't like it at all :(

---

### Post by Thorun on 2007-08-30
Now i have tried both OOo versions on my stationary computer. No breakdowns or failures. At all!

Conclusion: 
My Dell X1 Laptop has a problem. Maybe i should try  (once again) with a fresh install of Ubuntu and test the OOo immideatly after the install (to ensure that no later installed program could cause the trouble). If it still doesn't work, I'll call DELL for support. 
There is a Dell-support-forum somewhere on the i-net. (wil google it later). 

Thank you all for support and quick supply.

---

