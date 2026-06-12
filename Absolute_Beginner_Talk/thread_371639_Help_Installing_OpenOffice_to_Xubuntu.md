---
title: "Help Installing OpenOffice to Xubuntu"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by Woody_in_MN on 2007-02-27
Hi.  I successfully installed Xubuntu to a low end HP Pavillion, 256kb RAM.  I want to install OpenOffice.  I have Open Office on a Ubuntu 5.10 LiveCD disk I happened to have.  When I try to install Open Office from the Ubuntu CD by going to the CD => then go to the OpenOffice folder => then clicking on "setup.exe" - I get "Failed to execute setup.exe...(permission denied)"

Am I using the wrong file to initiate install?  Do I have the wrong version?  Do I have to down-load, and burn "OpenOffice for Xubuntu" if there is such a thing?

Thanks in advance,

 - w

---

### Post by hyper_ch on 2007-02-27
Just run this from the shell

```

sudo aptitude install openoffice.org

```

---

### Post by actuary286 on 2007-02-27
You are getting an error from setup.exe because you cannot run the program as a normal user.

The CD you are trying to install from is quite old (October 2005) and probably includes an old version of OpenOffice as well.

The best option is to download and install the newest version of OpenOffice through the Synaptic package manager. For instructions on how to use Synaptic see [Adding, Removing and Updating Applications]("https://help.ubuntu.com/6.10/xubuntu/desktopguide/C/add-applications.html") in the [Xubuntu Desktop Guide]("https://help.ubuntu.com/6.10/xubuntu/desktopguide/C/index.html"). I assume you are running version 6.10 (Edgy Eft), but the guide is available for older versions as well.

Once you have Synaptic running use the Search feature to look for openoffice.org. A number of packages will be found, but you only need the openoffice.org package, it will install everything you need.

You shouldn't have to worry the Extra Repositories mentioned in the Guide for OpenOffice, but you might consider adding them later since they have a lot of great software.

---

### Post by Woody_in_MN on 2007-02-27
> **hyper_ch said:**
> Just run this from the shell


How do I swap out to the shell?

 - w

---

### Post by actuary286 on 2007-02-27
The shell is accessed through the Terminal application. It should be under either Accessories or System Tools in the Applications menu.

---

### Post by Woody_in_MN on 2007-02-27
> **hyper_ch said:**
> Just run this from the shell

```

sudo aptitude install openoffice.org

```


Will this command work if I am not connected to the internet? My guess is no.  Please confirm.

Thanks,

 - w

---

### Post by Maestro23 on 2007-02-27
No, you need access to the Repositories.  There is another way. I installed OpenOffice 2.1 with the method in the following link.  You first need to d/l the OpenOffice.rpm from their site.  Then find the post by sgla1 in the link below.  Follow his instructions.

It worked like a charm for me.  Good luck.

[http://www.ubuntuforums.org/showthread.php?t=318865&page=3&highlight=Install+OpenOffice](http://www.ubuntuforums.org/showthread.php?t=318865&page=3&highlight=Install+OpenOffice)

Just another option for you.

---

### Post by Woody_in_MN on 2007-02-27
After trying a couple different versions of O/S on that low-end PC (only 256 KB ram) - I actually am running Ubuntu 6.10 on that PC.  Unbuntu 6.10 itself seems to run pretty nicely - OpenOffice will run, but it is a little slow.  Is there a OpenOffice "Lite" out there? 
Is there an alternative to OpenOffice that will still give me a word processor, and spreadsheet, that is file-compatible with the MS Office suite?  (I probably only need compatibioity thru Office 97 version - comptabile thru MS Office 2000 would be nice.)

Suggestions?

 - w

---

### Post by Brunellus on 2007-02-27
> **Woody_in_MN said:**
> After trying a couple different versions of O/S on that low-end PC (only 256 KB ram) - I actually am running Ubuntu 6.10 on that PC.  Unbuntu 6.10 itself seems to run pretty nicely - OpenOffice will run, but it is a little slow.  Is there a OpenOffice "Lite" out there? 
Is there an alternative to OpenOffice that will still give me a word processor, and spreadsheet, that is file-compatible with the MS Office suite?  (I probably only need compatibioity thru Office 97 version - comptabile thru MS Office 2000 would be nice.)

Suggestions?

 - w
GnomeOffice.  The two crucial components you care about are AbiWord and GNUmeric

---

### Post by Frak on 2007-02-27
> **Woody_in_MN said:**
> After trying a couple different versions of O/S on that low-end PC (only 256 KB ram) - I actually am running Ubuntu 6.10 on that PC.  Unbuntu 6.10 itself seems to run pretty nicely - OpenOffice will run, but it is a little slow.  Is there a OpenOffice "Lite" out there? 
Is there an alternative to OpenOffice that will still give me a word processor, and spreadsheet, that is file-compatible with the MS Office suite?  (I probably only need compatibioity thru Office 97 version - comptabile thru MS Office 2000 would be nice.)

Suggestions?

 - w
Try AbiWord - Very light | and Gnumeric - Great (Light) spreadsheat app.

---

### Post by actuary286 on 2007-02-28
I definitely second the above. Gnumeric works well with .xls files from Excel and Abiword can read and save Word .doc files, but the Abiword developers have a [Caveat]("http://www.abisource.com/twiki/bin/view/Abiword/FaqMicrosoftWordDocuments") on their website.

Also, with Office 2007 Microsoft has changed the format that all the applications use so Abiword and Gnumeric probably won't work with those files right now.

---

### Post by Frak on 2007-02-28
> **actuary286 said:**
> I definitely second the above. Gnumeric works well with .xls files from Excel and Abiword can read and save Word .doc files, but the Abiword developers have a [Caveat]("http://www.abisource.com/twiki/bin/view/Abiword/FaqMicrosoftWordDocuments") on their website.

Also, with Office 2007 Microsoft has changed the format that all the applications use so Abiword and Gnumeric probably won't work with those files right now.
Actually, I've been able to open Office 2007 Files finely in StarOffice, so it should also work with OpenOffice.Org and AbiWord. The "new" format is just .xml

---

### Post by Brunellus on 2007-02-28
> **Frak said:**
> Actually, I've been able to open Office 2007 Files finely in StarOffice, so it should also work with OpenOffice.Org and AbiWord. The "new" format is just .xml
. . . with MSFT proprietary extensions, right?

---

### Post by Frak on 2007-02-28
> **Brunellus said:**
> . . . with MSFT proprietary extensions, right?
Yeah, but they'll eventually be reverse engineered...

---

