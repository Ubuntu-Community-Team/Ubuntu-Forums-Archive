---
title: "What is best version to install on powerpc g4 laptop?"
date: 2015-05-14
forum: Apple Hardware Users
---

### Post by Roger_Romero on 2015-05-14
I am trying to get an old laptop that was given to me to work better, so i would like to switch to ubuntu. It is a powerpc g4 1.67ghz powerbook. What os would be best (ubuntu,kubuntu, etc.) and what version would you folks recommend. I realize its not supported anymore really but anything is an upgrade over what it is running now. Any help/ advice is greatly appreciated. I am totally new to linux, but i am fairly computer savvy, and if i dont understand something, i will ask. Thanks in advance!
i can provide hardware info if necessary just let me know what info you need.

---

### Post by Lars Noodén on 2015-05-14
I'd say Lubuntu 14.04 lts.  But there are some shortcoming and you may need to follow some work-arounds during and just after installation.  

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

---

### Post by Roger_Romero on 2015-05-14
Ok i found an mage here 
[http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/)
and it says i can run it without changing my computer. Does that mean it runs in addition to the mac os?

---

### Post by bapoumba on 2015-05-14
*Thread moved to **Apple Hardware Users**.*

---

### Post by Lars Noodén on 2015-05-15
> **Roger_Romero said:**
> Ok i found an mage here 
[http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/)
and it says i can run it without changing my computer. Does that mean it runs in addition to the mac os?

Maybe you could dual boot but I have never tried it on PPC.  I've only done full installations there.  Since OS X is discontinued for PPC, I would advise against trying dual boot.

---

### Post by Roger_Romero on 2015-05-15
> **Lars Noodén said:**
> Maybe you could dual boot but I have never tried it on PPC.  I've only done full installations there.  Since OS X is discontinued for PPC, I would advise against trying dual boot.
So i download the image, burn it to disk and then. Run it from there?

---

### Post by Roger_Romero on 2015-05-15
Also that page says they are desktop images, does it make a difference that i am doing it on a laptop?

---

### Post by Lars Noodén on 2015-05-15
The desktop image will also work on a laptop but whether desktop or laptop there may be some tuning of the graphics settings needed depending on which card you have.

---

### Post by Roger_Romero on 2015-05-15
Thanks Lars, you rock. Ill try tonight and see how it goes. I have my ipad for questions if i run into issues

---

### Post by rican-linux on 2015-05-15
If you have a radeon card remember to use these parameters

```
live radeon.modeset=1 video=offb:off video=radeonfb:off radeon.agpmode=-1
```

---

### Post by Roger_Romero on 2015-05-17
> **rican-linux said:**
> If you have a radeon card remember to use these parameters

```
live radeon.modeset=1 video=offb:off video=radeonfb:off radeon.agpmode=-1
```

My laptop has an ATI Mobility Radeon 9700. Where would i enter these parameters? Before or after i install the iso? Remember i am totally new to this, thanks!

---

### Post by rican-linux on 2015-05-17
when you fist boot into the cd. take a look at **[this]("http://ricanlinux.blogspot.com/2015/03/ubuntu-mate-on-my-ibook-g4.html")**.

---

