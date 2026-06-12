---
title: "thunderbird download"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by nikef on 2007-08-10
where can i download thunderbird  please,or do i just get it from mozila


thanks :)

---

### Post by MenZa on 2007-08-10
You can install Mozilla Thunderbird by running the following command:

```
sudo apt-get install mozilla-thunderbird
```

---

### Post by Inxsible on 2007-08-10
> **nikef said:**
> where can i download thunderbird  please,or do i just get it from mozila


thanks :)its in the repos too. But i believe that its an older version. so yes, you can download it from mozilla to get the latest version.

---

### Post by MenZa on 2007-08-10
> **Inxsible said:**
> its in the repos too. But i believe that its an older version. so yes, you can download it from mozilla to get the latest version.

You generally shouldn't install software from outside the repositories, even if there is a newer version, unless you require some of these newer features, or if there is a security risk---in which case the repositories are pretty quickly updated.

---

### Post by Inxsible on 2007-08-10
Use this link to install Thunderbird 2.0 on your machine.

[Thunderbird 2]("http://www.techystuff.info/?p=64")

---

### Post by nikef on 2007-08-10
thanks guys :)

---

### Post by MenZa on 2007-08-10
> **Inxsible said:**
> Use this link to install Thunderbird 2.0 on your machine.

[Thunderbird 2]("http://www.techystuff.info/?p=64")

That sounds pretty silly. The repositories have 2.0.0.6:

```
[17:25:26] menza@alderaan - ~ $ apt-cache show mozilla-thunderbird
Package: mozilla-thunderbird
Priority: optional
Section: mail
Installed-Size: 104
Maintainer: Alexander Sack <asac@ubuntu.com>
Architecture: all
Source: thunderbird
Version: 2.0.0.6-0ubuntu1
Depends: thunderbird
Filename: pool/main/t/thunderbird/mozilla-thunderbird_2.0.0.6-0ubuntu1_all.deb
Size: 59082
MD5sum: 4ad204f4e222a5a27f3970852a440e43
SHA1: 5c98d6989e49936d6f69445a977e2c6fd83d8ac3
SHA256: 5f51669d8b3ce267f6bd8b4e83525a4e89f6a22c46337c7fd4cdae71eb055774
Description: Transition package for mozilla-thunderbird rename
 Package to ease upgrading from older mozilla-thunderbird
 package to the new thunderbird package.
 .
 This package can be purged at anytime once the thunderbird
 package has been installed.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: xubuntu-desktop
```

---

### Post by Inxsible on 2007-08-10
> **MenZa said:**
> You generally shouldn't install software from outside the repositories, even if there is a newer version, unless you require some of these newer features, or if there is a security risk---in which case the repositories are pretty quickly updated.
I would have to disagree with you.

I like to have the latest software on my machine, because they resolve the bugs that were present in the earlier versions. Not all releases address bugs, but if you have a newer release, you are pretty much sure that it will either address bugs or add new features or enhance existing features or do all of them.

and Ubuntu repos are updated in 6 months time. So are you saying you should not use some software just because it was not released in time to be in the repos ?

---

### Post by MenZa on 2007-08-10
> **Inxsible said:**
> I would have to disagree with you.

I like to have the latest software on my machine, because they resolve the bugs that were present in the earlier versions. Not all releases address bugs, but if you have a newer release, you are pretty much sure that it will either address bugs or add new features or enhance existing features or do all of them.


I'd agree with you on some points, especially if you're talking about heavy-development software (e.g. Pidgin, which seems to update every week with bajillions of bug fixes). 

If you have Thunderbird 2.0.0.4, you probably won't be missing much from 2.0.0.6.

> **Inxsible said:**
> Ubuntu repos are updated in 6 months time. So are you saying you should not use some software just because it was not released in time to be in the repos ?

Uh, the repositories are continuously updated with new software. Also, in this case, the repository version is the latest version (released August 1st, 2007---that's just 10 days ago!).

---

### Post by nikef on 2007-08-10
i have downloaded from mozila

i have a folder on my desktop,where do i go from here

---

### Post by Inxsible on 2007-08-10
At the time Thunderbird 2 came out (way back when) I remember the repo version was 1.5.0.x( I don't rbr the last digit. it was 8 or 9)

that's why we had to download the latest version from mozilla. That's how I installed it. Maybe the installation left a cruft in my head :)

---

### Post by Inxsible on 2007-08-10
> **nikef said:**
> i have downloaded from mozila

i have a folder on my desktop,where do i go from hereAssuming you downloaded a file called thunderbird-2.0.0.6.tar.gz and have it on your desktop, enter the following commands one after the other in order
```
tar -xvf thunderbird-2.0.0.6.tar.gz
``````
cp -r thunderbird /etc/opt/
``````
cd /usr/bin/
``````
ln -s /etc/opt/thunderbird/thunderbird
``````
echo "[Desktop Entry]"$'\n'"Encoding=UTF-8"$'\n'"Name=Thunderbird"$'\n'"Comment=Thunderbird"$'\n'"GenericName=Email Client"$'\n'"Exec=thunderbird"$'\n'"Terminal=false"$'\n'"X-MultipleArgs=false"$'\n'"Type=Application"$'\n'"Icon=/etc/opt/thunderbird/icons/mozicon50.xpm"$'\n'"Categories=Applications;Network;"$'\n'"StartupNotify=true" > /usr/share/applications/thunderbird.desktop
```This is from the script that I had used. Simply copy-paste the commands in a terminal.

Hope that helps !

---

### Post by MenZa on 2007-08-10
> **Inxsible said:**
> At the time Thunderbird 2 came out (way back when) I remember the repo version was 1.5.0.x( I don't rbr the last digit. it was 8 or 9)

that's why we had to download the latest version from mozilla. That's how I installed it. Maybe the installation left a cruft in my head :)

Correct. I believe it was, what, a month before it was added to the repositories?

---

### Post by nikef on 2007-08-10
> **MenZa said:**
> You can install Mozilla Thunderbird by running the following command:

```
sudo apt-get install mozilla-thunderbird
```

hi thanks,i did try your way,but got loads of errors

so i downloaded from mozila, and extracted it to desktop,can i still use this folder or shall i delete and download again,sorry i am new to all this,its my first download lol

---

### Post by nikef on 2007-08-10
> **Inxsible said:**
> Assuming you downloaded a file called thunderbird-2.0.0.6.tar.gz and have it on your desktop, enter the following commands one after the other in order
```
tar -xvf thunderbird-2.0.0.6.tar.gz
``````
cp -r thunderbird /etc/opt/
``````
cd /usr/bin/
``````
ln -s /etc/opt/thunderbird/thunderbird
``````
echo "[Desktop Entry]"$'\n'"Encoding=UTF-8"$'\n'"Name=Thunderbird"$'\n'"Comment=Thunderbird"$'\n'"GenericName=Email Client"$'\n'"Exec=thunderbird"$'\n'"Terminal=false"$'\n'"X-MultipleArgs=false"$'\n'"Type=Application"$'\n'"Icon=/etc/opt/thunderbird/icons/mozicon50.xpm"$'\n'"Categories=Applications;Network;"$'\n'"StartupNotify=true" > /usr/share/applications/thunderbird.desktop
```This is from the script that I had used. Simply copy-paste the commands in a terminal.

Hope that helps !

thanks i extracted the file before i put it on desktop is it still ok to use

---

### Post by stchman on 2007-08-10
I have a script that installs Thunderbird 2.0.0.6 for Ubuntu.

[http://www.stchman.com/tools/thunderbird_install.sh](http://www.stchman.com/tools/thunderbird_install.sh)

If you don't want TBird anymore then I have an uninstall script

[http://www.stchman.com/tools/thunderbird_uninstall.sh](http://www.stchman.com/tools/thunderbird_uninstall.sh)

It will install TBird, create shortcut and create menu entry.

Script must be run as root with 755 permission.

---

### Post by nikef on 2007-08-10
> **stchman said:**
> I have a script that installs Thunderbird 2.0.0.6 for Ubuntu.

[http://www.stchman.com/tools/thunderbird_install.sh](http://www.stchman.com/tools/thunderbird_install.sh)

If you don't want TBird anymore then I have an uninstall script

[http://www.stchman.com/tools/thunderbird_uninstall.sh](http://www.stchman.com/tools/thunderbird_uninstall.sh)

It will install TBird, create shortcut and create menu entry.

Script must be run as root with 755 permission.

thanks
i am a newby could you explain ,i am not sure what i have to do with the script,or do i  just download it and it will install like windows .

---

### Post by stchman on 2007-08-10
> **nikef said:**
> thanks
i am a newby could you explain ,i am not sure what i have to do with the script,or do i  just download it and it will install like windows .

Yes, just download the script to whatever location you save stuff to.  Lets say for example that you save stuff to the desktop.  After download to the desktop do the following in a terminal:

```

chmod 755 ~/Desktop/thunderbird_install.sh

sudo ~/Desktop/thunderbird_install.sh

```

TBird will be installed and a menu item will be created.

---

### Post by nikef on 2007-08-10
Hi i have downloaded it to the desktop
but when i type in terminal,i get chmod: invalid mode: `755~desktop/thunderbird_install.sh'
Try `chmod --help' for more information.

---

### Post by stchman on 2007-08-10
> **nikef said:**
> Hi i have downloaded it to the desktop
but when i type in terminal,i get chmod: invalid mode: `755~desktop/thunderbird_install.sh'
Try `chmod --help' for more information.

You need a space between the 755 and the ~/Desktop.  Remember to capitalize the Desktop as Linux is case sensitive.

Just copy and paste into a terminal.

---

### Post by nikef on 2007-08-10
sorry for this but it still wont work 
this is what i put into the terminal 

trish@trish-desktop:~$ chmod 755 ~/Desktop/thunderbird_install.sh sudo~/Desktop/thunderbird_install.sh
chmod: cannot access `/home/trish/Desktop/thunderbird_install.sh': No such file or directory
chmod: cannot access `sudo~/Desktop/thunderbird_install.sh': No such file or directory

---

### Post by stchman on 2007-08-10
> **nikef said:**
> sorry for this but it still wont work 
this is what i put into the terminal 

trish@trish-desktop:~$ chmod 755 ~/Desktop/thunderbird_install.sh sudo~/Desktop/thunderbird_install.sh
chmod: cannot access `/home/trish/Desktop/thunderbird_install.sh': No such file or directory
chmod: cannot access `sudo~/Desktop/thunderbird_install.sh': No such file or directory

First off make sure that the thunderbird_install.sh is indeed in the ~/Desktop folder.  cd to ~/Desktop and do an ls command.  You can also verify that the thunderbird_install is there if it appears on your desktop.

When that is done type the following exactly in a terminal:

```

chmod 755 ~/Desktop/thunderbird_install.sh

```

Now once that is done with no errors do this in a terminal:


```

sudo ~/Desktop/thunderbird_install.sh

```

Remember to put spaces between chmod and 755 and a space between 755 and ~.

Also put a space between sudo and ~ in the next command.  Trust me this works as I and others have used it.

---

### Post by nikef on 2007-08-10
okies theres  a thunderbird folder in my desktop 

i copied and paste from here into terminal,and this is what i get 

trish@trish-desktop:~$ chmod 755 ~/Desktop/thunderbird_install.sh
chmod: cannot access `/home/trish/Desktop/thunderbird_install.sh': No such file or directory

---

### Post by stchman on 2007-08-10
> **nikef said:**
> okies theres  a thunderbird folder in my desktop 

i copied and paste from here into terminal,and this is what i get 

trish@trish-desktop:~$ chmod 755 ~/Desktop/thunderbird_install.sh
chmod: cannot access `/home/trish/Desktop/thunderbird_install.sh': No such file or directory

So there is not a file called thunderbird_install.sh in your /home/trish/Desktop folder.

You need to find where the browser downloaded the thunderbird_install.sh file to.  You said there was a thunderbird folder on your desktop.

---

### Post by nikef on 2007-08-10
yes there is a file in there called just that
i downloaded from the link you left,in firefox i clicked tools,downloads and open
a big box came up with lots of txt in it,i clicked save as,it asked where to save i chose desktop

i am very sorry about this,thanks for sticking with me

---

### Post by nikef on 2007-08-10
yes theres a white sheet of paper with a blue square in the middle
and it says underneath this
thunderbird_install.sh

this is what is looking at me on the desktop

---

### Post by Ripfox on 2007-08-10
Gosh...I guess Automatix isn't obsolete after all, huh? I just checked the box for Thunderbird 2.0 and it was installed and working in less time than it took to post this. THIS is one of the reasons I STILL like to keep good ol' Automatix on my machine. :popcorn:

---

### Post by nikef on 2007-08-10
> **ripfox said:**
> Gosh...I guess Automatix isn't obsolete after all, huh? I just checked the box for Thunderbird 2.0 and it was installed and working in less time than it took to post this. THIS is one of the reasons I STILL like to keep good ol' Automatix on my machine. :popcorn:

hi,whats Automatrix and where do i get it from,is it easier than the bloody terminal lol

---

### Post by stchman on 2007-08-10
> **nikef said:**
> yes theres a white sheet of paper with a blue square in the middle
and it says underneath this
thunderbird_install.sh

this is what is looking at me on the desktop

Then the commands should work.  Try this in a terminal:

```

cd /home/trish/Desktop

```

After that do this:
```

chmod 755 ./thunderbird_install.sh

```

When that is successful do this:
```

sudo ./thunderbird_install.sh

```

Let me know if that works.

---

### Post by Ripfox on 2007-08-10
[http://www.getautomatix.com/](http://www.getautomatix.com/)

Just follow the download page...there are LOTS of apps you can install through it including Flash, Java and all the codecs needed to live well on the web. :)

---

### Post by nikef on 2007-08-10
ok that worked,lots of txt came up in the terminal
where do i find thunderbird ?

---

### Post by nikef on 2007-08-10
> **ripfox said:**
> [http://www.getautomatix.com/](http://www.getautomatix.com/)

Just follow the download page...there are LOTS of apps you can install through it including Flash, Java and all the codecs needed to live well on the web. :)

thanks will try that,so does this do away with the terminal then

---

### Post by stchman on 2007-08-10
> **nikef said:**
> ok that worked,lots of txt came up in the terminal
where do i find thunderbird ?

The Thunderbird icon is in the Applications--->Internet--->Thunderbird.

I had to do the Thunderbird 2 that way as Thunderbird 2 is not in the repositories.  Thunderbird 1.5 is in the repositories for Feisty.

I am glad you got it installed.  As far as Thunderbird help I use Evolution so I will not be a whole lot of help in that category.

I would recommend Automatix but I have had problems with it before.  There are many on the forum that say don't use Automatix.

---

### Post by Ripfox on 2007-08-10
Well not really, but it simplifies lots of installs. It is good to know the terminal, and you WILL have to use it sometimes, but this will get you up and running on some stuff easier. Oh, and Thunderbird is under Applications/Internet.
BTW, I personally hav NEVER had a problem with Automatix since Breezy. Those problems seemed to revolve around older incarnations of Ubuntu (for me anyways)

Cheers

---

### Post by nikef on 2007-08-10
> **stchman said:**
> The Thunderbird icon is in the Applications--->Internet--->Thunderbird.

I had to do the Thunderbird 2 that way as Thunderbird 2 is not in the repositories.  Thunderbird 1.5 is in the repositories for Feisty.

I am glad you got it installed.  As far as Thunderbird help I use Evolution so I will not be a whole lot of help in that category.

I would recommend Automatix but I have had problems with it before.  There are many on the forum that say don't use Automatix.

Thank you very much for sticking with me,it must get frustrating when us newbys cant get it right after a few trys,i know thunderbird like the back of my hand lol,as this is what i used in windoze
yes the terminal is very diferent and very new to me will stick at it,once again thank you :)

Oh and i have found thunderbird now thanks

---

### Post by nikef on 2007-08-10
> **ripfox said:**
> Well not really, but it simplifies lots of installs. It is good to know the terminal, and you WILL have to use it sometimes, but this will get you up and running on some stuff easier. Oh, and Thunderbird is under Applications/Internet.
BTW, I personally hav NEVER had a problem with Automatix since Breezy. Those problems seemed to revolve around older incarnations of Ubuntu (for me anyways)

Cheers

thanks will look into it,and if i get any problems i can remove it ,yes i agree its good to get to know the terminal,it was just a bit of a sock to have to download like that after using windoze xp 
:) i supose i have been spoilt

---

### Post by stchman on 2007-08-10
> **nikef said:**
> Thank you very much for sticking with me,it must get frustrating when us newbys cant get it right after a few trys,i know thunderbird like the back of my hand lol,as this is what i used in windoze
yes the terminal is very diferent and very new to me will stick at it,once again thank you :)

Oh and i have found thunderbird now thanks

Just stick with Ubuntu.  After a while you will get the hang of it.  Remember, you had to learn Windows as well.  I have been using Ubuntu for about 6 months and have not looked back.

---

### Post by nikef on 2007-08-10
> **stchman said:**
> Just stick with Ubuntu.  After a while you will get the hang of it.  Remember, you had to learn Windows as well.  I have been using Ubuntu for about 6 months and have not looked back.

Oh i will defanatly be sticking with ubuntu  theres no windows on this pc,i did a whole disc install

:guitar:   and loving every minute of it :popcorn:

---

### Post by Xierxes on 2007-10-05
> **MenZa said:**
> That sounds pretty silly. The repositories have 2.0.0.6:

```
[17:25:26] menza@alderaan - ~ $ apt-cache show mozilla-thunderbird
Package: mozilla-thunderbird
Priority: optional
Section: mail
Installed-Size: 104
Maintainer: Alexander Sack <asac@ubuntu.com>
Architecture: all
Source: thunderbird
Version: 2.0.0.6-0ubuntu1
Depends: thunderbird
Filename: pool/main/t/thunderbird/mozilla-thunderbird_2.0.0.6-0ubuntu1_all.deb
Size: 59082
MD5sum: 4ad204f4e222a5a27f3970852a440e43
SHA1: 5c98d6989e49936d6f69445a977e2c6fd83d8ac3
SHA256: 5f51669d8b3ce267f6bd8b4e83525a4e89f6a22c46337c7fd4cdae71eb055774
Description: Transition package for mozilla-thunderbird rename
 Package to ease upgrading from older mozilla-thunderbird
 package to the new thunderbird package.
 .
 This package can be purged at anytime once the thunderbird
 package has been installed.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: xubuntu-desktop
```

I was wondering what repo you are using. I am using Fiesty and when running the same command I am given  (amongst others):

```

Section: mail
Installed-Size: 29752
Maintainer: Alexander Sack <asac@ubuntu.com>
Architecture: i386
Version: 1.5.0.13-0ubuntu0.7.04

```
Cheers

---

### Post by por100pre1 on 2007-10-05
> **Xierxes said:**
> I was wondering what repo you are using. I am using Fiesty and when running the same command I am given  (amongst others):

```

Section: mail
Installed-Size: 29752
Maintainer: Alexander Sack <asac@ubuntu.com>
Architecture: i386
Version: 1.5.0.13-0ubuntu0.7.04

```
Cheers

Thats the version present in the repositories. You can use [Ubuntuzilla]("http://ubuntuzilla.wiki.sourceforge.net/") for installing version 2 easily.

---

