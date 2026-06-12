---
title: "Repository problems on update"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by gerrymoth on 2007-04-10
I'm getting the following when checking for updates, is this a temp or perm thing?

```
The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
http://gb.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.bz2: MD5Sum mismatch
http://gb.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.bz2: MD5Sum mismatch
http://gb.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.bz2: MD5Sum mismatch
http://gb.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.bz2: MD5Sum mismatch
http://gb.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.bz2: MD5Sum mismatch
```

---

### Post by mac.ryan on 2007-04-10
To me, it looks like the files on the server have been signed with a different key that the one needed for the authentication...
EDIT: ...this can be due to a variety of reasons, amongst others:
[LIST]
[*]a mistake by the repo mantainers
[*]transmission error
[*]updated keys
[*]malicious attack on ubuntu's GB repos
[*]...[/LIST]

---

### Post by mac.ryan on 2007-04-10
Given [other users]("http://ubuntuforums.org/showthread.php?p=2433073") are experiencing the same, I would go for the first hypothesis...

---

### Post by gerrymoth on 2007-04-11
> **mac.ryan said:**
> Given [other users]("http://ubuntuforums.org/showthread.php?p=2433073") are experiencing the same, I would go for the first hypothesis...

Thanks, I'll try again tomorrow.

---

### Post by zvacet on 2007-04-11
```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by unibuntu on 2007-04-26
That did not do it for me.
And I am now getting the MD5Sum mismatch problem on other downloads as well such as Thunderbird...

How can I revert back too Edgy???

3 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 2106kB of archives. After unpacking 28.7kB will be used.
Do you want to continue? [Y/n/?] Y
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main tzdata 2007e-0ubuntu0.7.04 [314kB]
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main gnome-panel 1:2.18.1-0ubuntu3.1 [499kB]
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main gnome-panel-data 1:2.18.1-0ubuntu3.1 [1293kB]
Fetched 2106kB in 10s (199kB/s)                                                                                                                               
E: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2007e-0ubuntu0.7.04_all.deb:](http://gb.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2007e-0ubuntu0.7.04_all.deb:) MD5Sum mismatch
nitscheu@core2duo:~$ 


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/m/mozilla-thunderbird/mozilla-thunderbird_1.5.0.10-0ubuntu3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/m/mozilla-thunderbird/mozilla-thunderbird_1.5.0.10-0ubuntu3_i386.deb)
  MD5Sum mismatch

---

### Post by Seisen on 2007-04-26
Have you tried removing "gb" from your repo's and trying?

---

### Post by unibuntu on 2007-05-12
> **Seisen said:**
> Have you tried removing "gb" from your repo's and trying?

Yes, I tried the US servers, no change. 

I found someone had posted a bug report but it was closed immediately by the team with some b&$%!* about the servers being overloaded..

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/107817](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/107817)

That prompted me to immediately return to Edgy - which I now have and it is working fine thank you very much.

No idea what was causing that but until I read about a solution I am staying on Edgy.
Maybe we'll see some Apple adds soon about the pain of upgrading Ubuntu ;-)

---

### Post by Najand on 2007-05-12
Try:
```

sudo apt-get clean && sudo apt-get autoclean && sudo apt-get update

```
and try again.

---

### Post by Nanoboy on 2007-05-29
Just having the same problems in updating after reinstalling a fresh feisty, and using my old /home from a separate partition.

Just tried:
```
sudo apt-get clean && sudo apt-get autoclean && sudo apt-get update
```

No change...

---

### Post by zvacet on 2007-05-29
Can you 

```
cat /etc/apt/sources.list
```

and post it here

---

### Post by Nanoboy on 2007-05-29
I think it was just some (great britain?) server problem...  I used the "Select best server" button in synaptic package manager:
>Settings >Repositories
In the Ubuntu Software tab, under the Download from list, click "other..."

 and after it did some testing, it found a Portugal server for me, which upon connect, downloading packages no problems and quick!!!

---

