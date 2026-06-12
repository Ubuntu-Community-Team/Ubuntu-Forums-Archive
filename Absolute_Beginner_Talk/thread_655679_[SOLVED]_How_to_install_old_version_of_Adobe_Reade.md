---
title: "[SOLVED] How to install old version of Adobe Reader"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by reefsrt4 on 2008-01-01
This should be fairly simple for many here, but still a bit difficult for me in my early linux user stage....


I had Adobe reader 8 installed, but due to my University website requirements, I must use Adobe 7.0.9  The site saw my Adobe 8 version and claimed it was not supported.  Unfortunately, because of that I cannot read my online books.

So, I downloaded a tar.gz file with the required version of Adobe Reader.  The readme file is useless, it is so generic.

I ran tar "tar -zxvf AdobeReader_enu-7.0.9-1.i386.tar.gz" and it extracted everything onto the Desktop as folder "AdobeReader".

I tried the configure, make, make install through terminal with no success.


Anyone have any guidance to give on how I can get this installed?

Thanks in advance.

---

### Post by oldos2er on 2008-01-01
Have you installed build-essential? If not, in a terminal, type "sudo aptitude install build-essential". Then go into the AdobeReader directory and type "./configure". If you get any more error messages, please copy and paste them here.

---

### Post by reefsrt4 on 2008-01-01
Here's the output from terminal, as requested.

mike@mike-laptop:~$ sudo aptitude install build-essential
[sudo] password for mike:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
mike@mike-laptop:~$ cd Desktop
mike@mike-laptop:~/Desktop$ cd AdobeReader
mike@mike-laptop:~/Desktop/AdobeReader$ ./configure
bash: ./configure: No such file or directory
mike@mike-laptop:~/Desktop/AdobeReader$


Still ending with the same result.  Thanks for your time with this.

---

### Post by oldos2er on 2008-01-01
So I assume you already installed build-essential? Ok.

 Can you post the output of "ls" in ~/Desktop/AdobeReader?

---

### Post by reefsrt4 on 2008-01-01
> **oldos2er said:**
> So I assume you already installed build-essential? Ok.

 Can you post the output of "ls" in ~/Desktop/AdobeReader?

I wasn't really sure if it was installed or not, so I just posted the results of trying to install it, along with the other info.  Here's the latest info requested:



mike@mike-laptop:~$ cd Desktop/AdobeReader
mike@mike-laptop:~/Desktop/AdobeReader$ ls
COMMON.TAR  ILINXR.TAR  INSTALL  LICREAD.TXT  ReadMe.htm
mike@mike-laptop:~/Desktop/AdobeReader$

---

### Post by RomeReactor on 2008-01-01
Hi. Is "INSTALL" a text file? if so, please post its contents.

---

### Post by reefsrt4 on 2008-01-01
> **RomeReactor said:**
> Hi. Is "INSTALL" a text file? if so, please post its contents.

It looks like it is the actual install script, after opening in text editor.....however I don't think it is an install guide text file.  Do you still want me to post the contents?

---

### Post by RomeReactor on 2008-01-01
I just checked, and that is indeed the installer; in the terminal, inside the Adobe Reader directory:
```
sudo ./INSTALL
```

---

### Post by reefsrt4 on 2008-01-01
> **RomeReactor said:**
> I just checked, and that is indeed the installer; in the terminal, inside the Adobe Reader directory:
```
sudo ./INSTALL
```

That worked, it appears to have installed, but I cannot get it to launch.  Through the apps menu or terminal "acroread" as indicated in the bin folder.

Not sure about what is causing this.....any ideas?

---

### Post by RomeReactor on 2008-01-01
Please run it from the terminal:
```
acroread
```

If you get many error messages like this:
```
expr: syntax error
```
press CTRL+C to stop the process, and then you need to install **zsh**:
```
sudo apt-get install zsh
```
and modify the executable by changing its first line:
```
#!/bin/sh
```
to:
```
#!/bin/zsh
```

Where did you select to install it?

---

### Post by reefsrt4 on 2008-01-01
It made its own folder location:  usr/local/Adobe/Acrobat 7.0/



Running the items you have listed above now...will report results.

thanks for the help so far.

---

### Post by reefsrt4 on 2008-01-01
> **RomeReactor said:**
> Please run it from the terminal:
```
acroread
```

If you get many error messages like this:
```
expr: syntax error
```
press CTRL+C to stop the process, and then you need to install **zsh**:
```
sudo apt-get install zsh
```
and modify the executable by changing its first line:
```
#!/bin/sh
```
to:
```
#!/bin/zsh
```

That was it.  zsh was needed.  It now opens and runs.  I swear the problems never end.  I went to the school website and somehow the site still thinks I have Adobe 8.  I shut down and restarted firefox.  Perhaps a shutdown and restart of the computer is required?  I'll see what that does.  As far as my issue of getting an earlier version of Adobe installed and running, that has been accomplished, so thank you for that assistance.  I'll mark this as solved.

If you want to continue helping me with why the site doesn't see the plugin as the current version of Adobe, I certainly wouldn't refuse the assistance.  lol

Thanks again!

---

### Post by RomeReactor on 2008-01-01
Is the site publicly accessible? if so, post the link here, so more people can help.

---

### Post by reefsrt4 on 2008-01-01
It's Devry, but requires my login and password to access my class content.

---

### Post by RomeReactor on 2008-01-01
If you installed Adobe Reader version 8 from the repositories, and still have it in your system, it may be interfering; try uninstalling it.

---

### Post by reefsrt4 on 2008-01-01
> **RomeReactor said:**
> If you installed Adobe Reader version 8 from the repositories, and still have it in your system, it may be interfering; try uninstalling it.

I used synaptic to do a complete removal of Adobe, assuming there might be conflict if I just installed the earlier version.  The install you just helped me through took place after the removal.

I'm guessing even though it was a "complete" removal, it possibly missed something.  I even took the nppdf.so file from the new install and replaced it in the existing plugin folder for firefox.  That didn't work either....

---

### Post by RomeReactor on 2008-01-01
In Firefox, try going in "Edit->Preferences->Content" and press the "Manage" button; see if you can select Acrobat 7 from there. Another thing you could try is deleting the **xpti.dat** file in the hidden mozilla folder in your home directory; close Firefox, open a terminal and:
```
rm ~/.mozilla/firefox/*.default/xpti.dat
```
then open Firefox again and see if you can open the file now.

---

### Post by reefsrt4 on 2008-01-01
Performed both actions, things appear to be in order now.

Thanks a ton!! Sincerely appreciated.

---

### Post by cpbl on 2008-01-07
Where did you get your copy of Adober reader 7? Could you post a link?
I am running the latest Gutsy and Adobe Reader 8 won't print properly. I am usually printing double sided landscape, and evince messes it up horribly too. I don't know why. I've been doing this fine with Adobe 7 for years. 
 I want to revert to the previous version.

---

### Post by RomeReactor on 2008-01-07
Hi. You can find Adobe Reader 7 [here]("ftp://ftp.uni-koeln.de/www/acrobat-reader/unix/AdobeReader_enu-7.0.9-1.i386.tar.gz").

---

