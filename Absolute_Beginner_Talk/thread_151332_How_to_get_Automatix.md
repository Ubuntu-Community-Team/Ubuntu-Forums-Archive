---
title: "How to get Automatix"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2006-03-27
Following the instructions at:

[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

for

 How to add extra repositories

then

 How to get Automatix

returns an: 

3 upgraded, 60 newly installed, 0 to remove and 242 not upgraded.
Need to get 10.4MB of archives.
After unpacking 10.7MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort.

I thought I pasted the Repositories data. No, I did the copy and paste correctly. I did it religously. Is there another reason for the Abort?

---

### Post by arnieboy on 2006-03-27
if u are using an x86 version of Ubuntu Breezy do the following one after other from terminal to install automatix:
```
wget http://beerorkid.com/automatix/automatix_5.7-3_i386.deb
sudo dpkg -i automatix_5.7-3_i386.deb
```

---

### Post by John.Michael.Kane on 2006-03-27
Try reading here [http://www.ubuntuforums.org/showthread.php?t=138405](http://www.ubuntuforums.org/showthread.php?t=138405)


Edit: arnieboy beat me to it..

---

### Post by Mark_in_Hollywood on 2006-03-27
This is a Dell Dimension 4100 computer. Uses a 733MegHz Intel cpu. I'm very sure the arch=386. 

Here's the results, of which I am duly confuszested


root@lexington:/home/mark # wget [http://beerorkid.com/automatix/automatix_5.7-3_i386.deb](http://beerorkid.com/automatix/automatix_5.7-3_i386.deb)
--15:20:44--  [http://beerorkid.com/automatix/automatix_5.7-3_i386.deb](http://beerorkid.com/automatix/automatix_5.7-3_i386.deb)
           => `automatix_5.7-3_i386.deb'
Resolving beerorkid.com... 208.97.133.175
Connecting to beerorkid.com|208.97.133.175|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 33,730 (33K) [text/plain]

100%[====================================>] 33,730         5.35K/s    ETA 00:00

15:20:51 (5.50 KB/s) - `automatix_5.7-3_i386.deb' saved [33730/33730]

root@lexington:/home/mark # sudo dpkg -i automatix_5.7-3_i386.d
dpkg: error processing automatix_5.7-3_i386.d (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 automatix_5.7-3_i386.d

---

### Post by arnieboy on 2006-03-27
[QUOTE=Mark_in_Hollywood]This is a Dell Dimension 4100 computer. Uses a 733MegHz Intel cpu. I'm very sure the arch=386. 

Here's the results, of which I am duly confuszested


root@lexington:/home/mark # wget [http://beerorkid.com/automatix/automatix_5.7-3_i386.deb](http://beerorkid.com/automatix/automatix_5.7-3_i386.deb)
--15:20:44--  [http://beerorkid.com/automatix/automatix_5.7-3_i386.deb](http://beerorkid.com/automatix/automatix_5.7-3_i386.deb)
           => `automatix_5.7-3_i386.deb'
Resolving beerorkid.com... 208.97.133.175
Connecting to beerorkid.com|208.97.133.175|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 33,730 (33K) [text/plain]

100%[====================================>] 33,730         5.35K/s    ETA 00:00

15:20:51 (5.50 KB/s) - `automatix_5.7-3_i386.deb' saved [33730/33730]

root@lexington:/home/mark # sudo dpkg -i automatix_5.7-3_i386.d
dpkg: error processing automatix_5.7-3_i386.d (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 automatix_5.7-3_i386.d[/QUOTE]
u mistyped the last command. just copy and paste next time. The command is as follows:
```
sudo dpkg -i automatix_5.7-3_i386.deb
```
u furnished an incomplete file name while trying to install the same.

---

### Post by Mark_in_Hollywood on 2006-03-27
Call me CRAZY

it was a cut and paste.

Hmmmmm????

I'm feeling very conspiratorial

HOWEVER, following arnieboy's most recent response

                                                      SUCCESS


root@lexington:/home/mark # wget [http://beerorkid.com/automatix/automatix_5.7-3_i386.deb](http://beerorkid.com/automatix/automatix_5.7-3_i386.deb)
--15:28:38--  [http://beerorkid.com/automatix/automatix_5.7-3_i386.deb](http://beerorkid.com/automatix/automatix_5.7-3_i386.deb)
           => `automatix_5.7-3_i386.deb.1'
Resolving beerorkid.com... 208.97.133.175
Connecting to beerorkid.com|208.97.133.175|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 33,730 (33K) [text/plain]

100%[====================================>] 33,730         5.38K/s    ETA 00:00

15:28:45 (5.50 KB/s) - `automatix_5.7-3_i386.deb.1' saved [33730/33730]

root@lexington:/home/mark # sudo dpkg -i automatix_5.7-3_i386.deb
Selecting previously deselected package automatix.
(Reading database ... 60731 files and directories currently installed.)
Unpacking automatix (from automatix_5.7-3_i386.deb) ...
Setting up automatix (5.7-3) ...
root@lexington:/home/mark #


Mark, signing off and saying:

Thanking the Ubuntu/Linux support community since Jan. 21, 2006

---

