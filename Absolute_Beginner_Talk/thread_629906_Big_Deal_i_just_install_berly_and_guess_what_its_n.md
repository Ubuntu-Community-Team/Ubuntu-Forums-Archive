---
title: "Big Deal i just install berly and guess what its not working"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by sam1981 on 2007-12-02
now if someone who is out there now everything about beryl i can give him a remote access and plz make my pc look funtastic cuz i saw on you tube the video of beryl and looks  so good i and all my friend wants to see those effect so who ever is let me know and i will give you a remote access.

---

### Post by Dr Small on 2007-12-02
Remote access would be slow.
Have you tried installing beryl yet ??
[https://help.ubuntu.com/community/BerylOnFeisty](https://help.ubuntu.com/community/BerylOnFeisty)

Dr Small

---

### Post by daimaru on 2007-12-02
first what version of ubuntu are you running ( add it to your profile ). if your using gutsy, your desktop effects are already preinstalled ( as compiz ) 

the beryl project has fused with the compiz fusion project, so beryl does not exist anymore (well it does exist, but the new versions are now compiz). to get all your desktop effects up and running you have to first install the restricted drivers for your graphics card ( plz add your graphics card to your signature ) so if you have a nvidia ati or onboard stuff is going to make a difference here. most work out of the box but some onboard chips need some tweaking. 

to get full desktop effects you have to install the " advanced desktop effects settings " to do this type this in terminal or search for it within synaptic.

```
sudo apt-get install compizconfig-settings-manager
```after install you'll find it under system->preferences->advanced desktop effects settings

---

### Post by sam1981 on 2007-12-02
no but i installed it 
and i have beryl icon next to my clock and the theme icon on administration but can not select any theme

---

### Post by Dr Small on 2007-12-02
Beryl still exists, but it just isn't avaliable for Gutsy. It's in the Feisty repositories.

---

### Post by overdrank on 2007-12-02
> **sam1981 said:**
> no but i installed it 
and i have beryl icon next to my clock and the theme icon on administration but can not select any theme

It would help if you could tell us some system specs and which version of ubuntu you are using fesity, gutsy?

---

### Post by sam1981 on 2007-12-02
i have a version 7.10 and if its not gonna work on the latest version then how do i remove it?

---

### Post by daimaru on 2007-12-02
> **Dr Small said:**
> Beryl still exists, but it just isn't avaliable for Gutsy. It's in the Feisty repositories.
yes yes yes thank you for correcting me again. it does still exist, but if you read the info on the beryl page you do know that beryl has become compiz now dont you....dr smart.:popcorn:

> Beryl and Compiz (at least the extra plugins division of compiz) have merged. Please all welcome Compiz Fusion!

---

### Post by Hospadar on 2007-12-02
right-click the beryl icon and go to "choose window manager" (or something like that) and choose beryl.

Also, what video hardware are you using and are you using the accelerated drivers for them? (you will need to be)

---

### Post by sam1981 on 2007-12-02
well i am very very new to linux so just tell me that it should work or not ?

---

### Post by Dr Small on 2007-12-02
> **daimaru said:**
> yes yes yes thank you for correcting me again. it does still exist, but if you read the info on the beryl page you do know that beryl has become compiz now dont you....dr smart.:popcorn:
Yes, yes. I heard and knew that beryl was being disolved and was from then on going to be compiz-fusion, but to openly say that beryl doesn't exist would be a falsehood, wouldn't it :D

That's like saying, the titanic doesn't exist, because it hit the iceberg, but in reality, it still exists, but it lays dormant on the bottom of the ocean :)

Dr Small

---

### Post by daimaru on 2007-12-02
@dr small
sry mate, got carried away there. :) no offense
but to try and help sam. you should uninstall beryl and use compiz since your on gutsy, and since i dont have beryl installed and dr small has he can probably help you out there. I would only suggest searching for beryl in synaptic and removing it, but i dont really know what you did to install beryl. as i remember from my ati days i had to set up the xgl session and all that stuff so i m at a loss here.

---

### Post by Dr Small on 2007-12-02
> **daimaru said:**
> @dr small
sry mate, got carried away there. :) no offense
but to try and help sam. you should uninstall beryl and use compiz since your on gutsy, and since i dont have beryl installed and dr small has he can probably help you out there. I would only suggest searching for beryl in synaptic and removing it, but i dont really know what you did to install beryl. as i remember from my ati days i had to set up the xgl session and all that stuff so i m at a loss here.
No problem ;)
If he is running Gutsy instead of Feisty, then his best bet would be to attempt to get Compiz-Fusion working properly, instead of Beryl, as you stated.

---

