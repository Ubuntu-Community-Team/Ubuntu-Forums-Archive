---
title: "Installing programs"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by blithen on 2007-07-05
When I go to Add/Remove programs, I check the ones I want, and it downloads them fine. But it doesn't install them. Where do they download to. And if possible how do I turn it on to where it just installs right after downloading.

---

### Post by Vajra Vrtti on 2007-07-05
What do you mean by "it doesn't install them"?
You get error messages or just can't find them?
What programs are you trying to install?

---

### Post by blithen on 2007-07-05
The weird thing is there is no error message, it just goes from downloading then a quick flash, then back to loading the list of programs. I was trying to install XChat. And also some updates.

---

### Post by Nekiruhs on 2007-07-05
Try using Synaptic (System > Administration > Package Manager ) or the good ol' fashion command line sudo apt-get install programname. If those don't work, something is wrong with APT and thats alot more serious.
btw for xchat its ```
sudo apt-get install xchat
```

---

### Post by blithen on 2007-07-05
> **Nekiruhs said:**
> Try using Synaptic (System > Administration > Package Manager ) or the good ol' fashion command line sudo apt-get install programname. If those don't work, something is wrong with APT and thats alot more serious.
btw for xchat its ```
sudo apt-get install xchat
```

```
dpkg: parse error, in file `/var/lib/dpkg/available' near line 18299:
 missing package name
E: Sub-process /usr/bin/dpkg returned an error code (2)
blithen@blithen-desktop:~$
``` 

That's the error I got when I tried installing xchat.
I also did it with Banshee, and the same thing came up.

---

### Post by NeoLithium on 2007-07-05
sometimes they don't show up instantly in the gnome menu.  It's happened more than once for a few different things, usually after a reboot, restarting gnome panel or restarting dbus it works for me; and they're there.  Though it also does depend on the programs.

---

### Post by Nekiruhs on 2007-07-05
> **blithen said:**
> dpkg: parse error, in file `/var/lib/dpkg/available' near line 18299:
 missing package name
E: Sub-process /usr/bin/dpkg returned an error code (2)
blithen@blithen-desktop:~$ 

That's the error I got when I tried installing xchat.
:( Not good. Apparently your list of availible packages (thats what i think it is) is malformed at line 18299. Does just Xchat not install, or can you not install anything?

---

### Post by blithen on 2007-07-05
T__T I Can't install anything. Including updates...

---

### Post by NeoLithium on 2007-07-05
Ok, can you try:
```

sudo apt-get clean
then
sudo apt-get update

```
Along with any error messages, as well as posting the contents of this command in terminal:
```
cat /etc/apt/sources.list
```

---

### Post by blithen on 2007-07-05
So...I got no errors, that is obviously good. So do you still want me to post the contents of that list?
but I tried installing xchat again, and the same error popped up.

---

### Post by blithen on 2007-07-05
here is the contents of that sources list.

```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb http://archive.ubuntu.com/ubuntu/ feisty-backports restricted main multiverse universe

```

---

### Post by Nekiruhs on 2007-07-05
Could you post the file /var/lib/dpkg/available here as an attachement. I will try and go through it to find the issue. 
```
tar -cvvzf ~/Desktop/available.tar.gz /var/lib/dpkg/available
```
And just upload that file as an attachment. I'll try and have a look at line 18299.

---

### Post by blithen on 2007-07-05
And just encase I missed something, here is when I tried the sudo thing

```

blithen@blithen-desktop:~$ sudo apt-get clean
blithen@blithen-desktop:~$ sudo apt-get update
Get:1 http://archive.ubuntu.com feisty-backports Release.gpg [191B]
Ign http://archive.ubuntu.com feisty-backports/restricted Translation-en_US
Get:2 http://security.ubuntu.com feisty-security Release.gpg [191B]  
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Get:3 http://us.archive.ubuntu.com feisty Release.gpg [191B]         
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US              
Ign http://archive.ubuntu.com feisty-backports/main Translation-en_US
Ign http://archive.ubuntu.com feisty-backports/multiverse Translation-en_US
Ign http://archive.ubuntu.com feisty-backports/universe Translation-en_US
Hit http://archive.ubuntu.com feisty-backports Release               
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com feisty-security Release
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US  
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Get:4 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Hit http://archive.ubuntu.com feisty-backports/restricted Packages  
Hit http://us.archive.ubuntu.com feisty Release
Hit http://security.ubuntu.com feisty-security/main Packages                   
Hit http://us.archive.ubuntu.com feisty-updates Release              
Hit http://archive.ubuntu.com feisty-backports/main Packages                   
Hit http://archive.ubuntu.com feisty-backports/multiverse Packages   
Hit http://archive.ubuntu.com feisty-backports/universe Packages     
Hit http://security.ubuntu.com feisty-security/restricted Packages   
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://us.archive.ubuntu.com feisty/main Packages
Hit http://us.archive.ubuntu.com feisty/restricted Packages
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty/multiverse Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Fetched 4B in 1s (4B/s)  
Reading package lists... Done

```

---

### Post by blithen on 2007-07-05
There it is.

---

### Post by Nekiruhs on 2007-07-05
Heres my Lin 18299 of my /var/lib/dpkg/available 
```
Installed-Size: 124
```
Post your file as an attachement.

---

### Post by RomeReactor on 2007-07-05
Hi. Sorry to intrude. This is the first time I've seen this file, so I can't really comment anything useful. However, taking a look at your file, it seems to me the problem might be this entry, just above line 18289:
```
Packagå: language-pack=my
Priority: optional
Section: ýranslations
Insíalled-Size: 36
Taintainer: Martyn Pitt <martin.àitt@ubuntu.com>Architecture: a|l
Version: 1:7.±4+20070412
Replùces: language-pàck-my-base, lanöuage-pack-my-baje (<< 1:7.04+20 70412), languagõ-pack-gnome-my-êase (<< 1:7.04+¢0070412), languðge-pack-kde-my-ûase (<< 1:7.04+20070412), languhge-pack-my (<< !:7.04+20070412)Depends: language-pack-my-base
Pre-Depends: dpkg (>= 1.10.27ubuntu1)
Size: 2060
Description: translation updates for language Burmese
 Translation data updates for all supported packages for:
 Burmese
 .
 language-pack-my-base provides the bulk of translation data
 and is updated only seldom. This package provides frequent translation
 updates.
 .
 Please note that you should install language-support-my
 to get full support for this language.
```
The rest of the file appears to be in English, but this entry has characters that seem to be related to the Burmese language (see package description).

**EDIT**: Upon closer inspection, some entries appear to be corrupted. If no one else offers a better solution, I would suggest **completely removing** the packages **language-pack-my** and **language-pack-my-base** and **then re-install them**. Maybe this could correct the entries, but as I said, I really don't know much about this particular file.

---

### Post by blithen on 2007-07-05
Oh crap >>;; What do you suggest I do?

---

### Post by blithen on 2007-07-05
Before I do the whole uninstall thing I want to get a few other opinions first. Considering I can't install anything at the moment.

---

### Post by blithen on 2007-07-05
Anyone got any ideas?

---

### Post by Vajra Vrtti on 2007-07-06
I agree with RomeReactor suggestion. I would delete those corrupted entries.

---

### Post by RomeReactor on 2007-07-06
I agree,  you should wait until someone with experience regarding this file suggests a solution. Just in case, I took the liberty of modifying your **available** file (the one you posted) and corrected the entries I noticed were corrupted (according to their entries in Synaptic); I'm uplouding the modified file, and, should you choose to do so, you can replace your existing file with this one; just download it to your home folder (or move it there after download), unpack it, and enter this in the terminal:
```
sudo cp available /var/lib/dpkg/available
```
remember this modified file **must** be in your home folder; after that, enter:
```
sudo apt-get update
```
and try to install something either through Add/Remove or Synaptic.

---

### Post by blithen on 2007-07-06
Thanks for the try man, it didn't work though...

---

### Post by blithen on 2007-07-06
Are you sure you did everything correctly?

---

### Post by RomeReactor on 2007-07-06
I corrected one of the entries according to my own **/var/lib/dpkg/available** file; the other one, according to the package information Synaptic gave me. I wasn't very thorough; it's a big file, after all. I only corrected the ones that were near line 18289. There could be more. Did you extract the file from the archive before entering the commands I suggested? did you right-click on the file and select "Extract here", and if so, did it extract as a folder (upon extraction, only the text file should be on your home folder: **/home/YOUR_USER_NAME/available**).

---

### Post by blithen on 2007-07-06
I did everything you said. but we might be getting some with this new error xD

```
dpkg: parse error, in file `/var/lib/dpkg/available' near line 9627 package `language-pack-my':
 `Replaces' field, syntax error after reference to package `language-pack-my-base'
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by RomeReactor on 2007-07-06
I think this is the line:
> Replaces: language-pack-gnome-my-base, language-pack-my-base (<< 1:7.04+20070412), language-pack-gnome-my-base (<< 1:7.04+20070412), language-pack-kde-my-base (<< 1:7.04+20070412), language-pack-my (<< 1:7.04+20070412)
I think you need to remove this part:
> Replaces: **language-pack-gnome-my-base,** language-pack-my-base (<< 1:7.04+20070412), language-pack-gnome-my-base (<< 1:7.04+20070412), language-pack-kde-my-base (<< 1:7.04+20070412), language-pack-my (<< 1:7.04+20070412)
so the line ends up like this:
> Replaces: language-pack-my-base (<< 1:7.04+20070412), language-pack-gnome-my-base (<< 1:7.04+20070412), language-pack-kde-my-base (<< 1:7.04+20070412), language-pack-my (<< 1:7.04+20070412)
To edit the file, enter this in the terminal:
```
gksudo gedit /var/lib/dpkg/available
```
and go to **Search->Go to Line...->9627**.

---

### Post by blithen on 2007-07-06
gedit doesn't open. I'm using GNome.

---

### Post by Nekiruhs on 2007-07-06
Ok. here is my very default file Blithen.
Just extract it to your home folder and run the command that RomeReactor told you to 
( sudo cp ~/available /var/lib/dpkg/available ) without the ( )

---

### Post by blithen on 2007-07-06
It worked!!! Thanks a lot!

---

