---
title: "WMV file playback problem"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by wrgarrett on 2008-02-14
I posted this in Multimedia & Video but no reply so I thought I would post here and see if anyone can help.

I have Gutsy Gibbon. When I try to play a .wmv file, I get good sound but no picture. I have read every post I could find on this subject and installed all the codecs recommended and I still have sound but no picture.

I followed this thread: [http://ubuntuforums.org/showthread.php?t=491767](http://ubuntuforums.org/showthread.php?t=491767) with no positive result. I found other threads dating back to 2006 but did not follow them due to their date.

I found this one: [https://help.ubuntu.com/community/Re.../WindowsCodecs](https://help.ubuntu.com/community/Re.../WindowsCodecs)
but this error returned: william@william-laptop:~$ sudo dpkg -i w32codecs_20071007-0.0_i386.deb
dpkg: error processing w32codecs_20071007-0.0_i386.deb (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
w32codecs_20071007-0.0_i386.deb


I would appreciate any assistance please.

Additionally, after doing the fixes refereneced above, I can now no longer play any video files. I did get Totem to play one wmv file once. I have no idea why it played but it only did it once after multiple tries and has not since.

I also installed all available updates through Synaptic.

Thank you!

---

### Post by zerhacke on 2008-02-14
The no such file or directory error means you're either not in the directory you downloaded the .deb file to, or you're mistyping the name of the .deb file.

Open a terminal, cd to the directory that you put the .deb file into, and then type ls and press enter (That's a lower case LS).  Highlight the .deb filename and right click, selecting copy.  Then sudo dpkg -i, make a space, then right click and select paste.  This will ensure you're typing the name of the .deb file in correctly.

I am, of course, assuming you actually downloaded the w32codecs package.  You have to download that first before you can use the file.

---

### Post by cor2y on 2008-02-14
simplest method to this is add the medibuntu repos [www.medibuntu.org](www.medibuntu.org)) to your apt-list then you can download the and install the w32codecs via synaptic.
However if you already have the deb file, the problem is from looking at this is either you are not point to where you downloaded the file when you try to install or you are in the right directory but the filename is misspelled by you when trying to install.
The error message says no such file or directory, meaning either the location is worng or how you typed out the deb filename.

---

### Post by wrgarrett on 2008-02-14
I simply c/p the commands from the web site that I was directed to. I have no freakin' idea what I'm doing since I am brand new to Ubuntu. 

Ok, so I tried the Medibuntu suggestion by c/p the following from their web site instructions:


Ubuntu 7.10 "Gutsy Gibbon":

sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list



Then, add the GPG Key:

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

Then after the last command is executed, a long list of operations are listed and at the end is this:

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz)  302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz)  302 Found
Reading package lists... Done
W: GPG error: [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: You may want to run [COLOR="Red"]apt-get update[/COLOR] to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

Then I ran [COLOR="Red"]apt-get update[/COLOR] and got this message:
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

What does this mean? Did the package not install? I don't find it listed in Synaptic.

Thank you.

---

### Post by cor2y on 2008-02-14
you have to run apt-get as a super user aka sudo.
So that should be
```
sudo apt-get update
```
Also that error you got seems to indicate you added the wrong version of ubuntu, feisty instead of gutsy but you say you used the gutsy repo list.

---

### Post by wrgarrett on 2008-02-15
Thanks for reply, cor2y. I appreciate your help and patience.

I don't understand what you meant by I added wrong version of Ubuntu, Fiesty instead of Gutsy. Do you mean I installed Fiesty instead of Gutsy? Or that...oh, I see now! Duh! The "failed to fetch" error message! Hmmm. Well, I c/p from medibuntu website exactly because I don't trust my data entry in my old and feeble mind.

So, I go back and try again. Here is what happened, again:
Lots of informaiton lines returned then at the end:
W: GPG error: [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: Duplicate sources.list entry [http://www.getautomatix.com](http://www.getautomatix.com) gutsy/main Packages (/var/lib/apt/lists/www.getautomatix.com_apt_dists_gutsy_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

Then I sudo apt-get update again. And here is what happened, again:

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz)  302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz)  302 Found
Reading package lists... Done
W: GPG error: [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

I don't understand why reference to feisty appears in the above error msg. Do you? It is a c/p from 
[https://help.ubuntu.com/community/Medibuntu:](https://help.ubuntu.com/community/Medibuntu:)
First I c/p
sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list
Then I c/p and add sudo in front:
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
Then I run
sudo apt-get update

I did it again, twice, and still get this:

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz)  302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz)  302 Found
Reading package lists... Done
W: GPG error: [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

And still no video, no dvd player.

---

