---
title: "mplayer update not authenticated"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by stoogiebuncho on 2008-03-29
n00b here,

Some new updates for mplayer popped up on my machine today, but when I went to install them, the update manager told me that the updates could not be authenticated.

The updates that could not be authenticated are  mplayer-doc and mplayer-nogui.

I've looked around a little and it looks like this might have something to do with the GPG key, but, being a n00b, I don't know what that means or what to do about it.

Suggestions?

---

### Post by zvacet on 2008-03-29
```
sudo apt-get update
```

---

### Post by mrsteveman1 on 2008-03-29
Perhaps you have a 3rd party repo installed but haven't installed the signing key from that repo?

---

### Post by FuturePilot on 2008-03-29
Sometimes all you need to do is run
```
sudo apt-get update
```
but if you've added a third party repo like Medibuntu you need to make sure you have the gpg key for it.

---

### Post by fela on 2008-03-29
you don't actually _need_ the GPG key, if you trust the source then go ahead and download from it.

---

### Post by stoogiebuncho on 2008-03-29
I ran the apt-get update.  This is what I get back (after the normal stuff).

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: [http://playonlinux.botux.net](http://playonlinux.botux.net) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E7F12A5C79BB7A6
W: You may want to run apt-get update to correct these problems

So it looks like the problems are with medibuntu and playonlinux (which I was pretty sure I had removed from my system already).

Any tips on how to get these GPG keys?

---

### Post by mrsteveman1 on 2008-03-29
These will grab the gpg keys and install them:
```
wget -q http://playonlinux.botux.net/pol.gpg -O- | sudo apt-key add -
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```

Afterward update apt again:
```

sudo apt-get update
```

---

### Post by stoogiebuncho on 2008-03-29
Thanks, everyone, that's got it.

---

