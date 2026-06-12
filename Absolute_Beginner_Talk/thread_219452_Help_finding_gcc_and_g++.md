---
title: "Help finding gcc and g++"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by Micik on 2006-07-20
hello to all.
I have ordered ubuntu 6.06 LTS and installed it.
I tried to install anjuta later but I got error message that I don't have appropriate compiler. In terminal windows I typed man gcc and man g++ but man pages cannot be found. Also when I type man python, manual pages about python are opened. Is it possible that gcc is not installed?
I tried to look in Synaptic Software package and on the list I found that gcc is installed but maybe there is no entry in some PATH variable?
Please help me.
I had mandrake linux that came on 3 CDs and this 6.06 comes on 1 Cd so I suppose I don't have all these software. Computer on which is ubuntu installed doesn't have internet connection so upgrade from internet is out of question.

How to be 100% sure if gcc is present and if not how to install it from CD

---

### Post by scxtt on 2006-07-20
try --> **sudo apt-get install build-essential**

---

### Post by nalmeth on 2006-07-20
Explanation:

Ubuntu doesn't come pre-installed with the basic compilers, as it hopes to provide basic end-users with easier (double-click) ways of installing their application.

They are easy to obtain though, hammer off that command and you'll be good to go.

---

### Post by Micik on 2006-07-20
Will that command work regardless the fact that i don't have internet connection?
I assume I need to place installation Cd into cdrom and to type that in terminal window. In which folder I need to go first?

---

### Post by crystal on 2006-07-20
I think build-essential is in the CD. Just give it a try, if it turns out that you must use an online repository, then you can install it when you do have Internet access.

You can type the command from any folder.
```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by nalmeth on 2006-07-20
I'm sorry, I missed the part about the internet connection.
Take Crystal's advice

---

### Post by scxtt on 2006-07-20
just make sure **deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted** is in your **/etc/apt/sources.list** file, do a **sudo apt-get update** (if you had to add it) and then try the line i gave above ...

and make sure the cd is in the drive :p

---

### Post by Micik on 2006-07-20
When I try to execute line
sudo aptitude install build-essential
I get error message:
Malformed line 23 in source list etc/apt/sources.list
I assume I'll need to modify sources.list file, but how to remoce readonly attribute?
I open sources.list file in Text editor but cannot save change, is there any way to log as root user and modify file without problems?
Thanks

---

### Post by Buffalo Soldier on 2006-07-20
Q. How to modify **sources.list** file?

A. Run this command in the commandline:```
sudo gedit /etc/apt/sources.list
```It will then ask you for a password. Just enter the password that you use during login. Don't worry if nothing appears at the screen when you typed the password. It is intended that way as a security measure.

---

### Post by Micik on 2006-07-20
I have a problem and it seems I'm unable to solve it:
I type sudo aptitude install build-essential
and process go. After I type "Y"  in response Do you want to continue? I get following messages:

Unable to stat the mount point /cdrom/ -stat (2 No such file or directory) Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)...

What could be wrong here?
Here's contents of sources.list file:


## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted


Please help

---

### Post by Buffalo Soldier on 2006-07-20
> **Micik said:**
> I have a problem and it seems I'm unable to solve it:
I type sudo aptitude install build-essential
and process go. After I type "Y"  in response Do you want to continue? I get following messages:

Unable to stat the mount point /cdrom/ -stat (2 No such file or directory) Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)...

What could be wrong here?
What is wrong? Well, a few things :)[list=1]
[*] you did not add the approriate Universe and Multiverse repository to the sources.list file,

[*] the only repository listed in your sources.list file is the Ubuntu 6.06 (Dapper) installation CD. Thus you need to insert that particular CD into your CD/DVD drive before you start using apt-get.

[/list]

Possible solutions?[list=1]
[*] Read the user documentation available on [Reposity and how to add them](https://help.ubuntu.com/community/Repositories/Ubuntu)

[*] For example, here's what my sources.list file looks like:
> deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse

deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe
deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
[/list]

---

### Post by firebolt77 on 2006-07-20
hi all...I already installed gcc. I tried to install a program from source code form(tar.gz). When I tried to execute ./configure, it generates an error which is happened because my ubuntu doesn't gave glib library. When I tried to look some informations about glib, I noticed that it is a base library for GNOME n GTK. Doesn't it strange that my ubuntu doesn't have that library,because it is a basic library for GNOME. Does my ubuntu have problems(because it doesn't have the glib library) or it is normal?

---

### Post by Micik on 2006-07-20
Thanks for reply Buffalo Soldier.
Please keep in mind that computer on which ubuntu is installed is not connected to the internet so only place from where I can install is installation CD.
Please, can someone confirem that is possible to install gcc from instalation CD. If it is not possible then I'm wasting your time.

That's why my sources.list is poor, because I deleted all lines that has internet links.
I'm still unable to solve this. Is it really possible without internet? Even if I connect that computer, I have poor 26.4 K connection (dial up) so updates will not make sense.

I need solution only with help of 6.06 CD. I also have Mandrake 10.1 three cds. Maybe I can use them?

And of course CD is placed in cd drive unit befor spt-get commands!

---

### Post by scxtt on 2006-07-20
synaptic should detect that you've inserted a Dapper CD, tho i'm not sure why my line didn't work for you (maybe your entry should be different) ... my suggestion would be to load the disk, open synaptic and click on Edit, then Add CD-ROM to add your disk ... then, if you don't see build-essential after doing a search then it's not going to help you ...

---

### Post by Micik on 2006-07-21
When I click on Add Cdrom I get message E: cannot fetch cdrom or something similar. But when i go on CD/pool/main/... I can found build essential, so files are on CDrom.
I don't know what is wrong, I'll try to reformat and install ubuntu again.

---

### Post by Micik on 2006-07-21
After reformating and reinstalling ubuntu, I have no trpuble to install gcc with help  of using aptitude.
Now I can try to install anjuta that came in tar.gz archive. I extreacted and when I type ./configure I get error message that there is no perl XML parser. I searched CD for that package but culdn't find. Please can you help me finding XML parser for ubuntu?
I have Mandrake installation CDs and I found XML parser there in rpm, so I used:
sudo alien -i xmlperlparserblablabla.rpm and it passed OK, but still I'm getting the same error that XML perl parser is needed. What should I do?

---

