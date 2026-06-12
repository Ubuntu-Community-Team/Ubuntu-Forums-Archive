---
title: "Block (almost) all sites from 1 (young) user and other child account questions."
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by SunnyM on 2006-10-29
So I broke down and made an account for my daughter, as she's always banging away at my keys anyways. I want to set it up so she can only go to pre-approved sites without affecting everyone else on the computer. pbskids is fine, but I don't want her surfing the web, you know? Is there anyway to accomplish this?

I'd also like to prevent her doing things that would permanently damage her account or the computer, such as accessing admin functions or deleting icons. 

Last, but not least, I'd like to keep her from editing the menu/accessing some of mommy's programs. (*cough*Drug Wars*cough*) And have read only access to some folders in my secondary hard drive (such as backgrounds), and no access to others.

Huge thanks in advance, and any other advice on how to make her new computer access a good experience for everyone is also very appreciated.:KS

---

### Post by WiseElben on 2006-10-29
What you can do is set up your child's browser settings to connect via a proxy like [Squid Proxy]("http://www.squid-cache.org/"), which will only allow your child to access the websites you approve (whitelist).

EDIT: [Here is the article I got Squid Proxy from.]("http://applications.linux.com/article.pl?sid=04/12/03/1720204&tid=37&tid=49&tid=113")

---

### Post by Sef on 2006-10-29
> I'd also like to prevent her doing things that would permanently damage her account or the computer, such as accessing admin functions or deleting icons.

Don't give her admin persmissions when setting up the account.  It is off by default on other accounts.

---

### Post by SunnyM on 2006-10-30
Sorry about that, for some reason our internet dies every Sunday night. *sighs*

I'm trying out squid now, and the other advice seems ok, although I'm not sure how that would work should I need to set something up for her. Any ideas on the last part about totally hiding some programs?

Edit: Does anyone know a good site that could baby me through setting up squid?

---

### Post by bodhi.zazen on 2006-11-01
Try using a hosts file. It is very easy and blocks all that stuff.

Here is a how-to. At the bottom is a link to a script that will download and update your hosts file automatically.

[hosts](http://ubuntuforums.org/showthread.php?t=241460)

---

### Post by pbaehr on 2006-11-01
> **SunnyM said:**
> Any ideas on the last part about totally hiding some programs?


I'm fairly sure (I only have one account on my computer) if you remove an entry from the applications menu while logged on to your daughter's account it shouldn't have any impact on your menu. Just right click on the "Applications" menu and select the edit option. Then untick any items you don't want it to show.

---

### Post by raqball on 2006-11-01
if you are using FF I think there is also an extension you can add that does the same. I can't remember the name right now but if you are interested I will find it for you and post a link :)

EDIT: The FF plugin will not stop aceess to files but can filter the web..

---

### Post by bodhi.zazen on 2006-11-01
> **raqball said:**
> if you are using FF I think there is also an extension you can add that does the same. I can't remember the name right now but if you are interested I will find it for you and post a link :)

EDIT: The FF plugin will not stop aceess to files but can filter the web..

I think you are referring to Adblock plus and Filterset.G updater.

These are primarily for add blocking and work only with FF.

A hosts file works better because it works not just with FF, but also with **all other browsers**.

---

### Post by raqball on 2006-11-01
> **bodhi.zazen said:**
> I think you are referring to Adblock plus and Filterset.G updater.

These are primarily for add blocking and work only with FF.

A hosts file works better because it works not just with FF, but also with **all other browsers**.

You are correct! Good find and thanks for flashing me back to when I had to block my munchkin :)

---

### Post by bodhi.zazen on 2006-11-01
> **raqball said:**
> You are correct! Good find and thanks for flashing me back to when I had to block my munchkin :)

Welcome ;)

PS hosts file works as an adblock as well as filters content.

If it blocks a site you need:

copy (backup) your origional hosts file.```
sudo cp /etc/hosts /etc/hosts.org
```

Install new hosts file, copy (backup) your heavy duty hosts file.```
sudo cp /etc/hosts /etc/hosts.adblock
```

Disable hosts blocking```
sudo cp /etc/hosts.org /etc/hosts
```[indent]_I plead the 5th_[/indent]

Re-enable hosts```
sudo cp /etc/hosts.adblock /etc/hosts
```

No need for any type of reboot for changes to take effect.

8)

---

### Post by Klaidas on 2006-11-01
Just curious... how old is she? It seems that you are trying to restrict computer usage to only a few programs and lock everything else...

---

### Post by echo $USER on 2006-11-01
Enter tinyproxy...

[http://ubuntuforums.org/showthread.php?t=122011&highlight=tinyproxy](http://ubuntuforums.org/showthread.php?t=122011&highlight=tinyproxy)

---

