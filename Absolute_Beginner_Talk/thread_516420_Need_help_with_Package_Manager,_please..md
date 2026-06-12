---
title: "Need help with Package Manager, please."
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2007-08-03
I have managed to screw something up on my Feisty computer when trying to install some codecs.

The 'update' icon is showing and when I put my cursor on it I get this message:-

“ A error occurred, please run Package manager from the right click menu or apt-get on a terminal to see what is wrong.  The error message was: 'Error: BrokenCount > 0' “  (I think that is zero but could be wrong)

I tried entering ' sudo apt-get ' in a terminal but I don't see how this is telling me what is wrong:-

qwer@qwer-desktop:~$ apt-get

apt 0.6.46.4ubuntu10 for linux i386 compiled on Mar 14 2007 17:43:24

Usage: apt-get [options] command

       apt-get [options] install|remove pkg1 [pkg2 ...]

       apt-get [options] source pkg1 [pkg2 ...]



apt-get is a simple command line interface for downloading and

installing packages. The most frequently used commands are update

and install.



Commands:

   update - Retrieve new lists of packages

   upgrade - Perform an upgrade

   install - Install new packages (pkg is libc6 not libc6.deb)

   remove - Remove packages

   source - Download source archives

   build-dep - Configure build-dependencies for source packages

   dist-upgrade - Distribution upgrade, see apt-get(8)

   dselect-upgrade - Follow dselect selections

   clean - Erase downloaded archive files

   autoclean - Erase old downloaded archive files

   check - Verify that there are no broken dependencies



Options:

  -h  This help text.

  -q  Loggable output - no progress indicator

  -qq No output except for errors

  -d  Download only - do NOT install or unpack archives

  -s  No-act. Perform ordering simulation

  -y  Assume Yes to all queries and do not prompt

  -f  Attempt to continue if the integrity check fails

  -m  Attempt to continue if archives are unlocatable

  -u  Show a list of upgraded packages as well

  -b  Build the source package after fetching it

  -V  Show verbose version numbers

  -c=? Read this configuration file

  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp

See the apt-get(8), sources.list(5) and apt.conf(5) manual

pages for more information and options.

                       This APT has Super Cow Powers.

qwer@qwer-desktop:~$ 


Any help will be appreciated.

---

### Post by Steve1961 on 2007-08-03
Run sudo apt-get update from a terminal and post any error messages you get

---

### Post by L Campbell on 2007-08-03
> **Steve1961 said:**
> Run sudo apt-get update from a terminal and post any error messages you get

Hi, thanks for your interest.

qwer@qwer-desktop:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 3B in 1s (3B/s)  
Reading package lists... Done
qwer@qwer-desktop:~$ 

It looks like this worked.

Now the update icon is telling me I have 15 updates to install.

Many thanks for your help.

---

### Post by tchoklat on 2007-08-03
I often use aptitude, try
sudo aptitude update
sudo aptitude upgrade
 
 
tchoklat

---

