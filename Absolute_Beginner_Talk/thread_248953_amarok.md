---
title: "amarok"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by HdK on 2006-09-01
How do I get the latest version of amarok

---

### Post by toasted on 2006-09-01
Mines 1.4.2  whats the latest and whats the difference?

---

### Post by etomic13 on 2006-09-01
system-administartion-synaptic file manager. Then click search then type in amarok then click on the checkbox click install then select apply

---

### Post by jordanmthomas on 2006-09-01
```
#kubuntu.org packages for the latest amaroK version (packages, GPG key: DD4D5088)
deb http://kubuntu.org/packages/amarok-latest dapper main
```

Append that to your source.list and then type this:
```

gpg &#8211;keyserver subkeys.pgp.net &#8211;recv-keys DD4D5088
gpg &#8211;export &#8211;armor DD4D5088 | sudo apt-key add -
sudo apt-get update
sudo apt-get install amarok

```

---

### Post by toasted on 2006-09-01
I'm running it in Gnome... is that a no-no?

also... [http://amarok.kde.org/](http://amarok.kde.org/) says the latest is 1.4.2
Thats what I have and all I have done are regular updates with my Ubuntu

---

### Post by HdK on 2006-09-01
thanx for help but it is telling me that my amarok 1.3 is the latest version and it wont update?

---

### Post by jordanmthomas on 2006-09-01
What happens if you do this?
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Jucato on 2006-09-01
How about trying the instructions from this:

[http://kubuntu.org/announcements/amarok-1.4.2.php](http://kubuntu.org/announcements/amarok-1.4.2.php)

---

### Post by toasted on 2006-09-01
Did you try what jordanthomas said?

---

### Post by HdK on 2006-09-01
Ok thank you soo much it works now, what a sweet player :D

---

