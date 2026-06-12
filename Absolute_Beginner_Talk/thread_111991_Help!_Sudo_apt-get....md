---
title: "Help! Sudo apt-get..."
date: 2006-01-03
forum: Absolute Beginner Talk
---

### Post by Dr Von Bon Bon on 2006-01-03
Hello, 

I recently installed Lilypond-data in order to use Lilypond and it has absolutley killed my computer.

I cannot install anything else because as I go to it comes up with "preparing Lilypond-data" and then the installation just stops.

Trying to remove it with synaptic just causes it to crash and burn.

And I get this when I try and remove it using sudo-apt remove:

```
god@Callum:~$ sudo apt-get remove lilypond-data
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  lilypond-data
0 upgraded, 0 newly installed, 1 to remove and 19 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 15.4MB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing lilypond-data (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
god@Callum:~$ Errors were encountered while processing:
 lilypond-data

```


And before anyone suggests reinstalling it I have done that about twenty times.

Please Help.

---

### Post by sapo on 2006-01-03
Did you try to **sudo apt-get install -f lilypond-data** and after it use the sudo apt-get remove?

---

### Post by Dr Von Bon Bon on 2006-01-03
I just tried that, it said I already had the newest version installed and then the same thing happened when I tried to install it.

---

### Post by estel on 2006-01-03
Can you clear the package cache (or at least delete that package)?

---

### Post by Dr Von Bon Bon on 2006-01-05
How do I do that then please?

---

### Post by carlosqueso on 2006-01-05
to clear the package cache ```
sudo apt-get clean
``` I'm not sure that'll work though.  You might also want to try ```
dpkg -r lilypond-data
``` and see if it works.

---

### Post by Dr Von Bon Bon on 2006-01-05
The clean command didn't do anything and this error came up with the dpkg one:

```
god@Callum:~$ sudo dpkg -r lilypond-data
dpkg: error processing lilypond-data (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 lilypond-data

```

This is the error that will lead me back into a circle of pain.

Has anyone got any ideas please?

---

### Post by carlosqueso on 2006-01-05
try using ```
dpkg -r --force-remove-reinstreq
```  I'm not sure the consequences that this will have for your system...but apt, synaptic and dpkg should work properly afterward. NOTE: I've never done this (found it in dpkg's man page) so YMMV.

---

### Post by Dr Von Bon Bon on 2006-01-05
I tried that and it said:


```
god@Callum:~$ sudo dpkg -r --force-remove-reinstreq lilypond-data
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 92983 files and directories currently installed.)
Removing lilypond-data ...
/var/lib/dpkg/info/lilypond-data.postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: error processing lilypond-data (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 lilypond-data

```

---

### Post by carlosqueso on 2006-01-05
okay.....I think I have one more thing that we can try...but I'm not sure exactly how it works, so we're gonna do this carefully as to not break your computer any worse.  Type ```
cat /var/lib/dpkg/status | grep -A 9 lilypond-data > lilypond.txt
gedit lilypond.txt 
``` and post the contents of that file here.  This should output information about the lilypond-data package to a file called lilypond.txt and should be perfectly safe.  This should give me enough information to help you with the next part.

---

### Post by Dr Von Bon Bon on 2006-01-06
Okay, it came up as this

Package: lilypond-data
Status: deinstall reinstreq half-installed
Priority: optional
Section: tex
Installed-Size: 15064
Maintainer: Thomas Bushnell, BSG <tb@debian.org>
Architecture: all
Source: lilypond
Version: 2.6.3-9~breezy1
Depends: texinfo | texlive-texinfo
--
 /etc/emacs/site-start.d/50lilypond-data.el 3e7ecb26ca084ca1b37e75dc051aaeaf
Description: LilyPond music typesetter (data files)
 LilyPond is a music typesetter, an automated engraving system.  It
 produces beautiful sheet music using a high level description file as input.
 .
 This package contains architecture-independent data files for LilyPond.

Package: kblackbox
Status: deinstall ok config-files
Priority: optional
--
Replaces: lilypond (<= 2.2.3-1), lilypond-data (<= 2.2.3-1)
Suggests: lilypond (>= 2.6.3-9~breezy1), gv | postscript-viewer, mozilla-browser | www-browser
Description: LilyPond Documentation in HTML, PS and DVI formats
 This package contains the HTML, PostScript and DVI documentation for the
 LilyPond music typesetting software.

Package: bluez-utils
Status: install ok installed
Priority: optional
Section: admin




Is that what you wanted?

---

### Post by carlosqueso on 2006-01-06
Okay....we're in business....First, change to the /var/lib/dpkg/status, and backup your /var/lib/dpkg/status file. (If you need more help with this, let me know).  Then open up the file as sudo with your favorite text editor, search for the lilypond-data package, and replace ```
Status: deinstall reinstreq half-installed
``` with ```
Status: deinstall hold half-installed
``` which should tell dpkg to ignore this package altogether.   Please post back your results.

---

### Post by Dr Von Bon Bon on 2006-01-06
could you please tell me how to do the first two things please?


I think the first one is something like cd~/var/lib/dpkg/status 

but I have no idea how to do the second bit.

Sorry :(

---

### Post by carlosqueso on 2006-01-06
No problem...just type the following into a terminal.

```
cd /var/lib/dpkg/
sudo cp status status_bkup
sudo gedit status
```

You should then be able to use the find feature of gedit (probably edit-> or ctrl+f, I use mousepad) to find lilypond and replace the line I showed you.  I'm gonna be away from my computer for a while, but if you post back, I'll try to look in on you tonight or tommorow morning/early afternoon (Eastern Standard Time), and help more.

---

### Post by Dr Von Bon Bon on 2006-01-07
Okay, I did that and then tried to upgrade all of the things that need updating (According to synaptic) and this happened:


E: /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb: subprocess new post-removal script returned error exit status 1

W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)


I have no idea what most of that is apart from the lilypond thing and it's still trying to install for some messed up reason.



EDIT:

In synaptic it's marked for deinstallation and still tries to prepare it

---

### Post by carlosqueso on 2006-01-07
Grr.....I'm out of ideas about lilypond unless there is a way you can unmark lilypond in synaptic or completely delete it from the status file (althought that may break your system). However, the output from synaptic that you posted has nothing to do with it.  That means that it can't find the planetmirror repositories that you're using.  [http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672) is a reccomend sources.list file.   If you need help installing it, post back and I'll try to help.

---

### Post by Greg2 on 2006-01-07
[QUOTE=Dr Von Bon Bon]I have no idea what most of that is apart from the lilypond thing and it's still trying to install for some messed up reason.[/QUOTE]
I answered this in your other thread, but here it is again…

This is a known bug in the Synaptic package manager. It requires a clean environment with no half installed packages to perform any additional changes.

In a terminal do:```
sudo apt-get install -f
```
Then remove Lilypond-data with the Synaptic package manager.

---

### Post by nalmeth on 2006-01-07
I'm sorry, but isn't it:

sudo apt-get -f install

??

I remember running into this problem before myself. I was installing some kind of tab sheet program, and it totally screwed me over too. I might have eventually fixed it, but odds are I reinstalled. Don't assume you'll have to do this, but I remember it being a real pain.

EDIT: It was the lilypond package specifically aswell. Anyone know what the deal is here?

---

### Post by Greg2 on 2006-01-07
[QUOTE=nalmeth]I'm sorry, but isn't it:

sudo apt-get -f install[/QUOTE]
No, it&#8217;s ```
sudo apt-get install &#8211;f
``` will fix the package manager&#8230; as per the Synaptic manual.

I believe there is a problem with the lilypond-data package imho, that&#8217;s how I know this fix.:)

Edit: For the record I just checked bugzilla.ubuntu and there has been a bug report made, bug #21676

---

### Post by Dr Von Bon Bon on 2006-01-08
I tried doing the sudo apt-get install -f and it came up with this error:


E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory


Ummm, what do I do please?


Thanks loads everyone, especially carlosqueso for all his help.

---

### Post by Greg2 on 2006-01-08
[QUOTE=Dr Von Bon Bon]I tried doing the sudo apt-get install -f and it came up with this error:


E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory[/QUOTE]
It sounds like you have your package manager open? If you do close it, and try the command from your terminal again.

---

### Post by Dr Von Bon Bon on 2006-01-08
It's not installing.

It keeps going:

```
god@Callum:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  lilypond-data
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
10 not fully installed or removed.
Need to get 0B of archives.
After unpacking 15.4MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 93126 files and directories currently installed.)
Removing lilypond-data ...
/var/lib/dpkg/info/lilypond-data.postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: error processing lilypond-data (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 lilypond-data
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://packages.freecontrib.org breezy/free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://packages.freecontrib.org breezy/non-free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://packages.freecontrib.org breezy/free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://packages.freecontrib.org breezy/non-free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


Please help.
Thanks

---

### Post by Greg2 on 2006-01-08
[QUOTE=Dr Von Bon Bon]It's not installing.

It keeps going:

```
god@Callum:~$ sudo apt-get install -f
Password:
-snip-
Removing lilypond-data ...
/var/lib/dpkg/info/lilypond-data.postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: error processing lilypond-data (--remove):
 subprocess post-removal script returned error exit status 1
-snip-

```
[/QUOTE]
Now we can fix this. Open your text editor and save a blank file named kpsewhich in your /home directory. Then with terminal do:```
sudo cp -f kpsewhich /usr/bin
```

Now run the ```
sudo apt-get install -f
``` and you will probably have another missing file. Do the same thing and create an empty file with the missing name and cp to wherever, then try again with ```
sudo apt-get install -f
```

I know this sounds strange… but it works!:smile:

---

### Post by Dr Von Bon Bon on 2006-01-08
Okay, I did that but it hasn't come up with anymore missing files, instead:


```
god@Callum:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  lilypond-data
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
10 not fully installed or removed.
Need to get 0B of archives.
After unpacking 15.4MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 93126 files and directories currently installed.)
Removing lilypond-data ...
/var/lib/dpkg/info/lilypond-data.postrm: line 23: /usr/bin/kpsewhich: Permission denied
dpkg: error processing lilypond-data (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 lilypond-data
E: Sub-process /usr/bin/dpkg returned an error code (1)
god@Callum:~$

```


Do you have any ideas?
Sorry to be a hassle but I am incredibly grateful for your help.

---

### Post by Greg2 on 2006-01-08
OK… do:
```
 sudo chmod 777 /usr/bin/kpsewhich
``` and try again

---

### Post by Dr Von Bon Bon on 2006-01-08
Oh thank God.


Thant worked. Thanks so very very much. I've been struggling with this for about a month now (ive had UBuntu for about a month and a day)


Thank very much again.
YOu rule.
Thanks.

---

### Post by compuguy1088 on 2006-03-19
WOOT! This worked! I've been going through multiple guides to get rid of this evil deb file :mrgreen:

---

### Post by x0inx on 2006-04-09
You rock!!! this file has been pissing me off for about 2 hours.

---

### Post by MrNamjama on 2006-04-22
I had the same problem - thank you

---

### Post by [censored] on 2006-05-05
Man, someone should either remove lilypond-data from the ubuntu repositories, or put up an official HOWTO on how to fix this problem.

Here's my howto:

> 
$cd /usr/bin
$sudo touch kpsewhich
$sudo chmod 777 kpsewhich
$sudo apt-get install -f


---

### Post by ubu_dynamite on 2006-05-17
sudo touch /usr/bin/kpsewhich
sudo chmod 777 /usr/bin/kpsewhich

sudo apt-get remove lilypond-data

sudo rm /usr/bin/kpsewhich

Workt for me.

---

### Post by Coburn on 2006-05-24
This also worked for me; however, I had to repeat the fake-file process with /usr/bin/mktexlsr.

Making sure you have run apt-get update first, instead of assuming you have everything downloaded already, as I did, will save you time :)

I am so going to ask at lilypond.org if these files affect anything.

---

### Post by Coburn on 2006-05-24
Bad news.  There are two sorts of dependencies for Lilypond.  One is for install, the other for run.  The stats on the run packages don't look good.

Specifically, we apparently need higher versions of Pango and Guile, unnamed Python packages, and Ghostscript, which doesn't show in my repositories at first glance.

Edit:  manually downloaded said versions from debian.org/pool/main, except Ghostscript.  Also apt-got tetex from ubuntu, which lilypond seems to require.  Tried a tutorial and it seems to run anyway.  Haven't tried to delete it yet :)

---

