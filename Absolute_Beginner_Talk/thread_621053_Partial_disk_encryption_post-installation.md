---
title: "Partial disk encryption post-installation?"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by xSauronx on 2007-11-23
Is this possible or will i have to reinstall from scratch? I just want my /home partition encrypted, not my entire disk

or will i have to start from scratch? and then can i *only* encrypt my /home if it has its own partition? 

thanks :)

---

### Post by daimaru on 2007-11-23
I'm not sure about the post encryption of your /home directory, but i use 
"encfs" to encrypt stuff inside my /home/<username> directory, and it works great. just google encfs. you can also use a gui app to mount your encfs folders.

---

### Post by hyper_ch on 2007-11-23
You can use this here:   [http://www.howtoforge.com/ubuntu_dm_crypt_luks](http://www.howtoforge.com/ubuntu_dm_crypt_luks)

if you already have a seperate, empty partition, just follow that guide. Once you're done, you can copy your current home files to that partition and also make sure you mount it as /home.

---

