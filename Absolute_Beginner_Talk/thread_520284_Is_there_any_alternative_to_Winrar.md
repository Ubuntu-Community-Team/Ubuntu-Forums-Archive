---
title: "Is there any alternative to Winrar"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by wasim2050 on 2007-08-08
In Winrar there is a good option of keeping the broken file after extracting so is there anysuch alternate software for ubuntu.

---

### Post by aysiu on 2007-08-08
Try *rar* and *unrar*

---

### Post by wasim2050 on 2007-08-08
I want a GUI based program which can keep broken files after extracting like winrar.

Please help

---

### Post by aitorcalero on 2007-08-08
Did you try to install winrar through WINE?

---

### Post by Majorix on 2007-08-08
What is a "broken file"? I believe all software keep the file extracted from after extracting? Or what do you mean?

---

### Post by tbresson on 2007-08-08
A little googling and I found out what a broken file is..

[http://codeccorner.com/usenethelp/WinRar.html](http://codeccorner.com/usenethelp/WinRar.html)

It appears that WinRar can unrar the archive even if some of the files are missing (where the archive is spanned), e.g. you have a movie and are missing some of the last files and you want to try and extract whatever content possible to see the first part of the movie, perhaps to check the quality or something else.

I have no idea if there are any alternatives to WinRar on that point.

I use 7-zip and I like it a lot. I hope some day that it'll be included in the Archive Manager so that you can extract rar files from the gui (which is only possible with the console app at the moment as far as I know).

---

### Post by anaconda on 2007-08-08
I think I had winrar running in wine in my previous linux installation, so it should be possible.

---

### Post by topbot on 2007-08-08
what's wrong with the standard file-roller? with rar and urar installed in the system, it can compress and decompress rar.

Added: Ah, I see, I have misunderstood the initial post, sorry guys.

---

### Post by wasim2050 on 2007-08-08
> **tbresson said:**
> A little googling and I found out what a broken file is..

[http://codeccorner.com/usenethelp/WinRar.html](http://codeccorner.com/usenethelp/WinRar.html)

It appears that WinRar can unrar the archive even if some of the files are missing (where the archive is spanned), e.g. you have a movie and are missing some of the last files and you want to try and extract whatever content possible to see the first part of the movie, perhaps to check the quality or something else.

I have no idea if there are any alternatives to WinRar on that point.

I use 7-zip and I like it a lot. I hope some day that it'll be included in the Archive Manager so that you can extract rar files from the gui (which is only possible with the console app at the moment as far as I know).

This was exactly I was telling about to find out if the movie is worth downloading or not.

So guys is there anysuch program available for Ubuntu.

And if I use wine to install winrar will my installation will be sucessfull.

Please help

---

### Post by wasim2050 on 2007-08-08
It will also be helpful if someone can help me extract broken files through command shell.

---

### Post by mali2297 on 2007-08-13
> **wasim2050 said:**
> It will also be helpful if someone can help me extract broken files through command shell.

Try this:
```

unrar e -kb filename.rar

```

The "-kb" flag tells it to keep the broken files if it fails to completely extract the archive.

You can find *unrar* in the repositories.

---

### Post by ZuruxKakyn on 2007-08-15
how about broken zip files? i need help for extracting broken zip file, and the -kb is not in unzip, therefore cannot be used

---

### Post by alican timur on 2007-08-15
i installled unrar from the synaptic package manager, and it succeeded, but when i try to use it, it gives the error;

```
The program 'unrar' is currently not installed.  You can install it by typing:
sudo apt-get install unrar
Make sure you have the 'multiverse' component enabled
bash: unrar: command not found
```

when i say: 

```
$ sudo apt-get install unrar
```

it returns:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package unrar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package unrar has no installation candidate
```

---

### Post by mali2297 on 2007-08-15
@alican:

Have you checked this?
> 
Make sure you have the 'multiverse' component enabled


@Zurux:

I'm sorry, but I don't know about *unzip*. I couldn't find anything in the manual.

---

### Post by Outrunner on 2007-08-15
@alican timur: You need to enable the multiverse repositories. To do this go into your sources.list file

```
gksudo gedit /etc/apt/sources.list
```

and remove the '#' before every line that starts with 'deb'

Mine looks like this

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ro.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://ro.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ro.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://ro.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ro.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://ro.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ro.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://ro.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ro.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://ro.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb http://archive.ubuntu.com/ubuntu/ feisty-proposed restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ feisty-backports restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
```

---

### Post by jackfusion on 2007-08-18
I get an error when I do this gksudo gedit /etc/apt/sources.list.  the error is 

(gedit:6137): GnomeUI - WARNING **: While connecting to session manager: Authentication Rejected, reson : None of the authentication protocols specfied are supported and host-based authentication failed

What dose it mean?

---

### Post by mali2297 on 2007-08-18
> **jackfusion said:**
> I get an error when I do this gksudo gedit /etc/apt/sources.list.  the error is 

(gedit:6137): GnomeUI - WARNING **: While connecting to session manager: Authentication Rejected, reson : None of the authentication protocols specfied are supported and host-based authentication failed

What dose it mean?

If you got synaptic open, close it. I think that caused the warning (although I could still open sources.list).

---

### Post by mali2297 on 2007-08-18
The multiverse repositories can also be added by using the GUI, look here:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories")

---

### Post by xpod on 2007-08-18
That error is nothing to worry about either.....

Read about it here
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

EDIT:bottom of page

---

### Post by jackfusion on 2007-08-19
> **xpod said:**
> That error is nothing to worry about either.....

Read about it here
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

EDIT:bottom of page

> 

The multiverse repositories can also be added by using the GUI, look here:

[http://ubuntuguide.org/wiki/Ubuntu:F...a_repositories](http://ubuntuguide.org/wiki/Ubuntu:F...a_repositories)



After I get the error a blank source.list shows up in gedit.  How do I get around this?

---

### Post by Kitsun on 2007-08-19
It has been mentioned previously but I would like to say it again.

WinRAR has very good WINE compatibility, the WINE site lists it as Platinum which is their highest rating, I personally use it for files that Ubuntu can't open, there are not many files, but they do come along now and than.

---

### Post by mali2297 on 2007-08-19
> **jackfusion said:**
> After I get the error a blank source.list shows up in gedit.  How do I get around this?

Are you sure the file you open exists and that you're not misspelling the file name?
To be sure, use the autocompletion feature in the terminal, type
```

gksudo gedit /etc/apt/so

```
and press TAB. Then it should autocomplete the name if the file exists.

An alternative is to use an editor like nano,
```

sudo nano /etc/apt/sources.list

```

You were also given an alternative using the menus to get the right repositories, didn't that work?

---

### Post by jackfusion on 2007-08-19
I now get this error.  When trying to install unrar. what do I do?

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package unrar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package unrar has no installation candidate

---

### Post by Lithium17 on 2007-08-19
7zip works well, handles pretty much any type of archive.

---

### Post by mali2297 on 2007-08-20
> **jackfusion said:**
> I now get this error.  When trying to install unrar. what do I do?

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package unrar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package unrar has no installation candidate

After you have made changes in sources.list, type (or copy/paste) the following in the teminal:
```

sudo apt-get update

```
Then try to install. 

> i installled unrar from the synaptic package manager

What did you install? Perhaps you should uninstall it (in synaptic) before you proceed.

---

