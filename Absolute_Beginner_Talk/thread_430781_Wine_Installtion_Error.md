---
title: "Wine Installtion Error"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by Chris Kent on 2007-05-02
Good afternoon, fellow Ubuntu Enthusiasts!

I am a newbie who JUST finished installing Ubuntu on a Lenovo T42 and I was trying to get Wine to install.  I keep receiving an error after using the sudo apt-get update command

"W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems"

Anyone know what I gotta do to get over this hump? (Yes, I DID perform the "apt-get update" command :))

Thanks a billion, guys, I am loving this OS.

---

### Post by Cypher on 2007-05-02
I think you forgot the key step of getting the GPG key..Here are the [instructions]("http://winehq.org/site/download-deb")..
Do
```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -

```
then
```

sudo apt-get update

```
and then
```

sudo apt-get install wine

```

---

### Post by Chris Kent on 2007-05-02
I am pretty sure I did it, but I will try it again.  Thanks, Cypher.  I'll let you know!

---

### Post by Chris Kent on 2007-05-02
Fark.  It worked.  I don't know how I overlooked that first one, but thanks regardless!

---

### Post by Cypher on 2007-05-02
That step is fairly easy to forget, but when you get any errors related to authentication, that's your key that the GPG file is missing. Anytime you add a new repository to your sources.list file, remember that there is always a GPG file that goes with it..

But, good that it's working now..enjoy Wine..

---

