---
title: "is there any Chinese here? Need help with Chinese input on Dapper Drake"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by babyboss on 2006-07-03
Hello... I am trying to get my Chinese input to work on Dapper Drake. I followed ubuntuguide.com instruction, but it's not working. Ctrl+ space does not change the input method, and I can't input chinese under Openoffice word. I looked up the ubuntu wiki for SCIM input for Chinese, Japanese and Korean. However, the page does not exist yet.
Thanks for helping.

---

### Post by MaximB on 2006-07-04
did you installed the chinese language pack ?

---

### Post by drtvasudevan on 2006-07-04
[QUOTE=babyboss]Hello... I am trying to get my Chinese input to work on Dapper Drake. I followed ubuntuguide.com instruction, but it's not working. Ctrl+ space does not change the input method, and I can't input chinese under Openoffice word. I looked up the ubuntu wiki for SCIM input for Chinese, Japanese and Korean. However, the page does not exist yet.
Thanks for helping.[/QUOTE]

right click on the panel and choose add to panel.
under utilities you find keyboard indicator. click onthat to add it to the panel
when you want to switch you just click on this icon (or letters USA as in my pc) 
it changes to the next kbd you have selected.
post Q here for further help with scim though i used it to enable only my own language.
once you have got the hang of it write that wiki

---

### Post by elfgoh on 2006-07-12
Hey check out this guide here: It looks pretty solid. I'll try it in a few days time when I'm free.

[http://www.mrbass.org/linux/ubuntu/scim/](http://www.mrbass.org/linux/ubuntu/scim/)

---

### Post by Blur-king on 2006-07-12
I followed the guide and it work. After the quick setup, I had to also apply the instruction for the topic on "additional configuration if you are not using a CJK session". 
I then to set up my Openoffice by going to Tools -----> Options----> language settings i enabled the Asian lang and complex text layout.
I then went to Asian text layout and chose Chinese simplified.
My Scim icon showed up on my panel and i also did some setup changes as i had many versions of the chinese fonts activated initially. 
I am sorry if I am not able to give a clearer help as I am new to all this but  this works for me. &#19981;&#35201;&#25918;&#24323;

---

### Post by Blur-king on 2006-07-12
Hi guys i just managed to install the SCIM in another box. The instructions are right. Firstly you need to go the language support to install the chinese language. As we are using English menu we need to apply the second part ie activate the im switch. Follow the instruction in the docs, it will prompt you that you need " libapt-pkg-perl " , just sudo aptitude install it and repeat the im command again, now it will promt you to install " scim-qtimm " , sudo aptitude install this and run the im switch command again. Then logout and relogin. The scim icon should in the panel. You can then fine tune your setup by clicking on the icon. And yes I think there may not be a need to reconfigure Open Office as mention in my earlier post. Remember that you need to logout and then login before you can see any changes to the  SCIM.  cherio  guys.

---

### Post by drtvasudevan on 2006-07-13
> **Blur-king said:**
> H. Follow the instruction in the docs, it will prompt you that you need " libapt-pkg-perl " , just sudo aptitude install it and repeat the im command again, now it will promt you to install " scim-qtimm " , 

seems kubuntu is better in this respect.
it install the qtimm by default.
also some more language support.

tv

---

### Post by tilai on 2006-09-01
> **Blur-king said:**
> Hi guys i just managed to install the SCIM in another box. The instructions are right. Firstly you need to go the language support to install the chinese language. As we are using English menu we need to apply the second part ie activate the im switch. Follow the instruction in the docs, it will prompt you that you need " libapt-pkg-perl " , just sudo aptitude install it and repeat the im command again, now it will promt you to install " scim-qtimm " , sudo aptitude install this and run the im switch command again. Then logout and relogin. The scim icon should in the panel. You can then fine tune your setup by clicking on the icon. And yes I think there may not be a need to reconfigure Open Office as mention in my earlier post. Remember that you need to logout and then login before you can see any changes to the  SCIM.  cherio  guys.

Hmm, it works except with my aMSN, even after logging out and back in, I can't get the pinyin to work although SCIM is showing pinyin input.

---

### Post by paker on 2007-01-07
Please explain these instructions in plain English for me. I clicked on all links, but couldn't understand what they meant. Someone said "rock solid instructions" but they are foreign language to me. Please help me understand im-switch, where to enter these commands. Many thanks in advance.

---

