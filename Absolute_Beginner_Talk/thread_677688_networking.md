---
title: "networking"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by jesterjoker on 2008-01-25
Hi 
will I have a prob with networking if the other pc's operate on xp? I connect via another pc running xp

---

### Post by nebu on 2008-01-25
First, install samba
> apt-get install samba

then install SWAT (Samba Web Administration Tool)
> apt-get install samba swat

now create a folder on your harddisk which you would like to share through the windows network..... this is an example
> 
cd ~
mkdir samba_share

now open the samba configuration file
> 
cd /etc/samba
gvim smb.conf


now add this code to the end of your conf file
> 
[samba_share]
comment = Shared - ~/share
path = /home/***usernamegoeshere***/samba_share
available = yes
browsable = yes
public = yes
writable = yes


make sure u have changed the text to ur username

now restart samba
> etc/init.d/samba restart

now change your password in your samba account
> smbpasswd -a ***usernamegoeshere***

if u dont have a samba account.... make one...
> adduser ***usernamegoeshere***



then in ur windows pc .... enter ur usrname and password of ur samba account when u try to view this folder through Workgroup Coputers in the Network Connections window

---

### Post by hyper_ch on 2008-01-25
why do you have him install swat if you're not even going to use it?

---

### Post by Nhatz on 2008-01-25
Yeah... why bother installing swat? :(

---

### Post by jonabyte on 2008-01-25
I would advise not using swat....I have never got it to work properly with other non-Ubuntu linux servers.
The command line and vi to edit the conf file works just fine.

---

### Post by nebu on 2008-01-29
> **Nhatz said:**
> Yeah... why bother installing swat? :(

it helps if u want to tweak ur network settings later on

---

### Post by jonandrews on 2008-01-29
I've put a step-bystep guide to networking Ubuntu / Windows on a website:

/www.europe.eclipse.co.uk/Ubuntu

I hope it helps..

---

### Post by jmap82 on 2008-02-12
Thanks!  That How-To worked perfectly!

And for the record I'm running a Windows Vista machine and an Ubuntu 6.06 Dapper Drake machine over a wireless network!  On top of that I'm a total newb!

Thanks again!  It was exactly what I was looking for!

---

