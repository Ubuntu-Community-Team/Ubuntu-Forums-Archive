---
title: "adept problem in kubuntu"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by benner on 2006-07-06
tried to add a new repository to adept. now it won't open at all and i can't download any updates.  when i go to 'adept' i get an error message that says:

The APT Database could not be opened! This may be caused by incorrect APT configuration or some similar problem. Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem.

when i tried the former i got:

bash: apt-setup: command not found

when I tried the latter, i got:

E: Type 'http://subversion.jackaudio.org/jack/trunk/jack' is not known on line 1 in source list /etc/apt/sources.list

if you have a suggestions, i'd really appreciate it.  

i'm committed to figuring out linux but there seems to be a lot i need to know.  i don't really understand terminal commands very well and could use a guide on the basics.  a number of things that i want to install don't seem to be available in the repositories.  i selected the universe/multiverse ones that i saw in adept (i used ubuntu before and symbian was different) like jazz++ and vcdmount and so i have downloaded them and tried to install with no luck.  i have followed the instructions in the readme files as best as i could but 'configure' and 'make' don't ever seem to do anything.  i get 'command not found' etc..   i have been monkeying around for ages but i'm not getting it

---

### Post by shoot2kill on 2006-07-06
post  here your sources.list

> sudo gedit /etc/apt/sources.list

---

### Post by benner on 2006-07-06
maybe i dodn't understand.  i typed the command into Konsole:

ben@kubuntu:~$ sudo gedit /etc/apt/sources.list
Password:
sudo: gedit: command not found
ben@kubuntu:~$

this is what happened...

---

### Post by Jucato on 2006-07-06
He's using Kubuntu. the command is
```
kate /etc/apt/sources.list
```
(he doesn't need root privileges just to view the file)

There was probably a problem with the repository you added, so that's messing up with Adept. If you post the contents of ther sources.list, we might be able to determine what the problem is. It could also help if you could tell us what repository you were trying to add.

---

### Post by shoot2kill on 2006-07-06
> sudo kate /etc/apt/sources.list

try that...

---

### Post by crystal on 2006-07-06
Since you are using Kubuntu, what if you change "gedit" to "kate" or "kwrite"? Or if that doesnt work, "nano" or "vi" might, but the latter may be trickier to handle.

---

### Post by benner on 2006-07-06
i switched 'gedit' to 'kate' and got the following:


X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.
ScimInputContextPlugin()
kate: WARNING: Can't open /root/share/apps/konqueror/bookmarks.xml

then, Kate opened and displayed this:

[http://subversion.jackaudio.org/jack/trunk/jack](http://subversion.jackaudio.org/jack/trunk/jack)
# 
# deb cdrom:[Kubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted 


deb cdrom:[Kubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted 

deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) dapper main restricted 
deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) dapper main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) dapper-updates main restricted 
deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) dapper-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) dapper universe 
deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) dapper universe 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse 
deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse 


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe 


thanks for your help.  you guys are really great to be sharing your time like this...

---

### Post by Jucato on 2006-07-06
Just a few "notes":
1. KDE doesn't have gedit. It's default text editor is Kate (w/c stands for KDE Advanced Text Editor). KWrite is a stripped down version.
2. When launching GUI-based apps with root access, never use *sudo* only. For GNOME, use *gksudo*. For KDE, use *kdesu*.

So in the OP's case, the full command is
```
kdesu kate /etc/apt/sources.list
```
which shoot2kill also posted.

---

### Post by crystal on 2006-07-06
> When launching GUI-based apps with root access, never use sudo only. For GNOME, use gksudo. For KDE, use kdesu.
Off topic here, but could you explain, or link to an article that explains, why this is so?

---

### Post by Jucato on 2006-07-06
[quote=benner]i switched 'gedit' to 'kate' and got the following:


X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.
ScimInputContextPlugin()
kate: WARNING: Can't open /root/share/apps/konqueror/bookmarks.xml
[/QUOTE]
This is normal, AFAIK

This line is your problem:
> 
[http://subversion.jackaudio.org/jack/trunk/jack]("http://subversion.jackaudio.org/jack/trunk/jack")


That shouldn't be in there, or at least, it's not the proper way to add repositories. You can temporarily solve your problem by either removing that line or putting a '#' at the start of the line to disable it. something like
> #[http://subversion.jackaudio.org/jack/trunk/jack]("http://subversion.jackaudio.org/jack/trunk/jack")

If you could tell us what you were trying to do in the first place, or where you got that URL/address, maybe we could help you with what you're trying to do.

Oh, and you can also delete this line:
> 
deb cdrom:[Kubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

---

### Post by shoot2kill on 2006-07-06
delete the website name at the top of the page

---

### Post by Jucato on 2006-07-06
[quote=crystal]Off topic here, but could you explain, or link to an article that explains, why this is so?[/quote]

Sure thing.

From [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
> **NEVER** use sudo to start graphical programs. You should always use gksudo or kdesu to run such programs, otherwise new login attempts may fail. If this happens and at login an error message reports: "Unable to read ICE authority file", log in using the failsafe terminal and execute the command below substituting user for your username.

---

### Post by Jucato on 2006-07-06
Forgive me for double posting, but I wanted this on a separate topic.
I followed the link to Jack, an Audio Connection Kit. This program is available in the Ubuntu repositories. The name of the package in Ubuntu is *jackd*. It's in the universe repositories, which you can enable in Adept.

[http://packages.ubuntu.com/dapper/sound/jackd](http://packages.ubuntu.com/dapper/sound/jackd)

The version in the repositories is 0.100.0, while the latest is 0.101.1. I suggest you stick to the one in the repositories to be absolutely sure that it works with Kubuntu.

---

### Post by benner on 2006-07-06
i was hoping to install 'jack audio connection kit' so i could connect my digital piano to my computer and use some kind of midi sequencer software (jazz++ or rosegarden).  i downloaded it and had the file sitting on my desktop.  i was having trouble following the instructions to install it so i thought 'adept' may be easier.  i couldn't find it while searching with the existing repositories so i got this URL from the readme on my desktop.

sorry, i don't know how to remove the lines that you are talking about.  i'm an absolute beginner here.  cheers.

---

### Post by Jucato on 2006-07-06
Ok this will be quite a long one.

1. Type in the command line (or if you want, you can also press Alt+F2 and type this in)
```
kdesu kate /etc/apt/sources.list
```
This will launch Kate with root privileges, since you will be editing a file owned by root (sources.list).

2. Once Kate is launched, delete these lines, the way you normally deletee text in word processors
> [http://subversion.jackaudio.org/jack/trunk/jack]("http://subversion.jackaudio.org/jack/trunk/jack")
#
and
> 
deb cdrom:[Kubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
Note: delete these lines and only these lines.

3. Save the file and launch up Adept. Since the repository was fixed, Adept will launch normally. Now you can click on "Fetch Updates" to make sure your repositories are working.

Since you have the universe repositories enabled, installing Jack from Adept is easy. Just search for the package name *jackd. *Right-click, and request install. That's all there is to it.

Hope that helps.

---

### Post by benner on 2006-07-07
it worked.  thanks for your help everyone.

---

### Post by Petest on 2008-01-09
Thanks - you've just got me out of the same problem (its great what can be achieved by using the search function). 
Thanks again.

---

