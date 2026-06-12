---
title: "Unable to install any packages"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by vivin_west on 2006-12-08
Can any one help me fix this error. I am unable to instal a JRE package 

E: Malformed line 31 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
root@vivin-desktop:/home/vivin# sudo gedit etc/apt/sources.list

(gedit:18065): Gdk-WARNING **: locale not supported by Xlib

(gedit:18065): Gdk-WARNING **: cannot set locale modifiers

(gedit:18065): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by hotbrainz on 2006-12-08
type this in the terminal 

gksudo gedit /etc/apt/sources.list

and post it here

---

### Post by vivin_west on 2006-12-08
vivin@vivin-desktop:~$ gksudo gedit etc/apt/sources.list

(gksudo:18345): Gdk-WARNING **: locale not supported by Xlib

(gksudo:18345): Gdk-WARNING **: cannot set locale modifiers

** (gksudo:18345): WARNING **: Owner of /tmp/orbit-vivinzdauser is not the current user

(gedit:18346): Gdk-WARNING **: locale not supported by Xlib

(gedit:18346): Gdk-WARNING **: cannot set locale modifiers

(gedit:18346): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
vivin@vivin-desktop:~$


Please tell me what is happening

---

### Post by hotbrainz on 2006-12-08
Could you please open the "Synaptic package manager" and get the list of sources. I found this relevant thread which mite help

[http://ubuntuforums.org/showthread.php?t=173489]("http://ubuntuforums.org/showthread.php?t=173489")

---

### Post by vivin_west on 2006-12-08
I get this error when I open synaptic

E: Malformed line 31 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

I want to know how to go to the repository list

---

### Post by mcduck on 2006-12-08
> **vivin_west said:**
> vivin@vivin-desktop:~$ gksudo gedit etc/apt/sources.list

Please tell me what is happening

It should be 'gksudo gedit /etc/apt/sources.list', with a slash before etc ;)

---

### Post by burek on 2006-12-08
what gives you ?
```
lsb_release -a 
```
 
read your distro name
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list-backup
 
```
  
then if you have edgy
```
cd /etc/apt/
wget http://patrick295767.sitesled.com/miniram/sources.list-edgy
sudo cp sources.list-edgy sources.list
sudo apt-get update
sudo dpkg --configure -a
sudo apt-get -f -y install
sudo apt-get -f -y install gedit 

```
in case you have other distro, you can replace edgy by dapper for dapper

---

