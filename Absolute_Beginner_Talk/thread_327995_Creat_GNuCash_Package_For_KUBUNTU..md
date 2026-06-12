---
title: "Creat GNuCash Package For KUBUNTU."
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by 7mm on 2006-12-30
HI There, I'm Using KUBUNTU 6.10. I'm a Windows User With Not Much Linux Experience. Though I Enjoyed The UBUNTU Very Much & Now Using KUBUNTU. I Want To Use GnuCash Accounting Software & I've Searched For It But Package Available Is Beyond My Level (MS Windows) Of Knowlege. I Just Can't Understand The Procedure To Installation.

A Single Easy To Install File Or Such Installation Proccess Can Help Me. Can Anybody Creat Such File & Help Me. Please Help! :confused:

---

### Post by Jussi01 on 2006-12-30
Its in synaptic - if you go to the search part of synaptic then search for gnucash you can install it from there. also, Im not sure how it is in kubuntu, but in gnome you can add it through add remove programs. alternately you can type into terminal: 

```
sudo apt-get install gnucash
```

then enter your password

and it will be installed.

---

### Post by xopher on 2006-12-30
Ok, well as you see here, I did a quick search, which then told me that gnucash is available in the ubuntu repositories, universe to be specific.

([http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gnucash&searchon=names&subword=1&version=edgy&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gnucash&searchon=names&subword=1&version=edgy&release=all"))

This can easily be done from eg. the terminal too, with the simplest command:

```
apt-cache search gnucash
```

Which will show all the packages containing gnucash in either the name or description.
From there you can find that the packagename actually is gnucash, and for more information you could do a:

```
apt-cache show gnucash
```

Allright, enough.. Nothing of the above is actually needed to install it, it's much simpler than that. Just tried to explain how we concluded what the package name was exactly.

To install, make sure you have universe enabled in your /etc/apt/sources.list, then just do a:

```
sudo apt-get install gnucash
```

And voilà, there you go :)

Remember, everything you need, most of the times, are already in the repositories, so no need to download anything third party, no single files etc. Let (syn)apt(ic) do the job. You just sit back and enjoy the (short) ride, while it installs everything for you. ;)

Edit; seems someone beat me to it while I was writing all this nonsense, hehe..

---

### Post by Sef on 2006-12-30
A couple of minor points

First, update first:  ```
 sudo aptitude update
```

then install using aptitude: ```
sudo aptitude install gnucash
```

Aptitude is an updated version of apt-get.   If you use it to install a program and then decide to remove the program, it will remove the dependencies too.  Apt-get won't remove the dependencies.

---

### Post by 7mm on 2006-12-30
Thank You "Jussi01", "xopher" & "Sef" For Your Help. I Really Appriciate Your Effort Here :KS . Though "xopher" Mentioned Some Command Line Help Here & It Nearly Worked For Me. Since I'm a Dial-Up User It'll Cost Me More To Download Entire Package Through Phone Line ](*,)  . So I've Downloaded With High Speed Cyber Cafe. Now I Have The Package, But Don't Know How To Install It :-k  . I've Downloaded The File ( gnucash-2.0.2 ). Please Help :confused: .

---

### Post by Sef on 2006-12-30
The problem with what you did is that you may not have all the dependencies needed to run gnucash, especially since you are running Kubuntu.  They are listed in [packages.ubuntu.com]("http://packages.ubuntu.com/edgy/gnome/gnucash").  I do not know whether they were download along with gnucash.

---

### Post by 7mm on 2006-12-30
> **Sef said:**
> The problem with what you did is that you may not have all the dependencies needed to run gnucash, especially since you are running Kubuntu.  They are listed in [packages.ubuntu.com]("http://packages.ubuntu.com/edgy/gnome/gnucash").  I do not know whether they were download along with gnucash.

Wel Then, It's The Right Time & Right Setup To Check It Out, If IT's Working Or Not. Just Help Me With The Installation Procedure. Remember, Linux Command Line Is Still New To Me.

---

### Post by macogw on 2006-12-30
If you downloaded a .deb, just put it on your desktop and double click.  It'll run the installer.  If you're missing a dependency, it'll tell you the name, then you can install that dependendency first (also a .deb which you double click).

---

### Post by 7mm on 2007-01-01
> **macogw said:**
> If you downloaded a .deb, just put it on your desktop and double click.  It'll run the installer.  If you're missing a dependency, it'll tell you the name, then you can install that dependendency first (also a .deb which you double click).

No, Bro. It's Not ( .deb ) File. It's a Compressed File & Contains 9 Folder & 40 Files, Including ( install-sh ). Now Show Me How Do I Get This Thing To Work. Please Help!

---

### Post by 7mm on 2007-01-03
I've Tried To Run File ( INSTALL ) & ( install-sh ) using ( ./ ) Command, But It Shows Me ( Permission Denied ) Error. May Be I Need To Switch To Root. ](*,)  But How? Just Help Me With This One Guys.

---

### Post by 7mm on 2007-01-04
:confused:  Please Help Here People, NewBie Desperately Needs Help.

---

### Post by darrenm on 2007-01-04
Try

```
sudo ./install.sh
```

---

### Post by 7mm on 2007-01-05
Thank You "darrenm" For Your Reply & It's Very Helpful Though. But My Problem Remains. GnuCash Don't Have ( ./install.sh )File. It Has ( install-sh )File.

Error With (install-sh) => ./install-sh: no input file specified.

Error With (INSALL)   => bash: ./INSTALL: Permission denied

                                 => sudo: ./INSTALL: command not found

Can Any One Help!

---

### Post by pebo on 2007-01-05
You may find installation instructions in the INSTALL file so open it in a text editor.
Without having the download on my box I can't give specific instructions but there should be installation documentation included in README or INSTALL files

---

### Post by 7mm on 2007-01-05
Le'me See.........:-k

---

### Post by 7mm on 2007-01-08
Wel After All The Waiting & Discussing With Visited Community Members, I've got My Self GnuCash Running. Thank You "xopher" & "Sef" Who's Commandline Instruction Help Me (Windows User, NewBie Linux User) Big There.

Thank You People Who've Contributed & Helped Me Most To Solve My Problem.

---

### Post by 7mm on 2007-01-08
**Thread Ends Here, See Yaa & Take Care.**

---

