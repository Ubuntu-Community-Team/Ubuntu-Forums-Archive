---
title: "Problem installing VLC and Codecs"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by evandec on 2007-03-08
I am trying to install some software and I get this. What gives. 

```
evandec@Ubuntu-Laptop:~$ sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdcss2 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mozilla-plugin-vlc: Depends: vlc-nox (= 0.8.6-svn20061012.debian-1ubuntu1.1) but it is not going to be installed
                      Depends: libvlc0 (>= 0.8.6-svn20061012.debian) but it is not going to be installed
  vlc: Depends: vlc-nox (= 0.8.6-svn20061012.debian-1ubuntu1.1) but it is not going to be installed
       Depends: libiso9660-4 but it is not installable
       Depends: libtar but it is not installable
       Depends: libvcdinfo0 (> 0.7.23) but it is not installable
       Depends: libvlc0 (>= 0.8.6-svn20061012.debian) but it is not going to be installed
       Depends: libxosd2 (>= 2.2.13) but it is not installable
  vlc-plugin-esd: Depends: vlc-nox but it is not going to be installed
                  Depends: libvlc0 (>= 0.8.6-svn20061012.debian) but it is not going to be installed
E: Broken packages
evandec@Ubuntu-Laptop:~$ 
```

---

### Post by benfindlay on 2007-03-08
try typing
```
sudo apt-get -f install
```

If that doesn't solve it, I would suggest just trying ```
sudo apt-get install vlc
```

Thats all I ever do and vlc seems to play everything for me!

---

### Post by evandec on 2007-03-08
Did both things and all i got was this. 


```
evandec@Ubuntu-Laptop:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: vlc-nox (= 0.8.6-svn20061012.debian-1ubuntu1.1) but it is not going to be installed
       Depends: libiso9660-4 but it is not installable
       Depends: libtar but it is not installable
       Depends: libvcdinfo0 (> 0.7.23) but it is not installable
       Depends: libvlc0 (>= 0.8.6-svn20061012.debian) but it is not going to be installed
       Depends: libxosd2 (>= 2.2.13) but it is not installable
E: Broken packages

```

---

### Post by benfindlay on 2007-03-08
Did ```
sudo apt-get -f install
``` give you any options?

You could also try typing ```
sudo apt-get remove vlc vlc-plugin-esd mozilla-plugin-vlc libdvdcss2
```

Looking at the log generated, it looks like it is trying to install vlc 0.8.6, which I believe is new out. May well still have some teething problems with it, as last time I installed vlc using > sudo apt-get install vlc (rather than what was suggested on their website) it was version 0.8.4

I am assuming you used the instructions on their site and added the repository? If so did you type ```
sudo apt-get update
``` before attempting to install vlc et al?

---

### Post by evandec on 2007-03-08
```
sudo apt-get -f install
```

Ran that and got this

```
evandec@Ubuntu-Laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up flashplugin-nonfree (9.0.21.78~ubuntu1~edgy1) ...
Downloading... download failed
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
evandec@Ubuntu-Laptop:~$ 

```


```
sudo apt-get remove vlc vlc-plugin-esd mozilla-plugin-vlc libdvdcss2
```

Ran that and got this

```
evandec@Ubuntu-Laptop:~$ sudo apt-get remove vlc vlc-plugin-esd mozilla-plugin-vlc libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package vlc is not installed, so not removed
Package vlc-plugin-esd is not installed, so not removed
Package mozilla-plugin-vlc is not installed, so not removed
Package libdvdcss2 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up flashplugin-nonfree (9.0.21.78~ubuntu1~edgy1) ...
Downloading... download failed
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
evandec@Ubuntu-Laptop:~$ 

```


I did add everything to the repositories and updated and upgraded. 

I feel like it is hanging on this flash plugin but i dont know why.

---

### Post by benfindlay on 2007-03-08
Looks like this is your problem to me:
> Errors were encountered while processing:
 flashplugin-nonfree

Have you been using automatix by any chance? If so I would recommend removing the flashplugin stuff you installed through it

If not, I'm grasping at straws here as still not THAT versed in the subtleties of terminal code, but since its a dpkg error, you could try typing
```
sudo dpkg-reconfigure flashplugin-nonfree
```
and see what happens (or see if it generates anything of note!

Hope this helps!

EDIT: it also says > dpkg: error processing flashplugin-nonfree (--configure):

you could also try

```
sudo dpkg flashplugin-nonfree --configure
```
or
```
sudo dpkg --configure flashplugin-nonfree
```

or ```
sudo dpkg -P flashplugin-nonfree
```

---

### Post by evandec on 2007-03-08
Still nothing. I tried to use automatix but I cant because it says some keys still not downloaded. What might that mean?

---

### Post by benfindlay on 2007-03-08
Think automatix is down currently, so thats probably the reason thats not working.

Sorry, can't really thing of anything else. It seems like it doesn't like the flash plugin, might be worth looking for the proper command to either configure, re-configure or remove it. THen you might have more joy. Afraid I'm not entirely sure of that command myself!

Sorry can't be of more help

---

### Post by Drenhead on 2007-03-10
I'm getting the same errors as the original poster.  I'd appreciate it if you could let me know if you get it to work.

Thanks in advance.

---

