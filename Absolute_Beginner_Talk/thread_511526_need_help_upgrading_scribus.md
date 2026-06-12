---
title: "need help upgrading scribus"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by orwellus on 2007-07-27
Hello:

I need some help upgrading scribus. I have Edgy and  I installed the scribus available from add/remove which is 1.2. something and I would like to upgrade to a later version, if possible. I will confess I am not very good at complying packages. So, I was wondering if someone had some commands I could cut and paste into the terminal, or could provide me some instructions. I seemed to remember that you had to install something into Synaptic, but I am at a loss to know what that is. Any help would be appreciated.

---

### Post by RomeReactor on 2007-07-27
Hi. What version of Scribus do you have? enter this in the terminal (Applications->Accessories->Terminal) to see the exact version:
```
apt-cache show scribus | grep Version
```
The [Scribus site]("http://www.scribus.net/") is down at the moment, so I couldn't see what version they are offering now. I have Scribus 1.2.5.dfsg-5ubuntu3 installed in Feisty. Also, to compile, the package you need is Build-Essential:
```
sudo apt-get install build-essential
```

---

### Post by yorkie on 2007-07-27
latest version is 1.3.3.9 
I`m not sure but Idon`t think you can upgrade to latest version check with site when available

---

### Post by orwellus on 2007-07-28
Thank you for the replies. I installed scribus from edgy's add/remove section. The version I have installed is 1.2.4.1.dfsg-1ubuntu5. I could have swore I saw something about upgrading scribus, but I think it is on that scribus web-site which is down.

---

### Post by orwellus on 2007-07-28
I am replying to my own post. I think I figured it out. I went into Synaptic and did a search for Scribus. Four things came up. I uninstalled the box marked scribus (right click, then Mark for Removal). That removed Scribus 1.2.4. Then I installed the box marked scribus-ng (right click, then Mark for Install). And now I have Scribus 1.3.3.6 which shows up in the Applications menu under Graphics. Pretty neat. Doesn't have any pre-configured templates though.

---

### Post by RomeReactor on 2007-07-28
You could install **scribus-ng**, which is a development branch and supposedly has more features. You can find it in Synaptic,Add/Remove (search for **scribus** and look at the description) or from the terminal:
```
sudo apt-get install scribus-ng
```
You would have the newest version if you download it from its site, but are you certain you need the absolute newest version? What new features does it have that are not available in your already installed version? And since the one you have is specifically packaged for Ubuntu, installing the one from their site could be a little buggy, and even introduce a security risk or two. This is just speculation, though.

**EDIT**: I see you already installed scribus-ng...

---

### Post by orwellus on 2007-07-28
It looks like you and I are on the same wavelength. Yeah I like that Scribus-ng a lot better.

---

