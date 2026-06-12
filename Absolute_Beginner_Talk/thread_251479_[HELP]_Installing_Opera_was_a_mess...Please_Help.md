---
title: "[HELP] Installing Opera was a mess...Please Help"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by navneeth on 2006-09-05
The downloaded version of Opera (9.1 .deb file) was missing an important dependancy(?) - qtlib3, if I remember the name correctly and would not let me install. That didn't help much. After that I found 'Opera Browser' in Automatix, and then let it install, but I couldn't find it under  Applications->Internet. Where's Opera? I also checked the .deb file once more only to the find the error that appeared earlier missing, but still I don't see Opera installed. :confused: 

I found this page with links to some files...
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=libqt3-mt&version=dapper&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=libqt3-mt&version=dapper&arch=i386)
Can someone tell me which file to download and what to do once it is downloaded?

---

### Post by zerwas on 2006-09-05
Click on Applications - Add/Remove - "Show commercial software" and search for opera :)

---

### Post by mustang on 2006-09-05
Or just type 

```
opera
```

in the terminal.

---

### Post by navneeth on 2006-09-05
> **zerwas said:**
> Click on Applications - Add/Remove - "Show commercial software" and search for opera :)
That seems to be a solution. But the problem is my internet connection is virtually dead when I'm working in Ubuntu. It takes a long time to get the required files, and if the connection is bad, the operation is timed out. ](*,) 

Btw, typing 'Opera'in the terminal only returned 
```
Bash: Opera: Command not found
```

---

### Post by Dinerty on 2006-09-05
> **navneeth said:**
> The downloaded version of Opera (9.1 .deb file) was missing an important dependancy(?) - qtlib3, if I remember the name correctly and would not let me install. That didn't help much. After that I found 'Opera Browser' in Automatix, and then let it install, but I couldn't find it under  Applications->Internet. Where's Opera? I also checked the .deb file once more only to the find the error that appeared earlier missing, but still I don't see Opera installed. :confused: 

I found this page with links to some files...
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=libqt3-mt&version=dapper&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=libqt3-mt&version=dapper&arch=i386)
Can someone tell me which file to download and what to do once it is downloaded?

Ok mate, do this in the terminal:

```
sudo gedit /etc/apt/sources.list
```

then add this to your sources.list and save it

##The Opera browser
##Opera provides their own packages here
## The Opera browser (packages)
deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free

then

```
sudo apt-get update
```

then whenever you want to install it, just type this in the terminal

```
sudo apt-get install opera
```

it will download it for you and install it and add it to your menu under "Applications > Internet"

---

### Post by navneeth on 2006-09-05
Thanks, Dinerty. I'm ready to try all methods. Please correct me if I'm wrong, but won't this also depend on my internet connection? 

I'm actually trying to get Opera because many people say that it's faster than Firefox. Apparently, everything slows down in my computer when it comes to the internet. That's why I downloaded the deb file in Windows and transferred it to Ubuntu from a CD.

---

### Post by Dinerty on 2006-09-05
> **navneeth said:**
> Thanks, Dinerty. I'm ready to try all methods. Please correct me if I'm wrong, but won't this also depend on my internet connection? 

I'm actually trying to get Opera because many people say that it's faster than Firefox. Apparently, everything slows down in my computer when it comes to the internet. That's why I downloaded the deb file in Windows and transferred it to Ubuntu from a CD.

It will basically download the .deb and install it all for you, cannot recall the exact size of the file, but think it is around 10mb.

Depending on your connection it won't take long to download and then you will be whizzing around the net with Opera 9 ;)

---

### Post by gkiller on 2006-09-05
Actually there is a very good page on the wiki about Opera:
[https://help.ubuntu.com/community/OperaBrowser]("https://help.ubuntu.com/community/OperaBrowser")

Just follow the instructions there. You can use method 1 or method 2 for installing. If you have a slow internet connection, you can download the .deb from the Opera site with another PC and then copy the .deb to your Ubuntu installation. (But as the post above said, Opera is quite small, about 6 MB)

If you then still have any questions, don't hesitate to ask.

---

### Post by navneeth on 2006-09-05
gkiller,
  Yes, I did check that wiki before downloading Opera. To know what happened by using the first method please check the first post in this thread. Btw, that deb file was somewhere between 5 and 6 MB.

The thing is, I don't have a slow internet connection, relatively speaking. It's 256kbps. But while I'm working in Ubuntu I feel like I'm using dial-up or something worse than that. 

I do appreciate all your help, but it looks like that I'll need a properly functioning connection to try out any of the above methods. Since it seems now that it's slow irrespective of whether I'm using a web browser, I think something else need to be done.

Btw, does anyone know how to obtain the Static Version that mentioned in the article.> 
Static version: Opera has the Qt library built in. It's a larger download, and it doesn't use antialiased fonts on menus or the filechooser, and uses aliasing in the browser window and most other inferface elements.

---

### Post by gkiller on 2006-09-05
> **navneeth said:**
> gkiller,
  Yes, I did check that wiki before downloading Opera. To know what happened by using the first method please check the first post in this thread. Btw, that deb file was somewhere between 5 and 6 MB.
Did you type 'sudo apt-get -f install' after installing the .deb? Do you have the universe and multiverse repositories added? Maybe you need them, but I don't know for certain where the needed packages are.

Unfortunately I cannot help with the internet connection problems.

> Btw, does anyone know how to obtain the Static Version that mentioned in the article.
On the Opera download page, select "Other/static DEB" from the drop-down menu. Although I don't know if this generic deb will add the Application menu entry correctly.

---

### Post by navneeth on 2006-09-05
> **gkiller said:**
> Did you type 'sudo apt-get -f install' after installing the .deb? 
Actually I never got to install the .deb package. Anyway, if I'm able to get that file do something I'll do the 'sudo apt-get -f install' .

> 
Do you have the universe and multiverse repositories added? Maybe you need them, but I don't know for certain where the needed packages are.
Sorry for the noob question, but what are those? 



> 
On the Opera download page, select "Other/static DEB" from the drop-down menu. Although I don't know if this generic deb will add the Application menu entry correctly.
Thanks. I'll check that out.

---

### Post by gkiller on 2006-09-05
> **navneeth said:**
> Actually I never got to install the .deb package. Anyway, if I'm able to get that file do something I'll do the 'sudo apt-get -f install' .
I am not 100% sure, but I think typing 'sudo apt-get -f install' after the .deb package fails to install will fix the dependencies and then you are able to install the .deb. But since I'm quite new to Linux too, I might be wrong here. ;) But it shouldn't break anything anyway if you run the command.
> [Repositories]
Sorry for the noob question, but what are those?
Ubuntu's software packages are stored in repositories. There is the main repository, where all officially supported packages go. Then there are universe and multiverse repositories, where there are lots more packages, but these are not enabled by default. To enable them, you can follow these instructions:
[http://easylinux.info/wiki/Ubuntu_dapper#Repositories](http://easylinux.info/wiki/Ubuntu_dapper#Repositories)
(I would deactivate the PLF repository mentioned on that page, because it is unofficial and not needed anyway).

---

### Post by mssever on 2006-09-05
> **navneeth said:**
> Actually I never got to install the .deb package. Anyway, if I'm able to get that file do something I'll do the 'sudo apt-get -f install' .

Sorry for the noob question, but what are those [universe/multiverse]? 

Thanks. I'll check that out.
[http://psychocats.net/ubuntu/sources](http://psychocats.net/ubuntu/sources)

> **navneeth said:**
> Btw, typing 'Opera'in the terminal only returned 
```
Bash: Opera: Command not found
```

The reason for this is that Linux is case sensitive. That means that "Opera" and "opera" are entirely different. Try typing opera in all lowercase letters. BTW, you should assume that all Linux command-line stuff is in lowercase unless you know otherwise.

---

### Post by navneeth on 2006-09-06
An update: I have Opera installed thanks to the static package that came with all necessary files, but still, internet is very slow. :(

---

### Post by Dinerty on 2006-09-06
Is browsing really slow and webpages take ages to load?, if so it could be a ipv6 issue

---

### Post by Psquared on 2006-09-09
Question; the static version of Opera says "intel-linux' and I have an AMD processor. Will that make a difference in how it performs?

---

