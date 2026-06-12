---
title: "Java Runtime Environment"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Repent on 2007-04-21
How do I install this?


/home/joe203/Desktop/jre-6u1-linux-i586.bin


Thanks.

---

### Post by SOULRiDER on 2007-04-21
You REALLY should check out the guides on how software works and how it can be installed in Ubuntu. [https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)


To install the JRE you can type:
```
sudo apt-get install sun-java6-jre
```

---

### Post by taurus on 2007-04-21
Applications -> Accessories -> Terminal
```
cd ~/Desktop
chmod 755 jre-6u1-linux-i586.bin
sudo ./jre-6u1-linux-i586.bin
sudo update-alternatives --config java
```

---

### Post by Repent on 2007-04-21
I had all the installs I have done in a folder so I would not have to ask anymore but the last upgrade wiped out my hard drive so I lost everything sorry.

---

