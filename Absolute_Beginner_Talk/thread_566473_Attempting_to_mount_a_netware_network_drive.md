---
title: "Attempting to mount a netware network drive?"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by weezerisrock on 2007-10-03
Ok I am attempting to get to my shared drives on my ubuntu box.  We are using novell here and I cannot figure out for the life of me how to mount my netware drives.  (oh heck, or any network drive for that matter.)  I could really use some help.  Thanks in advance!

---

### Post by Nehvrook on 2007-10-03
Just bought one of these myself. What I did was found out it's IP address (How you do this will depend on your network drive and what OS's/PC's you have etc)

Once you know that all I do to mount it is go to

Places > Connect to Server

enter in "Windows Share" where it says service type  and then enter the IP address under server. Click connect and you should be able to see your network drive

Hope this helps

EDIT: I just tried going to 

Places > Connect to Server 

and then just clicking "Browse Network" and it found the network drive that way too (Though it took a while)

So if you can't/dont wan't to find the IP address you can try that way too

---

### Post by kaspar_silas on 2008-06-19
Hi,

I hope someone can help as this is driving me crazy.

My workplaces has several large Novell drives that I want to connect to. On XP it's a simple matter of double clicking the novell icon and entering a password and username and viola n: and x: appear. 

However I moved over to Ubuntu and this is now the only thing I do in XP and im getting to really hate the dual booting. 

I looked on the Novell site but they only have clients for Suse and OpenSuse. I did try these on Ubuntu as it appeared on the download screen Linux (all versions). But you just get screens of failed dependencies like the following

kasilas@kasilas:~/Desktop/ncl_build_711/NCL_disk$ sudo ./ncl_install install

[ncl_install] ncl_install v2.0 started
[ncl_install] mode = install
[ncl_install] option = 

[ncl_install] This script uses the following RPM options:
[ncl_install] -i
[ncl_install] For a description of these options,
[ncl_install] see the RPM documentation.

[ncl_install] Installing the Novell Client for Linux.
[ncl_install] Please wait...


[ncl_install] Installing nici...
error: Failed dependencies:
	/bin/sh is needed by nici-2.7.0-0.01.i386
	ld-linux.so.2 is needed by nici-2.7.0-0.01.i386
	libc.so.6 is needed by nici-2.7.0-0.01.i386
	libpthread.so.0 is needed by nici-2.7.0-0.01.i386
	libc.so.6(GLIBC_2.0) is needed by nici-2.7.0-0.01.i386
	libc.so.6(GLIBC_2.1) is needed by nici-2.7.0-0.01.i386
	libc.so.6(GLIBC_2.1.3) is needed by nici-2.7.0-0.01.i386
	libpthread.so.0(GLIBC_2.0) is needed by nici-2.7.0-0.01.i386
	libpthread.so.0(GLIBC_2.1) is needed by nici-2.7.0-0.01.i386
[ncl_install] ERROR: Installation of the nici rpm failed.

Cheers for any help, it's much appreciated

kasilas

---

### Post by Coombabah on 2008-07-15
> **weezerisrock said:**
> Ok I am attempting to get to my shared drives on my ubuntu box.  We are using novell here and I cannot figure out for the life of me how to mount my netware drives.  (oh heck, or any network drive for that matter.)  I could really use some help.  Thanks in advance!

I currently use ncpmount provided by installing ncpfs to mount Novell Netware drives in Ubuntu. 
It works OK for small files, isn't fast but saves booting to windows.
I found your post whilst looking for a better way.


Install ncpfs via synaptic or your prefered method along with it's dependancies. This will give you the ncpmount command.

man ncpmount will explain the options

The mount command will look something like this

sudo ncpmount -S short_novell_server_name -A novell_server_domain_name -U novell_username_with_dots_and_trees_or_whatever -V novell_share_name -u your_ubuntu_username /path_you_created_with_user_permissions_to_mount_it

---

