---
title: "Upgrading from Dapper to Edgy"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by Headspin on 2007-03-25
I was looking at upgrading to Edgy from Dapper and when I ran the update script I got this message.

[B]Fetched 858B in 3s (282B/s)
Failed to fetch [http://theli.free.fr/packages/dists/dapper/listen/binary-i386/Packages.gz](http://theli.free.fr/packages/dists/dapper/listen/binary-i386/Packages.gz)  301 Moved Permanently
Reading package lists... Done
W: GPG error: [http://morgoth.free.fr](http://morgoth.free.fr) dapper-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8CC68B397E2E4741
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.[/B]


I ran "apt-get update" but nothing changed..

Can I go ahead or do I need to get this key thing sorted out?...   

Also looks like it was tryig to download something that no longer exsists 

**Failed to fetch [http://theli.free.fr/packages/dists/dapper/listen/binary-i386/Packages.gz](http://theli.free.fr/packages/dists/dapper/listen/binary-i386/Packages.gz)  301 Moved Permanently**

This is running pretty peachy on an IBM600x + 512mb and wireless b.
Been running for a couple of months now and do not feel any urge to return to Windows.

Thanks for any help.

:)

---

### Post by Gerg on 2007-03-25
I also have the same problem but I think it has something to do with the wireless. If you attach your computer to the outside world with an ethernet cable and try the update again it might work.

---

### Post by Headspin on 2007-03-25
Sorry for the delay.. 

I went ahead anyway..  *lol*  everything seemed pretty bad.. lots of failures.

Eventually the pain ended and I rebooted. It came back up *amazed*  and said there were 256 updates *l*  so I let it update and one more reboot and it seems to be ok now??   

Some things are better.. others were corrupted but I re-added them.  Funnily enough, the wireless card icons were all screwed up bit I still had a connection.

Anyway.. it seems to have worked.

---

### Post by jem7v on 2007-03-25
When I upgraded from Dapper to Edgy I found that a lot of things ended up really buggy.  Later, due to unrelated circumstances, I was forced to do a clean install of Edgy, and I didn't have the same problems... From now on I'm just keeping my /home folder on a seperate partition and doing clean installs whenever I move to the newest release.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) talks about /home partitions a little more.

---

### Post by zvacet on 2007-03-26
gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
gpg --export --armor KEY | sudo apt-key add -
KEY=number
In your case
gpg --keyserver hkp://subkeys.pgp.net --recv-keys  8CC68B397E2E4741

gpg --export --armor 8CC68B397E2E4741 | sudo apt-key add -

```
sudo aptitude update
```
```
sudo aptitude upgrade
```

---

