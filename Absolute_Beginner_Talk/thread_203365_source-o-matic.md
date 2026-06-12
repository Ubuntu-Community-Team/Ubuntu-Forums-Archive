---
title: "source-o-matic"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by Arthur Millar on 2006-06-25
:-k 

im busy looking at the page generated after clicking the "give me a source.list" button

# Automatically generated sources.list
[COLOR="Yellow"]# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)[/COLOR]
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add - 

what do i do with this ??

---

### Post by gingermark on 2006-06-25
> 
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

Are you getting errors about missing keys (or unauthenticated repositories)?
If not, don't worry. If so, then do the commands given (in the terminal), but replace "KEY" with the numbers included for each repository within the file.

---

### Post by Arthur Millar on 2006-06-25
[QUOTE=gingermark]Are you getting errors about missing keys (or unauthenticated repositories)?
If not, don't worry. If so, then do the commands given (in the terminal), but replace "KEY" with the numbers included for each repository within the file.[/QUOTE]

i checked my source.list file and nothings changed im not sure what to do after i check all the package and source boxes i wanted 
when i click the give me source.list button i just get that bit of text in my first thread

---

### Post by gingermark on 2006-06-25
Pretty much everything in Linux is configured via text files. Sure, there are graphical interfaces for many things, but there are always the configuration files behind them.

The "Source-o-matic" produces a replacement "sources.list" file, which controls which repositories are looked at to get new and upgraded software.

Open up the terminal, and copy & paste the following:```
gksudo gedit /etc/apt/sources.list
``` and replace the contents with the "Source-o-matic" output.

Now save the file, and do ```
sudo apt-get update
```
You will now be able to use the new repositories (in Synaptic if you like). If you then get key / authentication errors do what I said in the previous post.

---

### Post by Arthur Millar on 2006-06-25
gingermark 
thanks again for the reply 
however source-o-matic only gives me 



---------------------------------------------------------------------------------------------------------
# Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multivers

------------------------------------------------------------------------------------------------------------

This !?!
i already know that these are the official repo's
and this is after checking all the boxes of unofficial repo's
why isnt source-o-matic giving me the rest of the addresses 
i have been adding and removing apt lines all day 
with the gedit in the terminal 
from other links off the net 
but for some strange reason none of my attempts will take  
please help 
could you possibly give me a source.list with 
Cipherfunk multimedia packages
Penguin Liberation Front
Bleeding edge wine packages

those are the only one i think i need afterall im using gnome 
so im not really intrested in the kde packages 
please please please

---

### Post by gingermark on 2006-06-25
# Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main

# Penguin Liberation Front (packages)
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) dapper free non-free

# Bleeding edge wine packages (packages)
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

---

### Post by Arthur Millar on 2006-06-25
thanks ill see if it works

---

### Post by Arthur Millar on 2006-06-25
this is what ive been looking at all day 

**Could not download all repository indexes**

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.


[http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-amd64/Packages.gz:](http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-amd64/Packages.gz:) 404 Not Found
[ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/dists/dapper/free/binary-amd64/Packages.gz:](ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/dists/dapper/free/binary-amd64/Packages.gz:) Unable to fetch file, server said 'Failed to open file.  '
[ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/dists/dapper/non-free/binary-amd64/Packages.gz:](ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/dists/dapper/non-free/binary-amd64/Packages.gz:) Unable to fetch file, server said 'Failed to open file.  '
[ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/main/binary-amd64/Packages.gz:](ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/main/binary-amd64/Packages.gz:) Unable to fetch file, server said 'No such file.  '

what is up with this 
help

---

### Post by Arthur Millar on 2006-06-25
so now i replace the keys Y/N

---

### Post by Arthur Millar on 2006-06-25
just found this as well ???



ImportError: could not import gtksourceview
Traceback (most recent call last):
  File "/usr/lib/gedit-2/plugins/modelines.py", line 24, in ?
    class ModelinePlugin(gedit.Plugin):
AttributeError: 'module' object has no attribute 'Plugin'

** (gedit:6759): WARNING **: Could not load python module modelines


** (gedit:6759): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN  (plugin)' failed

** (gedit:6759): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN  (plugin)' failed

** (gedit:6759): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN  (plugin)' failed

** (gedit:6759): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN  (plugin)' failed

** (gedit:6759): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN  (plugin)' failed

** (gedit:6759): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN  (plugin)' failed

** (gedit:6759): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN  (plugin)' failed

** (gedit:6759): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN  (plugin)' failed

** (gedit:6759): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN  (plugin)' failed

** (gedit:6759): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN  (plugin)' failed

** (gedit:6759): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN  (plugin)' failed

** (gedit:6759): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN  (plugin)' failed
artnlaw@HomePC:~$

---

### Post by gingermark on 2006-06-25
[QUOTE=Arthur Millar]so now i replace the keys Y/N[/QUOTE]

No the "Keys" are to do with making sure the repository is actually the one you think it is (ie for security), not related to this.

Have you tried typing "sudo apt-get update" after you change your sources.list? If that doesn't work, it looks like those repositories are temporarily down. EDIT: I can reach them fine, so they're not down.

---

### Post by Arthur Millar on 2006-06-25
ok 
so where els can i find the plugins i need to play a DVD?

---

### Post by gingermark on 2006-06-25
I have to say, I'm having trouble following you here.

If you want to install libdvdcss2 (which you need to play encrypted DVDs) then do
```
sudo apt-get install libdvdcss2
``` or use 'Synaptic Package Manager' to install it.

Apt-get or Synaptic will then look in the repositories listed in your sources.list file and then install it for you assuming it is available in one of those repositories (which it is - the PLF one).

Have a look at [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) for more info.

---

### Post by Arthur Millar on 2006-06-25
ok i kept a copy of my original source.list on the desktop 
"libdvdcss2" package doesnt come up in my search in synaptic  
what im trying to do is set my ubuntu (DD606)amd 64 to play multimedia 
my cds work fine but i would like my DVD's to work!
also i would like to brouse some other packages available to tweek my machine 
i still dont know which media player to use so i install gxine mplayer and totem movie player plaus all there pugins
well i suspect there are a bunch i need from other repo's 
so hence my dilema

---

### Post by Arthur Millar on 2006-06-25
artnlaw@HomePC:~$ _sudo apt-get install libdvdcss2_
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
artnlaw@HomePC:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
artnlaw@HomePC:~$

---

### Post by gingermark on 2006-06-25
Look at [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) for instructions.

In future please mention you are using the 64-bit version. There is no  64-bit version of the PLF repository, or of the WINE one, which is why you had problems.

You will struggle with some proprietary stuff, and have to play with chroots and other fun things I don't know about. I'd install the 32-bit version, and have your /home directory on a separate partition so when 64-bit matter improve you can just switch back.

You can achieve what you want on 64-bit, but as I understand it it is far more complicated.

---

### Post by Arthur Millar on 2006-06-25
im so sorry bout all the hassle for nothing thanks anyway ](*,) :-?

---

### Post by gingermark on 2006-06-25
Well hang on.

If you want to use the 64-bit version, then look at that link I gave for the 64-bit section. For DVD playback it says:
> The install-css.sh script will compile the libdvdcss2 library for you instead of downloading a prebuilt binary. Make sure you install the debhelper, build-essential and fakeroot packages first. Then issue the command 
sudo /usr/share/doc/libdvdread3/examples/install-css.sh

So install debhelper, build-essential and fakeroot by doing
```
sudo apt-get install debhelper build-essential fakeroot
```
and then do ```
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
```

---

### Post by Arthur Millar on 2006-06-25
Totem could not play 'dvd:///media/cdrom0'.
No URI handler implemented for "dvd".
should i try a different player \

---

### Post by Arthur Millar on 2006-06-25
mplyer works i havnt checked th sound yet
EDIT: why does mplayer only play one chapter then stop ?

---

