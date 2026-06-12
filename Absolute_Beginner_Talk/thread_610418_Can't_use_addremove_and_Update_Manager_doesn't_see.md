---
title: "Can't use add/remove and Update Manager doesn't seem to want to work in Gutsy"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by gambleb on 2007-11-12
I keep getting the message 

"The list of applications is not available

Click on 'Reload' to load it. To reload the list you need a working internet connection." 

I click refresh and then the same thing happens again.  Also I tried to use the update manager and either there haven't been any updates for Gutsy yet or that's not working either.  

I tried some of the fixes from other posts to no avail.  Please help.

Brian

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
ummmm can you past the contents of this file here
 /etc/apt/sources.list

can do that with this command 
sudo gedit /etc/apt/sources.list

well then copy and past into the forums :) 
there has been a problem were it comments out all your sorce list dont know why though :/

---

### Post by anewguy on 2007-11-12
When I installed Gutsy, I had a similar sounding problem.  The solution ended up being that the software sources weren't tagged.  To check, click on "System", scroll down to "Administration" then over to and click on "Software Sources".  You want to make sure at least the following are checked (I have another checked myself):

Canonical-Supported Open Source Software (main)

Community-maintained Open Source software (universe)


By default, after installing Gutsy, both of those were unchecked on my system.  Try checking them on your system, then re-do the attempts at update (you may have to tell it to "reload").:)

---

### Post by gambleb on 2007-11-12
This was pasted in from another post.  The first time I ran that command it was blank.




deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

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
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by doctorbighands on 2007-11-12
I assume the contents of the sources.list file you posted are your own. If so, you need to go through and uncomment your sources. Do this by erasing the "#" signs in front of every line that begins with "deb" or "deb-src". When that's done, save the file, and all should be well!

EDIT: I should mention that you need to be very careful to only delete the # signs DIRECTLY in front of the words "deb" or "deb-src". Leave all of the other ones intact!

---

### Post by gambleb on 2007-11-12
Thanks dude.  That at least fixed the add/remove problem...  Still didn't get any updates though.  Maybe there aren't any.

Brian

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
> **anewguy said:**
> When I installed Gutsy, I had a similar sounding problem.  The solution ended up being that the software sources weren't tagged.  To check, click on "System", scroll down to "Administration" then over to and click on "Software Sources".  You want to make sure at least the following are checked (I have another checked myself):

Canonical-Supported Open Source Software (main)

Community-maintained Open Source software (universe)


By default, after installing Gutsy, both of those were unchecked on my system.  Try checking them on your system, then re-do the attempts at update (you may have to tell it to "reload").:)

ya that should work 2 both are to check and see if you have your source list avalable

---

### Post by gambleb on 2007-11-12
Belay my last.  Both problems are fixed now...  thanks guys.

Brian

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
> **gambleb said:**
> Thanks dude.  That at least fixed the add/remove problem...  Still didn't get any updates though.  Maybe there aren't any.

Brian

if you can install something off the internet using
sudo apt-get install thingy 
then i think its fix right ?

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
OH this is a common problem we should make this page a stikky

---

### Post by anewguy on 2007-11-12
> **<<joe>> said:**
> ya that should work 2 both are to check and see if you have your source list avalable

Yes, both are doing the same thing - what you change under system/administration/software sources is a menu driven way of updating the sources.lst file, and you don't have to go through every line.  Even if you are using a restricted or other catagory, it can be handled through the manager. And, if I may add, it is probably safer for the newbie than doing the edit.  Please don't get me wrong - there is NOTHING wrong with doing the edit, just the menu approach would easier for most.:)

---

### Post by Heaf on 2007-11-12
so I had same problem but I just made this and everything works fine
 

[1] Open a terminal window - Applications > Accessories > Terminal
[2] Open the sources.list file for editing as super-user:
gksudo gedit /etc/sources.list
[3] Replace its content with the following:

# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# [https://help.ubuntu.com/community/Re...es/CommandLine](https://help.ubuntu.com/community/Re...es/CommandLine)

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe multiverse

[4] Use the following command to update your packages information:
sudo apt-get update

if you are using different version of ubuntu just change the (feisty) to your own version

---

### Post by Heaf on 2007-11-12
> **<<joe>> said:**
> OH this is a common problem we should make this page a stikky

yes many of people are having this problem. :confused:

---

