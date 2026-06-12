---
title: "Adding Repositiries in Synaptic"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by FreakShow! on 2006-11-28
I'm trying to install Wine, but for some reason the synaptic Package Manager won't do it. I copied the link into the custom source, but it gives an error of:
"Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences."

I know that the internet is working so why will it not find these updates?

When I click close on that window, another one comes up saying the following:
"The following problems were found on your computer:
W: GPG error: [http://ubuntu.moshen.de](http://ubuntu.moshen.de) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC0A1CC62F30665"

I have a feeling that this might be an issue with synaptic itself as it can't seem to add any extra repositires that I try (can't remember which ones I added)

Any ideas?

TIA :)

---

### Post by KingBahamut on 2006-11-28
Youll need to add the proper keys for access to that repository. The person who hosts it should be able to help you. 

You see this sort of deal with some repos an example below would be the case -- 

# kubuntu.org packages for the latest KDE version

deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) edgy main
deb [http://kubuntu.org/packages/kde-355](http://kubuntu.org/packages/kde-355) edgy main
deb-src [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) edgy main

GPG Key Information

wget [http://www.kubuntu.org/announcements/kubuntu-packages-jriddell-key.gpg](http://www.kubuntu.org/announcements/kubuntu-packages-jriddell-key.gpg) | sudo apt-key add

kubuntu-packages-jriddell-key.gpg

---

### Post by FreakShow! on 2006-11-28
EDITED: I have found the issue to be that Ubuntu is searching for a amd64 version of the file and it seemingly doesn't exist. Is there a way to force it to use a 32bit version or maybe to try and compile it's own version of 64bit Wine?

TIA :D

---

