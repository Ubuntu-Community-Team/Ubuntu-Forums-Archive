---
title: "Japanese and Chinese language packs for Gutsy"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by KevNice on 2007-10-28
Any guides out there on this?

I want to install a Japanese language pack with romaji input, and a Chinese language pack with BuPuMuFu input. What do I need to do?

Cheers yet again,
Kev

---

### Post by KevNice on 2007-10-28
bumpety bump

---

### Post by japtar10101 on 2007-10-28
install UIM and anthy. ```
sudo apt-get install uim-applet-gnome uim-xim uim-anthy uim-gtk2.0
```
Directions are in this web page: [https://help.ubuntu.com/community/JapaneseInput](https://help.ubuntu.com/community/JapaneseInput)

---

### Post by nrfool on 2007-10-28
I don't how to add japanese input method, but here is how to add chinese, I assume add japanese will be a similar process.
Step 1:
**System->language support->select "Chinese"**, apply
Step 2:
Then **go to SCIM input method setup**,** IMEngine->Chinese** (traditional/simplified/or both)->**choose the input method**.
(I think that your "BoPoMFu" input is labeled **&#8220;&#26234;&#33021;&#25340;&#38899;"** in Chinese.)
Hit **apply**.
I don't remember exactly, but I think you will need to **restart ubuntu** either after step 1 or step 2.

---

### Post by chang47 on 2007-10-30
BoPoMFu is chewing.

---

### Post by KevNice on 2007-10-30
thanks guys, got it all sorted it out.
cheers!

kev

---

### Post by cstoh on 2007-11-03
> **KevNice said:**
> thanks guys, got it all sorted it out.
cheers!

kev

What exactly did you do to sort out the problem? Which of the above advise did you use? Please share in detail.

---

### Post by serador on 2007-11-04
> **cstoh said:**
> What exactly did you do to sort out the problem? Which of the above advise did you use? Please share in detail.

This one worked for me.

```
sudo apt-get install uim-applet-gnome uim-xim uim-anthy uim-gtk2.0
```

Add it to panel and choose Anthy.

---

### Post by cstoh on 2007-11-06
> **japtar10101 said:**
> install UIM and anthy. ```
sudo apt-get install uim-applet-gnome uim-xim uim-anthy uim-gtk2.0
```
Directions are in this web page: [https://help.ubuntu.com/community/JapaneseInput](https://help.ubuntu.com/community/JapaneseInput)

Does´t work for me. I get this message
cstoh@cstoh-desktop:~$ sudo apt-get install uim-applet-gnome uim-xim uim-anthy uim-gtk2.0
[sudo] password for cstoh:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package uim-applet-gnome
cstoh@cstoh-desktop:~$ sudo apt-get install uim-applet-gnome

What next. please help

---

### Post by cstoh on 2007-11-09
> **japtar10101 said:**
> install UIM and anthy. ```
sudo apt-get install uim-applet-gnome uim-xim uim-anthy uim-gtk2.0
```
Directions are in this web page: [https://help.ubuntu.com/community/JapaneseInput](https://help.ubuntu.com/community/JapaneseInput)

Following your online command did not work for me. I tried using the synaptic package manager to look for all uim software but it returned a very long list. Finally I managed to install all the required modules by searching for ¨pinyin¨in the synaptic package manager. Then I followed  the link given in the directions page and it worked. Now I am so happy.

Thanks a million

---

