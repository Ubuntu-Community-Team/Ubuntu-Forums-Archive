---
title: "update"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by reston5 on 2008-03-28
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9

suggestions on what to do so I can upgrade to 8.04 I read another post and added the key but didnt help anything

---

### Post by Oldsoldier2003 on 2008-03-28
> **reston5 said:**
> W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9

suggestions on what to do so I can upgrade to 8.04 I read another post and added the key but didnt help anything

Change the download source in System >Administration> software sources
then

```
sudo apt-get update
sudo apt-get dist-upgrade
```

if apt doesn't upgrade you you can try 

```
sudo update-manager -c
```
or 
```
sudo upate-manager -d
```

---

