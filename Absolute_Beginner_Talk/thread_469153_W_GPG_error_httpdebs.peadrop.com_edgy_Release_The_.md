---
title: "W: GPG error: http://debs.peadrop.com edgy Release: The following signatures couldn't"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by halesquad on 2007-06-09
W: GPG error: [http://debs.peadrop.com](http://debs.peadrop.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 02D40794DD385D79

I was just doing updates and got the above message 

Any ideas 

Thanks 

Stephen

---

### Post by starcraft.man on 2007-06-09
Open the terminal (Applications > Accessories > Terminal) and paste this command in.

```
wget http://debs.peadrop.com/DD385D79.gpg -O- | sudo apt-key add -
```

then

```
sudo apt-get update
```

Thats it :).

---

### Post by halesquad on 2007-06-09
Thank you very much 

I am just gob smacked by the responce time on this site 

Another brill job done 

Thanks starcraft.man

---

### Post by starcraft.man on 2007-06-09
> **halesquad said:**
> Thank you very much 

I am just gob smacked by the responce time on this site 

Another brill job done 

Thanks starcraft.man

No problem. Please remember in future that when you add third party repos, most require their own GPG keys to authenticate packages. Usually you can find instructions on the site.

Have a nice day :).

---

