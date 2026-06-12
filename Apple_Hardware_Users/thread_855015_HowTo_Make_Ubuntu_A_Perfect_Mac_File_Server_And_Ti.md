---
title: "HowTo: Make Ubuntu A Perfect Mac File Server And Time Machine Volume"
date: 2008-07-10
forum: Apple Hardware Users
---

### Post by bobosky on 2008-07-10
I am looking for a bit of help walking through these instructions. I am very new to Ubuntu and things like terminals and command lines so I need a little more help. 

I found these instructions on how to make a Ubuntu file server for my Mac laptops at [http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/)

Please read the my comments and let me know what I should do next!

This is where I am stuck
July 9th, 2008 at 6:12 pm

At the first terminal step I type:
sudo apt-get build-dep netatalk
and I get this message:
Unable to find a source package fr netatalk
? what am I doing wrong?

This was the reply
Nath says:
July 10th, 2008 at 1:38 am

enduser: You need to edit your sources.list:
sudo vi /etc/apt/sources.list

Check that you have a source repository enabled
e.g deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy main restricted universe multiverse

Then update your packages
sudo apt-get update

Then you&#8217;ll be able to get the source packages.

This is a great article - if you make sure you read every step then it works perfectly. I got this working on Mint Linux 5 Elyssa.



The only problem is i don't understand the reply!

Tim

---

### Post by tiresia on 2008-07-10
Please, open a terminal and post us what you get 

cat /etc/apt/sources.list

---

### Post by cyberdork33 on 2008-07-10
first, I would not use vi if you are new to the commandline because that is just going to make things more difficult. If you want to edit the sources.list file try:
```
gksudo gedit /etc/apt/sources.list
```for a graphical editor, or
```
sudo nano /etc/apt/sources.list
``` for a commandline editor that is actually easy to figure out.

The problem is that there are source code packages and compiled binary packages available in the repos. In order to get the build dependencies for netatalk (that is what your apt-get command is trying to do) it needs the source package for netatalk to see what it relies on. Unfortunately, your system doesn't know where to find a source package for netatalk. This may be because the source packakge repo is not enabled on your system. if you edit your sources.list file you can make sure that the lines that begin with "deb-src" are not commented out so that your system can use them.

---

### Post by bobosky on 2008-07-10
Thanks tiresia and cyberdork33 so much for helping me out!

To: tiresia
from your instructions I get this:

bobo@bobo-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
bobo@bobo-desktop:~$ 

To: cyberdork33
from this command: sudo nano /etc/apt/sources.list

I get:

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

^G Get Help     ^O WriteOut     ^R Read File    ^Y Prev Page    ^K Cut Text     ^C Cur Pos
^X Exit         ^J Justify      ^W Where Is     ^V Next Page    ^U UnCut Text   ^T To Spell

As I read through the above it my guess is that I need to upgrade to 8.04 before I can get this working.

Thanks again for helping on this.

I really need some kind of tutorial on the command line that would walk me through basic instructions on how to do simple things like move files from one place to the next. At this point I have no idea what I am typing or what the result means.

---

### Post by cyberdork33 on 2008-07-10
> **bobosky said:**
> I really need some kind of tutorial on the command line that would walk me through basic instructions on how to do simple things like move files from one place to the next. At this point I have no idea what I am typing or what the result means.
As you can see in your output, the line starting with deb-src are mostly commented out (have a #-sign in front of them). you need to remove the #-sign to enable these repositories.

sudo is a command that you use to temporarily gain admin priviledges. This is required to be able to change certain system files and other files that do not belong to your user. you type it just before any command that you want to run with admin priviledges.

nano is a very simple text editor. The table at the bottom are various commands you can use. ^=ctrl key. Move around with the arrows and make changes to the file as noted, then you can save with CTRL+O and exit the editor with CTRL+X.

with that in mind, the command "sudo nano /etc/apt/sources.list" means, "use admin priviledges to run nano to edit the /etc/apt/sources.list file".

The basics of the commandline can be found at several locations on the web.
[http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by bobosky on 2008-07-12
cyberdork33

Thanks for pointing me in the right directions with the command line, and I will got check out [http://linuxcommand.org/](http://linuxcommand.org/)

Update one the Perfect Mac Sever project. I have updated to Ubuntu 8.04 and now I have not hit any problems going through the instructions for setting up a Server for my mac network. I have not finished the set up but when I do I will post here.

---

### Post by flaggh on 2008-07-12
Please let us know how this turns out.  I have a home server running xubuntu with netatalk and have no problems accessing it through OSX, however I have been unable to use it as my time machine volume.  I've already set the parameter to enable time machine to use unsupported volumes and the share shows up in my time machine configuration and it will start the backup process, however after a minute or so it comes up with an error.  Good luck!

---

### Post by bobosky on 2008-07-12
flaggh, when I am able to rap my brain around what I am acculay doing I will share what I have learned, but I fear I am still kind of shooting in the dark. 

This is where I am stuck in the instructions. 
[http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/#comment-437](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/#comment-437)

Instruction "sudo gedit /etc/netatalk/AppleVolumes.default"
This brings up a file and I add this line "
 ~/ "$u" allow:username1,username2 cnidscheme:cdb " to the bottom of the file and save it. 

Instruction "By adding the following line you will share each users home directory with the user name as the Volume name. To make things more secure you can define all users who are allowed to connect to your Ubuntu box via AFP:" 

Okay, I don't quite understand what I should do here. Should I change username1, userneame2 to something eles? If so to what?

Instruction "Because we want to use the Ubuntu machine as a backup server for Time Machine you should define a second volume just for Time Machine. Create a new folder in your home directory first and name it TimeMachine (or anything you like). Then add the following line to your AppleVolumes.default."

Where do I add this new line to the AppleVolumes? Do I add it under the other line?  

Instruction "If you’re on Leopard and have no Tiger installed Macs in your network you should use the upriv option which adds support for AFP3 unix privileges. If you have Macs with Tiger installed just use options:usedots to avoid unexpected behavior:"

What if I have macs with both Leopard and Tiger?

Instruction  "Finally if you want more stability and can accept slower file transfers you can use the dbd cnidscheme (cnidscheme:dbd)."

I really don't know how to edit the AppleVolume so I don't know where or how to make this change. 

Instruction "Of course you can define every folder you like or even an attached USB disk. Just define the correct path. External drives in Ubuntu should be found under /media"

I have three USB drives I would like to hook-up and share with the two Mac laptops but I don't really know how to edit this path in the AppleVolumes.

Bellow is the text in my AppleVolumes file:

# volume format:
# :DEFAULT: [all of the default options except volume name]
# path [name] [casefold:x] [options:z,l,j] \
#   [allow:a,@b,c,d] [deny:a,@b,c,d] [dbpath:path] [password:p] \
#   [rwlist:a,@b,c,d] [rolist:a,@b,c,d] [limitsize:value in bytes]\
#   [preexec:cmd] [root_preexec:cmd] [postexec:cmd]  [root_postexec:cmd] 
#
#
# name:      volume name. it can't include the ':' character and is limited
#            to 27 characters in length.
#
# variable substitutions:
# you can use variables for both <path> and <name> now. here are the
# rules:
#     1) if you specify an unknown variable, it will not get converted. 
#     2) if you specify a known variable, but that variable doesn't have
#        a value, it will get ignored.
#
# the variables:
# $b   -> basename of path
# $c   -> client's ip or appletalk address
# $d   -> volume pathname on server    
# $f   -> full name (whatever's in the gecos field)
# $g   -> group
# $h   -> hostname 
# $i   -> client ip without tcp port or appletalk network   
# $s   -> server name (can be the hostname)
# $u   -> username (if guest, it's whatever user guest is running as)
# $v   -> volume name (either ADEID_NAME or basename of path)
# $z   -> zone (may not exist)
# $$   -> $
#
# casefold options [syntax: casefold:option]:
# tolower    -> lowercases names in both directions
# toupper    -> uppercases names in both directions
# xlatelower -> client sees lowercase, server sees uppercase
# xlateupper -> client sees uppercase, server sees lowercase
#
# allow/deny/rwlist/rolist format [syntax: allow:user1,@group]:
# user1,@group,user2  -> allows/denies access from listed users/groups
#                        rwlist/rolist control whether or not the
#			 volume is ro for those users.
# preexec             -> command to be run when the volume is mounted,
#                        ignore for user defined volumes
# root_preexec        -> command to be run as root when the volume is mounted,
#                        ignore for user defined volumes
# postexec             -> command to be run when the volume is closed,
#                        ignore for user defined volumes
# root_postexec        -> command to be run as root when the volume is closed,
#                        ignore for user defined volumes
#
# codepage options [syntax: options:charsetname]
# volcharset           -> specifies the charset to be used as the volume codepage
#                         e.g. "UTF8", "UTF8-MAC", "ISO-8859-15"
# maccharset           -> specifies the charset to be used as the mac client codepage
#                         e.g. "MAC_ROMAN", "MAC_CYRILLIC"
#
# perm                -> default permission value OR with the client requested perm
#
# miscellaneous options [syntax: options:option1,option2]:
# prodos              -> make compatible with appleII clients.
# crlf                -> enable crlf translation for TEXT files.
# noadouble           -> don't create .AppleDouble unless a resource
#                        fork needs to be created.
# ro                  -> mount the volume as read-only.
# mswindows           -> enforce filename restrictions imposed by MS
#                        Windows. this will also invoke a default
#			 codepage (iso8859-1) if one isn't already 
#			 specified.
# nohex		      -> don't do :hex translations for anything
#		         except dot files. specify usedots as well if
#			 you want that turned off. note: this option
#			 makes the / character illegal.
# usedots             -> don't do :hex translation for dot files. note: when 
#                        this option gets set, certain file names
#			 become illegal. these are .Parent and
#			 anything that starts with .Apple.
# invisibledots       -> don't do :hex translation for dot files. note: when 
#                        this option gets set, certain file names
#			 become illegal. these are .Parent and
#			 anything that starts with .Apple. also, dot
#			 files created on the unix side are marked invisible. 
# limitsize           -> limit disk size reporting to 2GB. this is
#                        here for older macintoshes using newer
#                        appleshare clients. yucko.
# nofileid            -> don't advertise createfileid, resolveid, deleteid 
#                        calls
# root_preexec_close  -> a non-zero return code from root_preexec close the 
#                        volume being mounted.
# preexec_close       -> a non-zero return code from preexec close the 
#                        volume being mounted.
# nostat              -> don't stat volume path when enumerating volumes list
# upriv               -> use unix privilege.  
#
#
# dbpath:path         -> store the database stuff in the following path.
# password:password   -> set a volume password (8 characters max)
# cnidscheme:scheme   -> set the cnid scheme for the volume, default is [cdb]
#                        available schemes: [cdb dbd last]
#
# By default all users have access to their home directories.
~/ "$u" allow:username1,username2 cnidscheme:cdb
/home/bobo/TimeMachine TimeMachine allow:username1,username2 cnidscheme:cdb options:usedots
/media/900 allow:username1,username2 cnidscheme:cdb options:usedots
/media/240 allow:username1,username2 cnidscheme:cdb options:usedots
/media/150 allow:username1,username2 cnidscheme:cdb options:usedots

900 240 150 are the names of the USB drives. Did I get this right?

---

### Post by cyberdork33 on 2008-07-12
> **flaggh said:**
> I've already set the parameter to enable time machine to use unsupported volumes and the share shows up in my time machine configuration and it will start the backup process, however after a minute or so it comes up with an error.  Good luck!this will be true for creating Time Machine backups on network volumes. Google a bit and you will find suggestions. Once you can get it to create a valid sparsebundle, it will work great. I had to try a few dozen times before it worked.

---

### Post by flaggh on 2008-07-13
> **bobosky said:**
> 
Instruction "sudo gedit /etc/netatalk/AppleVolumes.default"
This brings up a file and I add this line "
 ~/ "$u" allow:username1,username2 cnidscheme:cdb " to the bottom of the file and save it. 

Instruction "By adding the following line you will share each users home directory with the user name as the Volume name. To make things more secure you can define all users who are allowed to connect to your Ubuntu box via AFP:" 

Okay, I don't quite understand what I should do here. Should I change username1, userneame2 to something eles? If so to what?

I don't think this step is totally necessary, but what you are doing by adding this line is restricting AFP access to only the usernames listed.  Yes you replace username1, username2 with actual usernames.  This prevents any users not listed from connecting to the server.

> **bobosky said:**
> 
Instruction "Because we want to use the Ubuntu machine as a backup server for Time Machine you should define a second volume just for Time Machine. Create a new folder in your home directory first and name it TimeMachine (or anything you like). Then add the following line to your AppleVolumes.default."

Where do I add this new line to the AppleVolumes? Do I add it under the other line?  

Yes, add it at the end of the document after the other line.

> **bobosky said:**
> 
Instruction "If you’re on Leopard and have no Tiger installed Macs in your network you should use the upriv option which adds support for AFP3 unix privileges. If you have Macs with Tiger installed just use options:usedots to avoid unexpected behavior:"

What if I have macs with both Leopard and Tiger?

Sounds like the safest bet is just usedots and no upriv.

> **bobosky said:**
> 
Instruction  "Finally if you want more stability and can accept slower file transfers you can use the dbd cnidscheme (cnidscheme:dbd)."

I really don't know how to edit the AppleVolume so I don't know where or how to make this change. 

It's already added to the TimeMachine configuration line.  Notice that is all one line even though it shows up as multiple on the web page.

> **bobosky said:**
> 
Instruction "Of course you can define every folder you like or even an attached USB disk. Just define the correct path. External drives in Ubuntu should be found under /media"

I have three USB drives I would like to hook-up and share with the two Mac laptops but I don't really know how to edit this path in the AppleVolumes.

~/ "$u" allow:username1,username2 cnidscheme:cdb
/home/bobo/TimeMachine TimeMachine allow:username1,username2 cnidscheme:cdb options:usedots
/media/900 allow:username1,username2 cnidscheme:cdb options:usedots
/media/240 allow:username1,username2 cnidscheme:cdb options:usedots
/media/150 allow:username1,username2 cnidscheme:cdb options:usedots

900 240 150 are the names of the USB drives. Did I get this right?

Assuming those are the actual mount points of the USB drives, it looks like you did everything write except for replacing usernames with actual usernames.  For example:
```
~/ "$u" allow:bobo cnidscheme:cdb
```

---

### Post by hehe22 on 2008-07-13
wow! Nice post! very interesting! thanks guys!

---

### Post by Protoss on 2008-07-15
So I followed this guide, along with the one linked. Everything seems to work, Leopard sees the share and logs me in fine and I can even browse the filesystem...But when I try to transfer a file, it's painfully slow....

---

