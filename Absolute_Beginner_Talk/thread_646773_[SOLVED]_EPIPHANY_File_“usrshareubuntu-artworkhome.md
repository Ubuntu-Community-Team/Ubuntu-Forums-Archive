---
title: "[SOLVED] EPIPHANY File “/usr/share/ubuntu-artwork/home/locales/index-C.html” not foun"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by beanco on 2007-12-21
I have been having firefox problems, [see this ](http://ubuntuforums.org/showthread.php?t=644874&highlight=robi)

so I wanted to try Epiphany to see if the problems occur in other browsers too...

when I open epiphany I get the

 ```
File “/usr/share/ubuntu-artwork/home/locales/index-C.html” not found.
```

or in terminal this

```
rob@rob-desktop:~$ epiphany 

(epiphany:29669): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(epiphany:29669): Gdk-WARNING **: locale not supported by C library
rob@rob-desktop:~$ 
```

Any idea how to get epiphany open?

Thanks

Robi

---

### Post by nowshining on 2007-12-21
did u uninstall the english translation language pack?

---

### Post by beanco on 2007-12-22
> **nowshining said:**
> did u uninstall the english translation language pack?

what's that? I do not know if I have installed it... Epiphany was working when I last installed ubuntu...

It just stopped. but since I was using firefox I did not really care about epiphany,, but that has changed.

robi

---

### Post by nowshining on 2007-12-22
system - administration - synaptic package manager

look for language pack and en

and yes en = english & if not installed - install it and re-try again and if not, report back.

---

### Post by bapoumba on 2007-12-22
Which locale are you using ?

---

### Post by beanco on 2007-12-22
thanks for the info. as soon as I have my net connection fully working I will try it. 

robi

---

### Post by nowshining on 2007-12-22
bapoumba's question can be answered without an internet connection on the machine.

---

### Post by bapoumba on 2007-12-22
> **nowshining said:**
> bapoumba's question can be answered without an internet connection on the machine.
Yes, sorry :)
```
cat /etc/environment
```

---

### Post by beanco on 2007-12-22
> **nowshining said:**
> bapoumba's question can be answered without an internet connection on the machine.

Well, I had not even seen bapoumba's question utnil I saw your msg Nowshining.

and Bpoumba, thanks for the code:

[PHP]rob@rob-desktop:~$ cat /etc/environment
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="en_US.UTF-8"
rob@rob-desktop:~$ 

[/PHP]

robi

---

### Post by nowshining on 2007-12-22
ur beanco looks fine to me. :) same as mine.

---

### Post by beanco on 2007-12-22
> **nowshining said:**
> ur beanco looks fine to me. :) same as mine.

Uh, OK but I still cannot get Epiphany to open....

[HTML]rob@rob-desktop:~$ epiphany

(epiphany:5846): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(epiphany:5846): Gdk-WARNING **: locale not supported by C library

[/HTML]


kind of annoying...

---

### Post by bapoumba on 2007-12-22
```
:~ $ cat /etc/environment 
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="en_US.UTF-8"
LANGUAGE="en_US:en"
```

Please go to System > Language Support (it may be a different menu with GNOME) and make sure you have the same thing as in the screenshot (not for the French part ;)). If some packages are missing, you will be prompted to install them.

---

### Post by beanco on 2007-12-22
great idea but this is what I get

[HTML]W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en-base/language-pack-en-base_7.04+20070412_all.deb
  Could not resolve 'archive.ubuntu.com'

[/HTML]

the list goes on to include everything that needs to be installed, fetched, whatever because I cannot access the internet  

[**[COLOR="Red"]take a look at this[/COLOR]**](http://ubuntuforums.org/showthread.php?t=644874&highlight=rob)


so what the heck can I do?

robi

---

### Post by bapoumba on 2007-12-23
Okay, I'll check your other problem, you need to fix net access first, and then we can continue here.

---

### Post by beanco on 2007-12-23
> **bapoumba said:**
> ```
:~ $ cat /etc/environment 
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="en_US.UTF-8"
LANGUAGE="en_US:en"
```

Please go to System > Language Support (it may be a different menu with GNOME) and make sure you have the same thing as in the screenshot (not for the French part ;)). If some packages are missing, you will be prompted to install them.

I just did this, ok I have not actually rebooted because I have other things going on that I cannot interrupt... but it did not help...

I will try epiphany agina after I reboot.

thanks again for all you help.

robi

---

### Post by bapoumba on 2007-12-23
Please post your sources.list:
```
cat /etc/apt/sources.list
```

---

### Post by beanco on 2007-12-23
here you go... kind of long

```
rob@rob-desktop:~$ cat /etc/apt/sources.list
## Uncomment the following two lines to fetch updated software from the network
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb http://archive.ubuntu.com/ubuntu feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu feisty universe
deb-src http://archive.ubuntu.com/ubuntu feisty universe

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted

deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe

deb http://archive.ubuntu.com/ubuntu feisty multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty multiverse

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

rob@rob-desktop:~$ 

```

---

### Post by bapoumba on 2007-12-23
The sources.list is fine (I would just comment out the cdrom and the backports, but that's a detail).

```
cat /var/lib/locales/supported.d/local
```

Here is mine, with both French and English locales:
```
isabella@yeti:~ $ cat /var/lib/locales/supported.d/local
fr_FR.UTF-8 UTF-8
en_US.UTF-8 UTF-8
```

Which language are you using? 
If using Hungarian, you should have also:
```
hu_HU.UTF-8 UTF-8
```

You can add it to the **/var/lib/locales/supported.d/local** file, and then run:

```
sudo locale-gen
```

---

### Post by beanco on 2007-12-23
I will try your suggestions later on.

as to Hungarian. well I never actualy use it... 

Just what is the locale stuff that I am going to be setting anyway?

Robi

---

### Post by nowshining on 2007-12-23
> **beanco said:**
> I will try your suggestions later on.

as to Hungarian. well I never actualy use it... 

Just what is the locale stuff that I am going to be setting anyway?

Robi
lolz

beanco u using english US i guess eh! :)

locale = language = ur local language

lets other programs know what language and the OS what language ur using, some progs need em' set exactly right..

---

### Post by beanco on 2007-12-24
well, I am using English!

Ok I have to be able to read Hungarian texts so I can translate them into English and on the rare occasion write stuff in Hungarian but that is just keyboard layout related, right?

robi

---

### Post by bapoumba on 2007-12-24
I'm using English environment too. This was just a suggestion, as there is nothing I could ind directly related to the errors you are getting.

One idea would be to make a new user (**sudo adduser <whatever login>**) and see if it happens too. If not, we can look to your regular user config files.

---

### Post by beanco on 2007-12-24
I created two new users


beanco, using system/user groups

and beanco2 using  sudo adduser

I was curious if there would be a difference.

The onyl difference was that beanco2 did not have any sound.

Neither could open epiphany.

and, ys, I rebooted, then tried them out.

robi

---

### Post by bapoumba on 2007-12-24
Hmm, so this either means a global settings problem (do you have similar issues with other applications ?) or a problem with epiphany.

Regarding epiphany, it is not a config problem. A new user has default config. Could be something lying in gconf, or within epiphany setup itself.

Please try to completely purge epiphany and reinstall it. You can use synaptic --> choose "Mark for complete removal" in the package menu or with apt-get or aptitude if you are used to these package managers (purge option).

```
sudo aptitude (or apt-get) remove --purge epiphany-browser
```

---

### Post by beanco on 2007-12-26
I removed and installed it twice at the command line and i still get that stupid msg....

what could I be doing wrong?


thanks

robi

---

### Post by bapoumba on 2007-12-26
Hmm, I went back to your first post and looked at the missing file. Does no make much sense to me. Please keep in mind I'm using xubuntu. I've attached the file, it is just a plain welcome message. I'll try to get one from GNOME (my son's using GNOME).
Edit: the upload did not work, trying something else.
Edit2: in the attached tarball.

---

### Post by beanco on 2007-12-26
I updated again Ubuntu and then reinstalled epiphany and now it works!!

I am typing in it now!!!

Thanks for you help!!

Robi

---

### Post by nowshining on 2007-12-27
i'm happy u got ur problem fixed, congrats my friend.

---

### Post by bapoumba on 2007-12-28
+1 :)

---

### Post by beanco on 2007-12-28
i am happy this place is so friendly and helpful.

I am currently at friends and they only have windows whatever.. ti is not fun

robi

---

