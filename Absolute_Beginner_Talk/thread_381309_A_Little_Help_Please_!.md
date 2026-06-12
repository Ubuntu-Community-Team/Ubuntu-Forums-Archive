---
title: "A Little Help Please ?!"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by HunkieChan on 2007-03-10
ok i just installed ubuntu, abonding my life long windows... i love it, but one problem one my video card, i guess, **when i scroll the window, it lags. **please, help me

---

### Post by Bachstelze on 2007-03-10
You need to install proper drivers for your graphics card. What maker/model is it ?

---

### Post by HunkieChan on 2007-03-10
> **HymnToLife said:**
> You need to install proper drivers for your graphics card. What maker/model is it ?

i tell you now, please dont go anywhere, oops, how do i find it in ubuntu ? its nvidia, thats all i know

---

### Post by Bachstelze on 2007-03-10
Everything you need is there :

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by HunkieChan on 2007-03-10
> **HymnToLife said:**
> Everything you need is there :

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

thanks alot, dont go anywhere, i might need you

---

### Post by Repent on 2007-03-10
If that didn't help try this [http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717) it's easy and fast.

---

### Post by dhughes on 2007-03-10
I agree **Envy** is a great tool for people new to Linux, it's a simple install and it does all the work needed to get your video card drivers installed correctly.  

 The Envy website has a great step-by-step explanation of how to install it too. the only freaky part after the Envy application install is when you have to type "envy" in Terminal and the screen goes black, but after that it's quite self-explanatory all you do is pick a number 1 for Nvidia and 2 for ATI  or the other way around, but you'll see it.


 Then as a new user you can pick away at things you don't know about and not worry about messing around with xorg.conf and other bizarre new Linux experiences.

---

### Post by HunkieChan on 2007-03-10
> **Repent said:**
> If that didn't help try this [http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717) it's easy and fast.

love you man ill use it now, thanks

---

### Post by HunkieChan on 2007-03-10
do i need to install nvidia, is that why my screen lags ?

---

### Post by Bachstelze on 2007-03-10
Yes. Your X Server is most probably configured to use the old vesa driver. If you don't want to go through all the hassle of installing the nvidia driver though, you can use the nv driver, which is shipped with Ubuntu. It is an open source driver for nvidia cards, which will not give you full 3D acceleration but is perfectly sufficient for desktop tasks.

---

### Post by HunkieChan on 2007-03-10
hey 
with envy, after i do the installion in the terminal .. i do what it asks me to do i press cntrl alt and f1.. then it takes me to a black screen..is there why i type envy ? please

---

### Post by HunkieChan on 2007-03-10
i did it... i did it.. LETS PARTY.. WAAWAAWEEWEE

---

