---
title: "apt-get update - NO PUBKEY"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by cmol on 2007-03-04
Hello..

When i run apt-get update, I get these errors:

```
W: GPG error: http://medibuntu.sos-sts.com edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: http://download.tuxfamily.org edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 576856718434D43A
```

So then i ran (googled the problem and found [http://medibuntu.sos-sts.com/repository.php):](http://medibuntu.sos-sts.com/repository.php):)

```
sudo wget http://medibuntu.sos-sts.com/sources.list.d/edgy.list -O /etc/apt/sources.list.d/medibuntu.list
```

I now i get:

```
W: GPG error: http://medibuntu.sos-sts.com edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: http://download.tuxfamily.org edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 576856718434D43A
W: Duplicate sources.list entry http://dk.archive.ubuntu.com edgy/universe Packages (/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_edgy_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://medibuntu.sos-sts.com edgy/free Packages (/var/lib/apt/lists/medibuntu.sos-sts.com_repo_dists_edgy_free_binary-i386_Packages)

```


What to do?

---

### Post by superpelican on 2007-03-04
cmol,

All you have to do is:
```
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
```

That should get the key and you should be in busniess... 

You may have to run the following agian:
```
sudo wget http://medibuntu.sos-sts.com/sources.list.d/edgy.list -O /etc/apt/sources.list.d/medibuntu.list
```

It's all on the link you posted... [http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

Hope this helps you out.

-Dave

---

### Post by cmol on 2007-03-05
> **superpelican said:**
> cmol,

All you have to do is:
```
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
```

That should get the key and you should be in busniess... 

You may have to run the following agian:
```
sudo wget http://medibuntu.sos-sts.com/sources.list.d/edgy.list -O /etc/apt/sources.list.d/medibuntu.list
```

It's all on the link you posted... [http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

Hope this helps you out.

-Dave

Thanks Dave :-)

Now i just need the second key?

error:
```
W: GPG error: http://download.tuxfamily.org edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 576856718434D43A

```

---

### Post by TonKi on 2007-03-05
[Have a look here]("http://download.tuxfamily.org/3v1deb/index.html")

If thats the repository you are using

---

### Post by Nythain on 2007-03-05
wget [http://3v1n0.tuxfamily.org/DD800CD9.gpg](http://3v1n0.tuxfamily.org/DD800CD9.gpg) -O- | sudo apt-key add -
if you are shooting for this repo
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy 3v1n0

---

### Post by cmol on 2007-03-05
> **Nythain said:**
> wget [http://3v1n0.tuxfamily.org/DD800CD9.gpg](http://3v1n0.tuxfamily.org/DD800CD9.gpg) -O- | sudo apt-key add -
if you are shooting for this repo
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy 3v1n0

Ran:

```
wget -q http://3v1n0.tuxfamily.org/DD800CD9.gpg -O- | sudo apt-key add -
```

(it stoped without the -q).........

But the error is still there..

Looked in my scources.list, found this:

```
deb http://download.tuxfamily.org/syzygy42 edgy exaile
```

Does that help?

---

### Post by TonKi on 2007-03-05
Open a terminal, and type the following, replacing KEYSTRING with one of the long sets of letters and numbers returned by Synaptic/Apt (576856718434D43A):

Code:
gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys KEYSTRING

This should give you another code, something like 1F41B907. Enter this command, replacing KEYSTRING2 with the new one.

Code:
gpg --armor --export KEYSTRING2 > keyName.gpg

This will give you a file containing the gpg key. Use this command to add it.

Code:
sudo apt-key add keyName.gpg

---

### Post by cmol on 2007-03-05
> **TonKi said:**
> Open a terminal, and type the following, replacing KEYSTRING with one of the long sets of letters and numbers returned by Synaptic/Apt (576856718434D43A):

Code:
gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys KEYSTRING

This should give you another code, something like 1F41B907. Enter this command, replacing KEYSTRING2 with the new one.

Code:
gpg --armor --export KEYSTRING2 > keyName.gpg

This will give you a file containing the gpg key. Use this command to add it.

Code:
sudo apt-key add keyName.gpg

Brilliant :D

Thanks for the help :-)

---

