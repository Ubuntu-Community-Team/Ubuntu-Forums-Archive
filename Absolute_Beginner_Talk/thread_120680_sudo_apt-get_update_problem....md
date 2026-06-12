---
title: "sudo apt-get update problem..."
date: 2006-01-23
forum: Absolute Beginner Talk
---

### Post by grim918 on 2006-01-23
im getting this error message when i run sudo apt-get update. i dont know what could be causing the problem. 
here is a list of the repositories:

//-----------------------------------------------------------------------------//
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Preview i386 (20050908)]/ breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse

## Backports
##deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-backports main universe multiverse restricted
##deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted
//--------------------------------------------------------------------------------------------//

and this is the error that i get when i run the update command.

//-----------------------------------------//
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Preview i386 (20050908) breezy Release.gpg
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [19.6kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Sources
Fetched 20.2kB in 4s (4110B/s)
Reading package lists... Done
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release: Unknown error executing gpgv
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release: Unknown error executing gpgv
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release: Unknown error executing gpgv
W: You may want to run apt-get update to correct these problems
//--------------------------------------------------//

can anyone help me out with this problem.

---

### Post by bscbrit on 2006-01-23
It appears that the sites in question are not supported by a valid gpg authentication or, at least, that Synaptic cannot find a valid authentication.  I've little knowledge in this area but it might not be a problem with your installation but a problem with the site providing the software.  Does this fault actually prevent you from installing software from these sites?  I looked in my Synaptic and the only thing that might be of relevance is Settings > Repositories > Authentication.  However, in my Synaptic everything seems OK but you might want to check what your Synaptic shows.

---

### Post by carlosqueso on 2006-01-23
You also may want to remove the "us." from each line in your sources.list.  The US mirrors seem to just generally suck.

---

### Post by grim918 on 2006-01-23
i think that it is a problem with the sites. i tried running the command and i got a different error now. this is my new error.my dpkg command is not working. does anyone know how to fix this
heres the error:

E: dpkg was interrupted, you must manually run ' dpgk --configure -a' to correct the problem.

this shows up at the end after running the update command. the output from the update command is the same  as the above output.

---

### Post by carlosqueso on 2006-01-23
I'd try opening a terminal and trying what it says, first without "sudo", but you are probably gonna need to use "sudo" before it?

---

