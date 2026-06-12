---
title: "Installing, I get it, but I don't."
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by -Ghost9- on 2007-02-06
I've been reading and reading. I get how there are repositories and you can get a list of programs to check and install etc. But what I'm having a hard time grasping is how to use synaptic to install software I've downloaded to my desktop. Point me in the right direction?

For instance, I downloaded firefox 2 from the mozilla site to my desktop, but now don't know how to use what i've downloaded.

---

### Post by lyceum on 2007-02-06
I don't think that is how Synaptic works...

try this,

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by meng on 2007-02-06
You don't use synaptic to install software you've downloaded, the whole point of synaptic is to download and install at the same time. Anyway, I assume you're using Dapper, because Firefox 2 comes with Edgy already. And if you want to install Firefox 2 on Dapper, look here:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by lyceum on 2007-02-06
also, try this:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

"how to install anything."

---

### Post by -Ghost9- on 2007-02-06
> **lyceum said:**
> also, try this:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

"how to install anything."

Thanks. this looks helpful. My new homework assignment.

---

### Post by aysiu on 2007-02-06
> **-Ghost9- said:**
> Thanks. this looks helpful. My new homework assignment.
While that link will generally acquaint you with all typical installations, the package in particular you want (Firefox 2.0 for Dapper) is best obtained through the script multiple people have linked you to:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by -Ghost9- on 2007-02-06
> **aysiu said:**
> While that link will generally acquaint you with all typical installations, the package in particular you want (Firefox 2.0 for Dapper) is best obtained through the script multiple people have linked you to:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

yeah but this is part of my problem. everything seems directed to a repository. what if i don't want to figure out what repository to go to but know exactly the website that has what i need to download. I download it and wham, i don't know what to do with it. that's why now I need to read up on how to make things install. the dependency on repositories is frustrating to me.

---

### Post by aysiu on 2007-02-06
> **-Ghost9- said:**
> yeah but this is part of my problem. everything seems directed to a repository. what if i don't want to figure out what repository to go to but know exactly the website that has what i need to download. I download it and wham, i don't know what to do with it. that's why now I need to read up on how to make things install. the dependency on repositories is frustrating to me.
I think you're missing the point.

With all the major repositories enabled, you don't have to track down dependencies or even know what repositories a piece of software lives in. You just open up your package manager (Synaptic, Adept, Add/Remove) and search for you want, click to install it, and then it gets downloaded and installed, along with all its dependencies.

If you're facing dependency errors, you probably have a crap repositories list and should get a new one:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Having repositories is a different way of thinking, but it ultimately makes your life easier, not harder... if you're open to it. Windows and Mac make you dependent on your web browser and Google searches for finding software. The repositories make it more like online "shopping," where you just put things in your cart and check out.

In the meantime, for Firefox, use the aforementioned script.

---

### Post by confused57 on 2007-02-06
mostwanted's(monkeyblog) is excellent for installing software...aysiu also has a nice "howto":
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

I usually extract the file(tar.gz, tar.bz2, etc), cd to the extracted source file, and read the install instructions in the README file...

---

### Post by Maestro23 on 2007-02-06
> **confused57 said:**
> mostwanted's(monkeyblog) is excellent for installing software...aysiu also has a nice "howto":
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

I usually extract the file(tar.gz, tar.bz2, etc), cd to the extracted source file, and read the install instructions in the README file...

Yeah, if you are going to install something from source, reading the README file is a must.

---

### Post by -Ghost9- on 2007-02-07
i'll figure it all out. I just prefer to play before learning, and so far I haven't been able to do that. It's been an uphill battle every step of the way.

---

### Post by lyceum on 2007-02-07
> **-Ghost9- said:**
> i'll figure it all out. I just prefer to play before learning, and so far I haven't been able to do that. It's been an uphill battle every step of the way.

At first some things will seem famillar, and others will make you feel like you are on another planet. When you look back over 6 months an see how much you have learned, you will be shocked, amaized and very pleased. :)

---

### Post by -Ghost9- on 2007-02-07
> **lyceum said:**
> At first some things will seem famillar, and others will make you feel like you are on another planet. When you look back over 6 months an see how much you have learned, you will be shocked, amaized and very pleased. :)

well it only took me 3 days to actually get 6.06 installed and working properly :mad:  it can only be up from here. Now I need to figure out if I can get edgy working. video freezes everytime. I'm always curious of the system specs of these people who have 0 problems. I've had a problem at almost every step from burning the CD to installation.

---

### Post by -Ghost9- on 2007-02-07
> **lyceum said:**
> At first some things will seem famillar, and others will make you feel like you are on another planet. When you look back over 6 months an see how much you have learned, you will be shocked, amaized and very pleased. :)

well it only took me 3 days to actually get 6.06 installed and working properly :mad:  it can only be up from here. Now I need to figure out if I can get edgy working. video freezes everytime. I'm always curious of the system specs of these people who have 0 problems. I've had a problem at almost every step from burning the CD to installation to video drivers etc...

---

### Post by SunnyRabbiera on 2007-02-07
edy is called edgy for a reason.
me I would just stick to dapper, or just dist upgrade but that can kill your compy.

---

### Post by lyceum on 2007-02-07
> **-Ghost9- said:**
> well it only took me 3 days to actually get 6.06 installed and working properly :mad:  it can only be up from here. Now I need to figure out if I can get edgy working. video freezes everytime. I'm always curious of the system specs of these people who have 0 problems. I've had a problem at almost every step from burning the CD to installation to video drivers etc...

I am one of those people (sorry to rub it in). Here is my list of what works and what doesn't (I build and sell Ubuntu boxes)

works:
Western Digital hard drives (I really haven't found any that don't, but I seem to pick up more from them than anyone else)

Creative sound cards (there may be exceptions, but I have not found any yet)

Anything by Intel. I have an Intel 3D grapgics card in my laptop and Compz and Beryl work great!

Doesn't work:
The nVidia and ATI video cards by defult, but that will change with Feisty.
Broadcom WiFi cards even with the how to's here.

I have build PC's with used parts listed above with lower specs than my "top of the line" Windows box that run better on Ubuntu, and have 3D graphics to boot.

---

### Post by -Ghost9- on 2007-02-07
i'm running an amd(FX-55 chip) system with ATI. linux hates me. I built it for games on windows before ubuntu was even a word I had heard.

On the plus side the sound and internet have always worked flawlessly.

---

### Post by lyceum on 2007-02-07
> **-Ghost9- said:**
> i'm running an amd(FX-55 chip) system with ATI. linux hates me. I built it for games on windows before ubuntu was even a word I had heard.

On the plus side the sound and internet have always worked flawlessly.

I think Linux will like you better in April :D

[https://launchpad.net/ubuntu/feisty/+specs](https://launchpad.net/ubuntu/feisty/+specs)

---

### Post by -Ghost9- on 2007-02-07
w0ot. Just got edgy installed. I guess all that work does pay off, frustrating as it is.

---

