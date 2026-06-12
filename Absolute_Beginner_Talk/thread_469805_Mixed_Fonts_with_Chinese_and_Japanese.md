---
title: "Mixed Fonts with Chinese and Japanese"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by farang on 2007-06-10
Dear forum,

I have just started on Ubuntu with 7.04 version.  I am having trouble displaying Chinese and Japanese scripts properly. Regardless of the language modes I select at login screen (either in Chinese &#22823;&#38470;, English or Japanese modes), Chinese texts are shown in mixed fonts.  An example from a Web-page is below:
```
&#20320;[COLOR=DarkOrange]&#30340;&#36523;&#24433;[/COLOR][COLOR=Blue]&#33830;&#32469;[/COLOR][COLOR=DarkOrange]&#22312;&#25105;&#24515;&#20013;[/COLOR]
A[COLOR=DarkOrange]BBB[/COLOR][COLOR=Blue]CC[/COLOR][COLOR=DarkOrange]BBBB[/COLOR]
```The short sentence is displayed in three fonts (A, B, C).  I realise font B are used in Japanese text but cannot account for the existence of A and C for Chinese-specific characters.

My question is how I can force a uniform font use and how I can select the font to be used through-out.  As a matter of fact, I am not quite happy with the Chinese fonts I've got out of the box with Ubuntu.

TIA,
F

---

### Post by FleetAdmiral74 on 2007-06-10
Have you tried setting it as default in System - Administration - Language support? There is a blue check box.

---

### Post by farang on 2007-06-10
Just updated the Language Support menu.   The Chinese interface has much satisfactory font shape but the problem persists....

---

### Post by farang on 2007-06-11
> **farang said:**
> Just updated the Language Support menu.   The Chinese interface has much satisfactory font shape but the problem persists....

I have followed the instruction given in a forum [HOWTO]("http://ubuntuforums.org/showthread.php?t=396135").  Still having the problem.  Could anyone please assist?

---

### Post by farang on 2007-06-24
bump ~

No-one out there to help me?

---

### Post by dmizer on 2007-06-24
i think the problem is that fonts B and C do not contain the character displayed in font A, and likewise for the other two.

i think you'll need to take a look at this page: [http://www.ubuntux.org/how-to-install-the-free-microsoft-truetype-fonts](http://www.ubuntux.org/how-to-install-the-free-microsoft-truetype-fonts)

this should give you more satisfactory results.

---

### Post by farang on 2007-06-25
> **dmizer said:**
> i think you'll need to take a look at this page: [http://www.ubuntux.org/how-to-install-the-free-microsoft-truetype-fonts](http://www.ubuntux.org/how-to-install-the-free-microsoft-truetype-fonts)
Among the command lines listed in the Web page, I cannot execute the following two;
```
sudo cp /etc/fonts/local.conf /etc/fonts/local.conf_backup
sudo gedit /etc/fonts/local.conf
```
This is because there is no such thing as local.conf file in the directory.

---

