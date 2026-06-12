---
title: "kubuntu with dialup"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by edwardLS on 2006-10-10
Having just recently given kubuntu a try on a Dell Inspiron 9100 laptop, I have fought (and finally won) the battle with getting online using a WinModem with Linux.  I should mention that dialup access is the only viable option at this time for my home use.  My employer is kind enough to permit me to connect that laptop to our Broadband connection to get updates and install new applications.

However, I was wondering if their was an easy way to "download" new applications at work using Broadband, place the downloaded software on removable media, take it home and install the software?  I certainly am concerned with dependencies and such, as I don't currently want to have to learn that battle.  I am more interested in making the 'computer user' switch to Linux.  

Bringing a laptop to work is not difficult; however, I plan to eventually install kubuntu on a tower-desktop - not so portable or even trans-portable.

---

### Post by jordanmthomas on 2006-10-10
You should take a look at klik.
You can download a program and all its dependencies in one file and run it from there.  Uninstallation is easy, too, just delete the file.

[http://klik.atekon.de/](http://klik.atekon.de/)

Not sure what you should do about updates though.

---

### Post by D10 on 2006-10-10
> **edwardLS said:**
> Having just recently given kubuntu a try on a Dell Inspiron 9100 laptop, I have fought (and finally won) the battle with getting online using a WinModem with Linux.  I should mention that dialup access is the only viable option at this time for my home use.  My employer is kind enough to permit me to connect that laptop to our Broadband connection to get updates and install new applications.

However, I was wondering if their was an easy way to "download" new applications at work using Broadband, place the downloaded software on removable media, take it home and install the software?  I certainly am concerned with dependencies and such, as I don't currently want to have to learn that battle.  I am more interested in making the 'computer user' switch to Linux.  

Bringing a laptop to work is not difficult; however, I plan to eventually install kubuntu on a tower-desktop - not so portable or even trans-portable.

I am  in the same boat when it comes to broadband access at home. 

The way I did it was mark what packages I want to install on my home pc, and create a download script using synaptic. [ File> Generate Package Download Script ] I downloaded wget for Windows, and created a batch file that would run wget on the downlaoad script.

Then just add the downloaded packages to synaptic [ File> Add Downloaded Packages ]. I have not had a problem with any updates or packages.

---

### Post by edwardLS on 2006-10-10
D10,
I think you have described a method that will permit me to survive a bit longer with dialup until Broadband becomes available at home.  I use kubuntu and notice that I can't find a means to "Generate Package Download Script."  That is OK, I don't mind using ubuntu to get synaptic; can 'adept' in kubuntu generate package download script?
Could you provide this newcomer with an example of what you describe as "..created a batch file that would run wget on the download script..." please?  Appreciate your assist..

---

### Post by D10 on 2006-10-10
> **edwardLS said:**
> D10,
I think you have described a method that will permit me to survive a bit longer with dialup until Broadband becomes available at home.  I use kubuntu and notice that I can't find a means to "Generate Package Download Script."  That is OK, I don't mind using ubuntu to get synaptic; can 'adept' in kubuntu generate package download script?
Could you provide this newcomer with an example of what you describe as "..created a batch file that would run wget on the download script..." please?  Appreciate your assist..

I am not for sure about adept, I have never used it. I use xubuntu and Simply Mepis (which is a KDE based distro that uses the ubuntu repos). Both of these distros use synaptic as the graphical package manager. Even with kubuntu you should be able to apt get synaptic.

Here is where I downloaded the unix tools for windows [http://unxutils.sourceforge.net](http://unxutils.sourceforge.net) wget is included. After you have your package script saved on your windows pc open it with a text editor and remove the #!/bin/sh line at the top. Then save the txt file as a batch file [script.bat], and execute it. 

To run the batch file you will either need to add it to the usr\local folder of the Unix tools for Windows, or add the folder Unix tools is located to your PATH, and in that case you can run the batch file from anywhere.

Hope that helps

---

### Post by edwardLS on 2006-10-11
D10,
Thanks so much for not only a good solution to my problem, but for the additional assistance provided this newbie.

---

