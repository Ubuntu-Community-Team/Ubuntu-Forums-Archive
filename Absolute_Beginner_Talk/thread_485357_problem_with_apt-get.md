---
title: "problem with apt-get"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by hayzam on 2007-06-26
actually i am new inhere ... 
and i tried installing a package called " sun-java6-jre " , anyway .... during the installation i stuck with a blue screen containing Configuring Package  . OS Distributer licencse of java and the terms of agreement .. etc

and now , i cant break using Ctrl+C nor q nor anything ....
and i dont know how to tell them I DAMN AGREE , PLZ COMPLETE installation and let my apt-get working properly ...

coz even if i close the terminal , i cant do apt-get upgrade and tells me that the dpkg interrupted  ...

need help urgently

Thanks in Advance

---

### Post by Nekiruhs on 2007-06-26
This is a common issue, does it say a command when you try and run apt-get? try running that. just copy and paste it.

---

### Post by hayzam on 2007-06-26
yeah " dpkg --configure -a "

---

### Post by Nekiruhs on 2007-06-26
> **hayzam said:**
> yeah " dpkg --configure -a "
Then just run ```
sudo dpkg --configure -a

```
You have to go through the installation process for Java again. You have to use the arrow keys, right key I think, to select the I accept button.

---

### Post by hayzam on 2007-06-26
yeah ........ thank you man

---

