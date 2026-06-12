---
title: "Update error"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by maddot on 2007-06-27
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

I'mg getting the above error when i try to update my ubuntu system. How do i resolve it? thanks.

---

### Post by Seisen on 2007-06-27
Go into synaptic and go to Setting>Repositories and click the tab that says Authentication and click on the one that says "Ubuntu Archive Automatic Signing Key" and then click on remove. Then click on reload in Synaptic and it should redownload the key.

---

### Post by maddot on 2007-06-27
after doing that, i get the following error:

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

after clicking on return to defaults, and reloading, i get the following error again :

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

---

### Post by Seisen on 2007-06-27
Okay put this in the terminal

```
gpg --keyserver subkeys.pgp.net --recv 437D05B5
gpg --export --armor KEY | sudo apt-key add - 
```

---

### Post by maddot on 2007-06-28
sorry, for the late reply..nope... still the same badsig error.

---

### Post by Seisen on 2007-06-28
Try commenting this line 
```
http://archive.ubuntu.com feisty-security
```
in your source list then run

```
sudo apt-get update
```
then uncomment that line and run 
```
sudo apt-get update 
```
again and see if that works.

To comment the line out just do put this in front of it.

```
#
```

---

### Post by maddot on 2007-06-29
where is the sources list? :X

Edit:
Okay..that was really dumb i 've managed to solve it. I realised that i forgot to add the ntfs-3g key into my repository..lmao. But it's funny how it brings up the problem to a fiesty main key. MAybe it's a small glitch/bug. Anyway, it's cured. Thanks for your help anyway :).

---

### Post by Seisen on 2007-06-29
Okay that is weird, but at least its fixed.

---

