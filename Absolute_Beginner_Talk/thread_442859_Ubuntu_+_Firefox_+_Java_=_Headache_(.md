---
title: "Ubuntu + Firefox + Java = Headache :("
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by tonycm1 on 2007-05-13
Alright... I have the newest update of Firefox and have been trying to manually install Java with no success.... I am new to linux (and Ubuntu) so I'm not too sure what i'm doing wrong here....

Here's what I've done so far:
-Downloaded java (jre-6u1-linux-i586.bin)
-went to [http://java.com/en/download/help/5000010500.xml#selfextracting](http://java.com/en/download/help/5000010500.xml#selfextracting) and followed instructions there to extract bin
-went to [http://java.com/en/download/help/5000010500.xml#enable](http://java.com/en/download/help/5000010500.xml#enable)

I'm having problems in the "enabling" phase..... can anybody point me to the right direction for doing this with firefox?

:)

---

### Post by nonewmsgs on 2007-05-13
[http://www.getautomatix.com/](http://www.getautomatix.com/)

it has java right there and i think even the FF plugin for it.

---

### Post by [S|G] on 2007-05-13
You can install java from Ubuntu's repository with apt:
```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

---

### Post by Grungydan on 2007-05-13
If I'm not mistaken, a trip to a website that you know uses Java will cause Firefox to prompt you for installation of the required plugins.

Might be worth a try.  Good luck!

---

### Post by tonycm1 on 2007-05-14
> **nonewmsgs said:**
> [http://www.getautomatix.com/](http://www.getautomatix.com/)

it has java right there and i think even the FF plugin for it.

I'm trying to follow the instructions here except after hitting step 6 in the installation ([http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_on_.28K.2CX.29Ubuntu_6.10_i386.2CAMD64_.28Edgy.29](http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_on_.28K.2CX.29Ubuntu_6.10_i386.2CAMD64_.28Edgy.29)) I get a screen in terminal that is a blue screen that says "Ubuntu Configuration" at the beginning and says "Configuring sun-java5.bin" in red and the has what looks like a legal disclaimer and an "OK' button at the bottom.... except how do I click on this OK button to continue while in terminal??? I'm so confused.... all I want is for java to work :(

---

### Post by [S|G] on 2007-05-14
press "tab" to select the OK button and then press enter

---

### Post by tonycm1 on 2007-05-14
> **Grungydan said:**
> If I'm not mistaken, a trip to a website that you know uses Java will cause Firefox to prompt you for installation of the required plugins.

Might be worth a try.  Good luck!

Your right, except it doesn't do an installation automatically and the manual installation isn't working for me :( any ideas?

---

### Post by canadianwriterman on 2007-05-14
I believe you just hit the tab key to reach the OK button, then press enter.

---

### Post by n0dl on 2007-05-14
Do not use automatix! You'll never learn *nix that way. What enabling phase are you talking about? What's the step number?

---

### Post by tonycm1 on 2007-05-14
> **canadianwriterman said:**
> I believe you just hit the tab key to reach the OK button, then press enter.

haha... don't i feel silly.... that worked! thanks :) hopefully this works....

---

### Post by canadianwriterman on 2007-05-14
No problem... I was puzzled by the same thing.

---

### Post by tonycm1 on 2007-05-14
> **tonycm1 said:**
> haha... don't i feel silly.... that worked! thanks :) hopefully this works....

Excellent! It worked.... i'm kind of dissapointed I had to rely on Automatrix to get this working.... I really want to learn linux without relying on other software packages....

---

### Post by jrusso2 on 2007-05-14
Oh boy its really hard to install the "correct way using synaptic".  What is the difference?

---

