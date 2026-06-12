---
title: "Software &quot;Installation&quot;"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by scriptsales on 2007-11-12
I am wondering if there is a set of rules for installing 3rd party software. I would like to use Thunderbird as my eMail client and downloaded it from the site. I got the .tar.gz file and extracted everything expecting to see a "Setup" program. Obviously this isnt there, there isnt anything that even looks like a program to me so I am wondering if it needs installing at all in the conventional sense or do I just stick it in an appropraite location and then try running it from there?:confused:

---

### Post by overdrank on 2007-11-12
> **scriptsales said:**
> I am wondering if there is a set of rules for installing 3rd party software. I would like to use Thunderbird as my eMail client and downloaded it from the site. I got the .tar.gz file and extracted everything expecting to see a "Setup" program. Obviously this isnt there, there isnt anything that even looks like a program to me so I am wondering if it needs installing at all in the conventional sense or do I just stick it in an appropraite location and then try running it from there?:confused:

HI and maybe this link will help
[http://cutlersoftware.com/ubuntuinstall/#source](http://cutlersoftware.com/ubuntuinstall/#source)
Good luck!

---

### Post by Paul820 on 2007-11-12
Just a quick question, why are you downloading thunderbird from the website? Thunderbird is available from add/remove or through synaptic. Or is it the latest version?

---

### Post by scriptsales on 2007-11-12
> **Paul820 said:**
> Just a quick question, why are you downloading thunderbird from the website? Thunderbird is available from add/remove or through synaptic. Or is it the latest version?

I am guessing its because I didnt know about Synaptic, what is that? like add / remove programs in Windows?

In general though, is there a simple set of guidelines for installing stuff that isnt available through Synaptic or, as i fear, every time I download a program I am going to have to figure out how to install that program depndant on how the author decided to do things?

Cheers
Andy

---

### Post by Paul820 on 2007-11-12
Nearly everything you need is available through System->Administration->Synaptic Package Manager or through Applications->Add/Remove. Also have a look here: [http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by miggols99 on 2007-11-12
Synaptic is a program that lets you install and remove programs. Most apps that you'll need will be available there. A very easy way to install thunderbird:

[apt:thunderbird]("apt:thunderbird")

---

### Post by scriptsales on 2007-11-12
OK,

Found Synaptic, can't see Thunderbird on there. I can see that "thunderbird-locale-en-gb" (Menu and Message recource for Thunderbird) is installed but cant seem to find the Thunderbird "Program" under any of my "Applications" menus, I have evolution mail but just fancied using Thunderbird as I am used to that package.

I also still wonder about installing stuff that isnt listed in Synaptic. Does everything have to be done through that manager, can you add packages to it manually?

---

### Post by scriptsales on 2007-11-12
> **miggols99 said:**
> Synaptic is a program that lets you install and remove programs. Most apps that you'll need will be available there. A very easy way to install thunderbird:

[apt:thunderbird]("apt:thunderbird")

Hi, is that URL apt:thunderbird a URL or a terminal command ?

---

### Post by overdrank on 2007-11-12
> **scriptsales said:**
> OK,

Found Synaptic, can't see Thunderbird on there. I can see that "thunderbird-locale-en-gb" (Menu and Message recource for Thunderbird) is installed but cant seem to find the Thunderbird "Program" under any of my "Applications" menus, I have evolution mail but just fancied using Thunderbird as I am used to that package.

I also still wonder about installing stuff that isnt listed in Synaptic. Does everything have to be done through that manager, can you add packages to it manually?

Hi maybe this link will help
[https://help.ubuntu.com/community/ThunderbirdNewVersion](https://help.ubuntu.com/community/ThunderbirdNewVersion)
Good luck! :KS

---

### Post by KentS on 2007-11-12
Installing from source:
Most of the time:
Download source code
```
tar -zxvf PACKAGE.tar.gz
cd PACKAGE
./configure
make 
sudo make install
```

But you should look at the README (or something like that) before installing.

---

### Post by Paqman on 2007-11-12
Generally you don't download software from the developer's website in Ubuntu, but through Synaptic instead. You'll very quickly realise that it's _much_ better than the way Windows does it.

[How to install anything in Ubuntu](http://monkeyblog.org/ubuntu/installing/)

---

### Post by miggols99 on 2007-11-16
> **scriptsales said:**
> Hi, is that URL apt:thunderbird a URL or a terminal command ?
It's a URL. It's a great new feature in Gutsy that lets you install packages from the browser by clicking one of those links. Much easier than me having to type the command..by the way if you want to install something through the terminal it's

```
sudo apt-get install package-name
```

---

