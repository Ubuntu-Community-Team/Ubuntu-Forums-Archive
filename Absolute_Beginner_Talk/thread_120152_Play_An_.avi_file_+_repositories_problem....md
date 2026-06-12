---
title: "Play An .avi file + repositories problem..."
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by Kevbb on 2006-01-20
I just installed Ubuntu 2 days ago, (I really like the different experience) and decided to try and play some .avi files i have. It seems joining the forums is the best way to go.
Im trying to use Totem, but when I go to open an .avi file with Totem, it seems to just shut the program down (nothing happens, and program closes).
I have enabled extra repositories, to check for new stuff, but they mostly produce errors...along the lines of [COLOR="Red"]"Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hoary-updates Release.gpg
Temporary failure resolving 'nz.archive.ubuntu.com'[/COLOR]
Can someone please assist me in getting an .avi to play,
and perhaps point me in the correct direction when it comes to adding / changing repositories...or why I might be having these problems?

Cheers / Kevbb (first time poster)

---

### Post by Masteroc on 2006-01-20
try using mplayer with codecs from the repository

---

### Post by Mustard on 2006-01-20
KevB, it looks like something is mucked up in your sources.list from that error message.  Either the mirror you're using is down, or the url is misconfigured.  Can you post the entire contents of your sources.list in here please.  Try wrapping it in these tags when you post to make it look neat. :)  [noparse]```
 ..your sources.list in here
```[/noparse].

To veiw your sources.list try this command in a terminal, which you can find in your Applications>>System Tools menu (for hoary hedgehog), which it appears you are running atm.

```
sudo gedit /etc/apt/sources.list
```

Copy and paste the contents of that file into here so we can take a look at it.

Now its probably not worth proceeding on your .avi problem until this problem is solved, but I think you might need to download and install some other things before you can play .avi's.  You won't be able to download them until you fix your sources.list problem though.

I've created a pretty standard Hoary Hedgehog sources.list below for comparison. (I've used the New Zealand mirrors as well, but they are not compulsory)

Sources.list created using  [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

```
# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://nz.archive.ubuntu.com/ubuntu hoary main restricted
deb http://nz.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb http://security.ubuntu.com/ubuntu hoary-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://nz.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://nz.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://nz.archive.ubuntu.com/ubuntu hoary universe multiverse
deb http://nz.archive.ubuntu.com/ubuntu hoary-updates universe multiverse
deb http://security.ubuntu.com/ubuntu hoary-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://nz.archive.ubuntu.com/ubuntu hoary universe multiverse
deb-src http://nz.archive.ubuntu.com/ubuntu hoary-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu hoary-security universe multiverse
```

---

### Post by Mustard on 2006-01-20
[QUOTE=Masteroc]try using mplayer with codecs from the repository[/QUOTE]

w32codecs is not in the repository btw.  I also have doubts that he can download mplayer, given the repositories problems he is having. :)

---

### Post by Kevbb on 2006-01-20
Mustard...cheers for the quick reply...REPOSITORY code as per below
```
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb http://nz.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://nz.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://nz.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://nz.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://nz.archive.ubuntu.com/ubuntu hoary universe
deb-src http://nz.archive.ubuntu.com/ubuntu hoary universe

# deb http://security.ubuntu.com/ubuntu hoary-security main restricted
# deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

# deb http://security.ubuntu.com/ubuntu hoary-security universe
# deb-src http://security.ubuntu.com/ubuntu hoary-security universe

```

---

### Post by Mustard on 2006-01-20
Well, from the look of your sources.list everything seems to be fine.  Mind you I go cross-eyed whenever I try looking for errors in sources.lists. :)

I would suspect that your local mirror is having problems if you are getting problems with resolving their address.  I would create a sources.list that doesn't use your local New Zealand mirror (which I have done below) and replace your old sources.list with the new one.  I'll create one using the link I posted above and post it in here...

You could continue to try updating your package list from your current sources.list by using this command...

```
sudo apt-get update
```

If it continues to give you errors, then backup your old sources.list using this command...

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```

Then open up your old sources.list using..

```
sudo gedit /etc/apt/sources.list
```

Then completely remove your old sources.list text by selecting it all and deleting it, and the copy this one below into your sources.list to replace the old one.  After saving the new one, you would need to do a sudo apt-get update again, to get the latest package list.


This one below is not using the New Zealand mirror, so hopefully you won't get the same resolve problems again.  Inside this sources.list below are instructions on fixing gpg errors too, if you happen to encounter any.  If everything works after that, then I guess we could try installing some stuff to get .avi's playing.

```
# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu hoary main restricted
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb http://security.ubuntu.com/ubuntu hoary-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu hoary universe multiverse
deb http://archive.ubuntu.com/ubuntu hoary-updates universe multiverse
deb http://security.ubuntu.com/ubuntu hoary-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://archive.ubuntu.com/ubuntu hoary universe multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu hoary-security universe multiverse
```

Now in the future if you want to go back to using your local mirror version.  You have a backup, so to copy the backup back to your sources.list you could do this...

```
sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list
```

This will overwrite the sources.list that is not using the New Zealand mirror.  Alternatively you could go to the Source-o-matic link and create a brand new sources.list that points at your NZ mirror and use that instead.

Oh...one more thing.  You might like to look over this old guide for Hoary Hedgehog.
[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)
It's got some stuff on installing multimedia codecs and even installing Mplayer.  The only problem with it is that you can't get w32codecs from the standard repositories anymore.  To do that you would need to go here and read through the wiki guide.
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

Have you thought about upgrading your system to Breezy Badger?

---

### Post by Kevbb on 2006-01-20
I replaced the repository list with the one you provided, and ran 
"sudo apt-get update" ...below is the list generated, including errors. Im running this PC through another PC (sharing the other pc's internet connection) this wouldn't be causing problems would it? This PC has full permissions through the other one.
The other PC is running Windows XP (probably a swear word around here...aye..lol)
I mentioned Just in case this might affect anything? 
[CODE:~$ sudo apt-get update
Err http://nz.archive.ubuntu.com hoary Release.gpg
  Temporary failure resolving 'nz.archive.ubuntu.com'
Err http://security.ubuntu.com hoary-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Err http://nz.archive.ubuntu.com hoary-updates Release.gpg
  Temporary failure resolving 'nz.archive.ubuntu.com'
Ign http://security.ubuntu.com hoary-security Release
Ign http://nz.archive.ubuntu.com hoary Release
Ign http://security.ubuntu.com hoary-security/main Packages
Ign http://nz.archive.ubuntu.com hoary-updates Release
Ign http://security.ubuntu.com hoary-security/restricted Packages
Ign http://nz.archive.ubuntu.com hoary/main Packages
Ign http://security.ubuntu.com hoary-security/main Sources
Ign http://nz.archive.ubuntu.com hoary/restricted Packages
Ign http://security.ubuntu.com hoary-security/restricted Sources
Ign http://nz.archive.ubuntu.com hoary/main Sources
Ign http://security.ubuntu.com hoary-security/universe Packages
Ign http://nz.archive.ubuntu.com hoary/restricted Sources
Ign http://security.ubuntu.com hoary-security/multiverse Packages
Ign http://nz.archive.ubuntu.com hoary/universe Packages
Ign http://security.ubuntu.com hoary-security/universe Sources
Ign http://nz.archive.ubuntu.com hoary/multiverse Packages
Ign http://security.ubuntu.com hoary-security/multiverse Sources
Ign http://nz.archive.ubuntu.com hoary/universe Sources
Err http://security.ubuntu.com hoary-security/main Packages
  Temporary failure resolving 'security.ubuntu.com'
Ign http://nz.archive.ubuntu.com hoary/multiverse Sources
Err http://security.ubuntu.com hoary-security/restricted Packages
  Temporary failure resolving 'security.ubuntu.com'
Ign http://nz.archive.ubuntu.com hoary-updates/main Packages
Err http://security.ubuntu.com hoary-security/main Sources
  Temporary failure resolving 'security.ubuntu.com'
Ign http://nz.archive.ubuntu.com hoary-updates/restricted Packages
Err http://security.ubuntu.com hoary-security/restricted Sources
  Temporary failure resolving 'security.ubuntu.com'
Ign http://nz.archive.ubuntu.com hoary-updates/main Sources
Err http://security.ubuntu.com hoary-security/universe Packages
  Temporary failure resolving 'security.ubuntu.com'
Ign http://nz.archive.ubuntu.com hoary-updates/restricted Sources
Err http://security.ubuntu.com hoary-security/multiverse Packages
  Temporary failure resolving 'security.ubuntu.com'
Err http://security.ubuntu.com hoary-security/universe Sources
  Temporary failure resolving 'security.ubuntu.com'
Ign http://nz.archive.ubuntu.com hoary-updates/universe Packages
Err http://security.ubuntu.com hoary-security/multiverse Sources
  Temporary failure resolving 'security.ubuntu.com'
Ign http://nz.archive.ubuntu.com hoary-updates/multiverse Packages
Ign http://nz.archive.ubuntu.com hoary-updates/universe Sources
Ign http://nz.archive.ubuntu.com hoary-updates/multiverse Sources
Err http://nz.archive.ubuntu.com hoary/main Packages
  Temporary failure resolving 'nz.archive.ubuntu.com'
Err http://nz.archive.ubuntu.com hoary/restricted Packages
  Temporary failure resolving 'nz.archive.ubuntu.com'
Err http://nz.archive.ubuntu.com hoary/main Sources
  Temporary failure resolving 'nz.archive.ubuntu.com'
Err http://nz.archive.ubuntu.com hoary/restricted Sources
  Temporary failure resolving 'nz.archive.ubuntu.com'
Err http://nz.archive.ubuntu.com hoary/universe Packages
  Temporary failure resolving 'nz.archive.ubuntu.com'
Err http://nz.archive.ubuntu.com hoary/multiverse Packages
  Temporary failure resolving 'nz.archive.ubuntu.com'
Err http://nz.archive.ubuntu.com hoary/universe Sources
  Temporary failure resolving 'nz.archive.ubuntu.com'
Err http://nz.archive.ubuntu.com hoary/multiverse Sources
  Temporary failure resolving 'nz.archive.ubuntu.com'
Err http://nz.archive.ubuntu.com hoary-updates/main Packages
  Temporary failure resolving 'nz.archive.ubuntu.com'
Err http://nz.archive.ubuntu.com hoary-updates/restricted Packages
  Temporary failure resolving 'nz.archive.ubuntu.com'
Err http://nz.archive.ubuntu.com hoary-updates/main Sources
  Temporary failure resolving 'nz.archive.ubuntu.com'
Err http://nz.archive.ubuntu.com hoary-updates/restricted Sources
  Temporary failure resolving 'nz.archive.ubuntu.com'
Err http://nz.archive.ubuntu.com hoary-updates/universe Packages
  Temporary failure resolving 'nz.archive.ubuntu.com'
Err http://nz.archive.ubuntu.com hoary-updates/multiverse Packages
  Temporary failure resolving 'nz.archive.ubuntu.com'
Err http://nz.archive.ubuntu.com hoary-updates/universe Sources
  Temporary failure resolving 'nz.archive.ubuntu.com'
Err http://nz.archive.ubuntu.com hoary-updates/multiverse Sources
  Temporary failure resolving 'nz.archive.ubuntu.com'
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg  Temporary failure resolving 'nz.archive.ubuntu.com'
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/hoary-updates/Release.gpg  Temporary failure resolving 'nz.archive.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hoary-security/Release.gpg  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hoary-security/main/binary-i386/Packages.gz  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/binary-i386/Packages.gz  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz  Temporary failure resolving 'nz.archive.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hoary-security/main/source/Sources.gz  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz  Temporary failure resolving 'nz.archive.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/source/Sources.gz  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/hoary/main/source/Sources.gz  Temporary failure resolving 'nz.archive.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/binary-i386/Packages.gz  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/hoary/restricted/source/Sources.gz  Temporary failure resolving 'nz.archive.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hoary-security/multiverse/binary-i386/Packages.gz  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz  Temporary failure resolving 'nz.archive.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/source/Sources.gz  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/hoary/multiverse/binary-i386/Packages.gz  Temporary failure resolving 'nz.archive.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hoary-security/multiverse/source/Sources.gz  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/hoary/universe/source/Sources.gz  Temporary failure resolving 'nz.archive.ubuntu.com'
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/hoary/multiverse/source/Sources.gz  Temporary failure resolving 'nz.archive.ubuntu.com'
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/binary-i386/Packages.gz  Temporary failure resolving 'nz.archive.ubuntu.com'
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/binary-i386/Packages.gz  Temporary failure resolving 'nz.archive.ubuntu.com'
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/source/Sources.gz  Temporary failure resolving 'nz.archive.ubuntu.com'
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/source/Sources.gz  Temporary failure resolving 'nz.archive.ubuntu.com'
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/hoary-updates/universe/binary-i386/Packages.gz  Temporary failure resolving 'nz.archive.ubuntu.com'
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/hoary-updates/multiverse/binary-i386/Packages.gz  Temporary failure resolving 'nz.archive.ubuntu.com'
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/hoary-updates/universe/source/Sources.gz  Temporary failure resolving 'nz.archive.ubuntu.com'
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/hoary-updates/multiverse/source/Sources.gz  Temporary failure resolving 'nz.archive.ubuntu.com'
Reading package lists... Done
W: Couldn't stat source package list http://nz.archive.ubuntu.com hoary/main Packages (/var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://nz.archive.ubuntu.com hoary/restricted Packages (/var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://nz.archive.ubuntu.com hoary/universe Packages (/var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://nz.archive.ubuntu.com hoary/multiverse Packages (/var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://nz.archive.ubuntu.com hoary-updates/main Packages (/var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://nz.archive.ubuntu.com hoary-updates/restricted Packages (/var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://nz.archive.ubuntu.com hoary-updates/universe Packages (/var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_hoary-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://nz.archive.ubuntu.com hoary-updates/multiverse Packages (/var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_hoary-updates_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com hoary-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com hoary-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com hoary-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
[/CODE]
Any help is really appreciated...thanks people / Kevbb.

---

### Post by Kevbb on 2006-01-21
Cheers for the links....I'll have a look at them soon. appreciate your help...thanks.

I changed the list to the second one you provided (without NZ) and am still getting resolving errors...." Temporary failure resolving 'security.ubuntu.com'...etc....etc,
as per my previous comment..do you think because im sharing a connection that it's causing any prob's? There's nothing downloading on the other PC...im using Winproxy on the other to share the connection, with full privilages for this one....any ideas?

Ta Kevbb.

---

### Post by Mustard on 2006-01-21
[QUOTE=Kevbb]Cheers for the links....I'll have a look at them soon. appreciate your help...thanks.

I changed the list to the second one you provided (without NZ) and am still getting resolving errors...." Temporary failure resolving 'security.ubuntu.com'...etc....etc,
as per my previous comment..do you think because im sharing a connection that it's causing any prob's? There's nothing downloading on the other PC...im using Winproxy on the other to share the connection, with full privilages for this one....any ideas?

Ta Kevbb.[/QUOTE]

Ah ok...well this would definitely be the problem then. :)

I would say your sources.list is fine (whichever one you use), but the internet connection sharing arrangement you have is not working.

You could put all the above error messages inside these forum codes to make it neat too. :) [noparse]```
..your code in  here
```[/noparse]

I'm not too experienced with setting up internet connection sharing, so i would suggest you start a completely new thread in the forum that deals with that problem specifically.

---

