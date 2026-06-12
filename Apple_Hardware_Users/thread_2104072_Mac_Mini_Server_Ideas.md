---
title: "Mac Mini Server Ideas?"
date: 2013-01-12
forum: Apple Hardware Users
---

### Post by eenofonn on 2013-01-12
Hey everyone!

I happened upon an older Intel 1.6 Ghz Core Duo Mac Mini (which I thought was a G4) it had Tiger installed on it but I didn't really have a need for another desktop. So I thought it would be a fun project to throw a few things on there and run it headless (which I found has some quirks).

I started off with just a simple LAMP server but I've added a few things like BIND9 and Minidlna.
I have a NAS already so I don't need a Samba server and I am happy to let my router serve up DHCP.  So I guess I'm just curious if anyone else has any good ideas that help me utilize this cool little piece of hardware.

I will probably get around to setting up bacula on there at some point but I'm just not backup crazy at home.

*Edit - I forgot to add I'm running 12.04

---

### Post by eenofonn on 2013-01-13
Bump

---

### Post by LinuxBill on 2013-01-14
- Dont know if you have any use for usenet? Could try setting up sabnzb on there for any of your download needs? I use the program sickbeard for downloading a lot of TV shows that i miss if im working or busy. Its great does it automatically and you choose what qulaity you would like to download with.
 
- OpenLDAP server for authentication around the house/flat?
 
- Rsync server for all your machines?
 
Some are slightly overkill but would be fun to do.

---

### Post by eenofonn on 2013-01-14
> **LinuxBill said:**
> - Dont know if you have any use for usenet? Could try setting up sabnzb on there for any of your download needs? I use the program sickbeard for downloading a lot of TV shows that i miss if im working or busy. Its great does it automatically and you choose what qulaity you would like to download with.
 
- OpenLDAP server for authentication around the house/flat?
 
- Rsync server for all your machines?
 
Some are slightly overkill but would be fun to do.

I'm on limited bandwidth so I try to keep my downloads to a minimum but that sounds like a good idea if I didn't have the restriction. I've thought about doing an LDAP setup that might be fun! 

Rsync server would give me what functionality? I would think that it would be only usefull if I had some actual space on that machine which only has a 60GB HD.  

More information about my setup:

Main Machine - 2011 27" iMac Core i5 Dual boot Mt Lion and Win 7
NAS - D-Link DNS-321 with dual 1TB Hitachi drives in Raid-1
Secondary Machine - Dell XPS 435 w/ Vista Ultimate (not sure what I'm going to do with this)
Streamer - NetGear NTV300SL rooted

---

### Post by LinuxBill on 2013-01-14
> **eenofonn said:**
> I'm on limited bandwidth so I try to keep my downloads to a minimum but that sounds like a good idea if I didn't have the restriction. I've thought about doing an LDAP setup that might be fun! 

Rsync server would give me what functionality? I would think that it would be only usefull if I had some actual space on that machine which only has a 60GB HD.  

More information about my setup:

Main Machine - 2011 27" iMac Core i5 Dual boot Mt Lion and Win 7
NAS - D-Link DNS-321 with dual 1TB Hitachi drives in Raid-1
Secondary Machine - Dell XPS 435 w/ Vista Ultimate (not sure what I'm going to do with this)
Streamer - NetGear NTV300SL rooted

Rsync would let you back up your key folders and config files to your mac mini. Might only need a 10GB partition? Even do full backups if you attach a USB HDD ?

---

### Post by eenofonn on 2013-01-14
> **LinuxBill said:**
> Rsync would let you back up your key folders and config files to your mac mini. Might only need a 10GB partition? Even do full backups if you attach a USB HDD ?

Oh you must not have seen my statement about Bacula :)

---

### Post by eenofonn on 2013-01-15
Just a note regarding my setup.  I have removed minidlna and installed Plex.... wow what a difference

---

