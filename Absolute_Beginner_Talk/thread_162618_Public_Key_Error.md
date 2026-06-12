---
title: "Public Key Error"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by Reaver on 2006-04-19
I was looking into updating my repos, and reading up on editing the sources list etc etc to get the latest updates/version so i figured i'd start at step 1 with 'Sudo apt-get update' which ran fine until the end segment.

Then it threw this at me:

**W: GPG error: [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E8DDB29170188C3B**

Something to do maybe with that particular server is down or unavailable?

Can i cut it out of the updating process so that everything else gets run normally?

---

### Post by Perfect Storm on 2006-04-19
Tried this?:
```
gpg --keyserver subkeys.pgp.net --recv E8DDB29170188C3B
gpg --export --armor E8DDB29170188C3B | sudo apt-key add -

```

---

### Post by Reaver on 2006-04-20
Looks like there's a server problem..

gpg: requesting key 70188C3B from hkp server subkeys.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

that's all i get everytime i've tried it over the last few days.
Anyway to cut it out of the list when it searches for updates?

---

### Post by Perfect Storm on 2006-04-20
Try see if you can find a mirror somewhere.

If you want to cut it out of your sourcelist: 
```
 sudo gedit /etc/apt/sources.list
```

and add **#** infront of the line that makes trouble.

---

### Post by Reaver on 2006-04-20
Thanks very much. I will do :)

---

