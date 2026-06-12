---
title: "GPG Keys for Dummies"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by Hoary on 2006-09-01
Having somehow screwed up sources.list within my brand new Kubuntu, I followed advice in another thread and had "source-o-matic" build me a replacement.

I have a question about what to do with GPG keys. Source-o-matic does warn:
 
> When a repository in this list has a GPG key, you may need to add that to the APT trusted keys. You can do this with the following commands (replace KEY with the key ID) 
 gpg --keyserver subkeys.pgp.net --recv KEY
 gpg --export --armor KEY | sudo apt-key add - 

Sure enough, I need to enter the GPG key for the Kubuntu repositories. Source-o-matic does provide it: DD4D5088. Not understanding what I was doing, I typed in:

> 
 gpg --keyserver subkeys.pgp.net --recv DD4D5088


but was told:

> 
gpg: keyring `/home/peter/.gnupg/secring.gpg' created
gpg: requesting key DD4D5088 from hkp server subkeys.pgp.net
?: subkeys.pgp.net: Connection refused
gpgkeys: HKP fetch error: Connection refused
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0


Should I just keep trying? (I did try a bit later: same result.) Or did I make some mistake there?

What I really need is Japanese input. I hope that this is available via "ubuntu-desktop-ja", advertised for Ubuntu [here](http://www.ubuntulinux.jp/download), which says I should add:
 
> deb [http://archive.ubuntulinux.jp/ubuntu-ja](http://archive.ubuntulinux.jp/ubuntu-ja) dapper/
deb [http://archive.ubuntulinux.jp/ubuntu-ja](http://archive.ubuntulinux.jp/ubuntu-ja) dapper-ja/

I need a GPG key for this too. However, it's not mentioned on the download page (where I'd expect to see it), and search results for that site don't seem to say anything useful about a GPG key.

(Well I hope that the Japanese input package -- when I manage to get it -- works with Kubuntu. If it only works with Ubuntu, I'm up a certain creek.)

Comments, help, advice, contumely?

---

### Post by Hoary on 2006-09-02
Hmm, the problem seems to have evaporated by itself. Anyway, I can download the stuff I want, and I've Japanesified this system.

---

