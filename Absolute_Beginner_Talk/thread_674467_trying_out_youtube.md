---
title: "trying out youtube"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by firsttimeubuntero on 2008-01-21
How can I get videos from sites like youtube to play on my browser?. I'm using firefox, and I already downloaded the "Macromedia Flash plugin" from Add/Remove applications

---

### Post by smartboyathome on 2008-01-21
Uninstall the plugin from Add/Remove, and then go to youtube and install the plugin from there.

---

### Post by billgoldberg on 2008-01-21
If you restarted firefox and it still don't work.

Try this out:

[http://linuxowns.wordpress.com/faq/#10]("http://linuxowns.wordpress.com/faq/#10")

---

### Post by firsttimeubuntero on 2008-01-21
> **smartboyathome said:**
> Uninstall the plugin from Add/Remove, and then go to youtube and install the plugin from there.

which one of the three is it? 

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

is it the tar.gz file?

---

### Post by omi291 on 2008-01-21
> **firsttimeubuntero said:**
> which one of the three is it? 

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

is it the tar.gz file?

Yeah, it's the tar file. extract it, then go to the terminal and change the directory to the location of the file. and then type in this:

./flashplayer-installer

It worked for me

---

### Post by firsttimeubuntero on 2008-01-21
> **omi291 said:**
> Yeah, it's the tar file. extract it, then go to the terminal and change the directory to the location of the file. and then type in this:

./flashplayer-installer

It worked for me

How do I change the directory to the location of the file?

---

### Post by omi291 on 2008-01-21
> **firsttimeubuntero said:**
> How do I change the directory to the location of the file?

Just use the "cd" command. for example, if i were going to change to the location lets say, /home/desktop, i would type:

cd /home/desktop

---

### Post by firsttimeubuntero on 2008-01-21
> **omi291 said:**
> Just use the "cd" command. for example, if i were going to change to the location lets say, /home/desktop, i would type:

cd /home/desktop

ok so it should be something like: cd /tar.gz

---

### Post by sports fan Matt on 2008-01-21
Can anyone shed light on why the flash player is absolutely a pain in the rear to a. install for some people and why it doesnt play nice with linux as a whole...(meaning it just seems like everytime there is a new version out it has more bugs ..etc)

---

### Post by confused57 on 2008-01-21
> **firsttimeubuntero said:**
> ok so it should be something like: cd /tar.gz
Right-click on the tar.gz you downloaded to your Desktop, select "Extract Here"...then from a terminal:
```
cd Desktop
```

then cd to the extracted directory...you can type cd,(space between cd & the directory name)  then the first few letters of the file, press tab & it should complete the file name...then you can issue the command to install:
```
./flashplayer-installer
```

---

