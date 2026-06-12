---
title: "automatic"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by goofey24 on 2007-02-01
good evening everybody, hi taurus if you are out there. i need a link for automatic2 for dapper drake. :lolflag: :lolflag:

---

### Post by shareMenaPeace on 2007-02-01
Not sure but the official website has at leas, is drake a special release?
Ubuntu 6.06 (Dapper 386)
getautomatix.com

---

### Post by psyne on 2007-02-01
Unless I am mistaken the following should work.

Add it to the source list
```
echo deb http://www.getautomatix.com/apt dapper main | sudo tee -a /etc/apt/sources.list
```

Download the Key
```
wget http://www.getautomatix.com/apt/key.gpg.asc
```

Import the Key
```
gpg --import key.gpg.asc
```

Update the Key
```
gpg --export --armor 521A9C7C | sudo apt-key add -
```

Now you need to update your source list using the following command

```
sudo apt-get update
```

Install Automatix2 Using the following command

```
sudo apt-get install automatix2
```

---

### Post by HereInOz on 2007-02-01
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

This page gives you the list of installations.

---

