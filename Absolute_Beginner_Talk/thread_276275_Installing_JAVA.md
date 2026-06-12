---
title: "Installing JAVA"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by d4rk on 2006-10-12
YOU DO _NOT_ NEED TO READ ALL THIS (
Ok, here's the deal, I've decided to install Frostwire. Frostwire is an alternative client for Limewire, that's open source. I download Frostwire from theyr homepage, and run the file, which is a selfinstaller. The problem is that it needs JAVA installed, a quite new version of JAVA. I use the synaptic manager, but it's not registred any Java Runtime Enviroment file there. I remember it was a thread about it here, but when I search I dont get any results, so to the question:
)

HOW DO I INSTALL THE NEWEST VERSION OF JAVA ON MY UBUNTU 6.06LE SYSTEM?

---

### Post by taurus on 2006-10-12
You can either download it directly from Sun's site or you can use Automatix to install java on your machine...  You can get more info regarding Automatic at [http://www.getautomatix.com](http://www.getautomatix.com).

---

### Post by l.tambiah on 2006-10-12
See [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by d4rk on 2006-10-12
Ok, thanks a lot for response on such a short time.

---

### Post by d4rk on 2006-10-13
I install Java trough Automatix, but Frostwire still whines about that i've got an old version of Java. I remeber last time i installed frostwire, I installed everything trough terminal...

---

### Post by pay on 2006-10-13
You need to change your default java```
sudo update-alternatives --config java
```then select the one you installed.

---

### Post by d4rk on 2006-10-13
> **pay said:**
> You need to change your default java```
sudo update-alternatives --config java
```then select the one you installed.

Thank you.

---

### Post by weird_c00kie on 2006-10-13
i tried installing java through automatix and it wouldn't work. couldn't find the file or something

i did get it through synaptic though
just search for **j2re1.4** :)

---

### Post by d4rk on 2006-10-13
> **weird_c00kie said:**
> i tried installing java through automatix and it wouldn't work. couldn't find the file or something

i did get it through synaptic though
just search for **j2re1.4** :)

Use Jay's command in Terminal. Then you have to select the Java installment you installed with Automatix. I've tested it, and it works fine.

---

