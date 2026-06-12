---
title: "problem with repositries"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by dead_man_walking on 2006-07-22
When i click the reload button in the synaptic package manager .. i get theese errors 

1.) cdrom:[Ubuntu 5.10 _dapper Badger_ - Release i386 (20051012)]/dists/dapper/main/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
cdrom:[Ubuntu 5.10 _dapper Badger_ - Release i386 (20051012)]/dists/dapper/restricted/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

2.) then i get this error :- W: Couldn't stat source package list cdrom://Ubuntu 5.10 _dapper Badger_ - Release i386 (20051012) dapper/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fdapper%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_dapper_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _dapper Badger_ - Release i386 (20051012) dapper/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fdapper%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_dapper_restricted_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by lowey23 on 2006-07-22
Hello again, deadman

From other posts in these forums, I seem to remember that you have upgraded to Dapper but still have the CD (Breezy) listed in your sources.list.

I hope these instructions are correct. Try this:-

In the terminal, put this line

gksudo gedit /etc/apt/sources.list

At the top, put a # in front of the line or lines that refer to your Breezy CD. That will stop your machine from looking to your CD for instal of apps. Everything without a # in front of it should refer to Dapper. If you have lines that start with deb.blah blah and have a # in front of them, remove the #.

Save and exit.

Then, again at command line, 

sudo apt-get update
then
sudo apt-get upgrade

Hopefully, this should get you going.

Cheers

Lowey

---

### Post by dead_man_walking on 2006-07-22
When i use gksudo i get theese errors

(gksudo:7409): Gdk-WARNING **: locale not supported by Xlib

(gksudo:7409): Gdk-WARNING **: cannot set locale modifiers
(gedit:7412): Gdk-WARNING **: locale not supported by Xlib

(gedit:7412): Gdk-WARNING **: cannot set locale modifiers

(gedit:7412): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

but when i use just sudo instead instead of gksudo ...sources.list opens

okay .. i think i did wat u guys told me to do (maybe)

i opened sources.list then i looked for breezy .. couldnt find it ... then i looked for  # deb and replaced it with deb .... but still i get errors


first is this

W: Couldn't stat source package list cdrom://Ubuntu 5.10 _dapper Badger_ - Release i386 (20051012) dapper/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fdapper%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_dapper_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _dapper Badger_ - Release i386 (20051012) dapper/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fdapper%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_dapper_restricted_binary-i386_Packages) - stat (2 No such file or directory)

second is this

cdrom:[Ubuntu 5.10 _dapper Badger_ - Release i386 (20051012)]/dists/dapper/main/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
cdrom:[Ubuntu 5.10 _dapper Badger_ - Release i386 (20051012)]/dists/dapper/restricted/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

sorry for theese noobish questions .... i hope i am not irritating anybody ... i would really appreciate ur help

---

### Post by dead_man_walking on 2006-07-23
Anybody replying

---

### Post by lowey23 on 2006-07-23
Sorry about the mix up with gksudo. Thats needed for opening graphical apps from the command line. sudo was what was needed.

You have a reference to 'dapper Badger" in there. I think that's whats causing your problem. I'm assuming that you have the internet connected so there is no need to have a reference to your CD in the sources.list. My suggestion is to remove those references completely. After you have done that your sources.list should look something like the one at this link:-

[http://www.psychocats.net/ubuntu/sources.php]("http://psychocats.net/ubuntu/sources.php")

I hope that helps you

Cheers

Lowey

---

### Post by dead_man_walking on 2006-07-23
Well i checked the link .... edited my sources.list with the one given on teh first number which was meant for dapper users ... and i havent got any 
errors while opening synaptic uptill now ... so i guess its working ...lol ... thnx for all teh help u guys gave me ... i really appreciate teh work that u guys have done for me ... thnx again

---

