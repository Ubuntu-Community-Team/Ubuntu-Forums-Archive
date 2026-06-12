---
title: "how to update firefox?!?"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by fyrestarre512 on 2007-06-14
Hello everyone.  I'm a total noob when it comes to linux/ubuntu.
Finally got my system to connect to the internet...
now...
how in the world do I update firefox?
i downloaded the newest version, but I can't seem to figure out how to install it.  Can anyone give me explicit directions on this or send me somewhere that can?
i really like the linux op sys, and am trying my hand at something new.  
Thanks for the help.

---

### Post by Rocket2DMn on 2007-06-14
You should be able to run
```
sudo apt-get install firefox
```
Updates will be available through
```
sudo apt-get update
```
I thought firefox came built in, but I could be wrong (Applications->Internet).

---

### Post by klytu on 2007-06-14
> **fyrestarre512 said:**
> Hello everyone.  I'm a total noob when it comes to linux/ubuntu.
Finally got my system to connect to the internet...
now...
how in the world do I update firefox?
i downloaded the newest version, but I can't seem to figure out how to install it.  Can anyone give me explicit directions on this or send me somewhere that can?
i really like the linux op sys, and am trying my hand at something new.  
Thanks for the help.

What version of Ubuntu did you install? If it's Edgy 6.10 or Feisty 7.04, then you'll get the latest Firefox automatically (I think ...) after you have installed all the updates. If you are using Dapper 6.06 LTS, take a look at these sites:

[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla)
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

I would recommend you follow the instructions at the site in the first link. In other words, **don't try to install the downloaded package directly**. If you really want to do that, read the info in the second link about manually updating Firefox - **read it carefully**.

---

### Post by kittyhawk63 on 2007-06-14
> **fyrestarre512 said:**
> Hello everyone.  I'm a total noob when it comes to linux/ubuntu.
Finally got my system to connect to the internet...
now...
how in the world do I update firefox?
i downloaded the newest version, but I can't seem to figure out how to install it.  Can anyone give me explicit directions on this or send me somewhere that can?
i really like the linux op sys, and am trying my hand at something new.  
Thanks for the help.

Automatix2 will install it and give you the very latest version 2.0.0.4

---

### Post by kittyhawk63 on 2007-06-14
> **fyrestarre512 said:**
> Hello everyone.  I'm a total noob when it comes to linux/ubuntu.
Finally got my system to connect to the internet...
now...
how in the world do I update firefox?
i downloaded the newest version, but I can't seem to figure out how to install it.  Can anyone give me explicit directions on this or send me somewhere that can?
i really like the linux op sys, and am trying my hand at something new.  
Thanks for the help.

You can also click on Help in Firefox and choose "check for updates."

---

### Post by NoobieDoobieDo on 2007-07-06
> **kittyhawk63 said:**
> You can also click on Help in Firefox and choose "check for updates."

It's grayed out.

---

### Post by p_quarles on 2007-07-06
> **NoobieDoobieDo said:**
> It's grayed out.
It's grayed out because Firefox in Ubuntu is a custom build. Canonical releases security updates for it on a regular basis, but it doesn't track with every version released by Mozilla.

In other words, if you're looking for Firefox 3.0, you're not going to get it from the package manager. It's still in Alpha anyway, so if you don't know how to compile it from the source, you should probably stay away from it.

---

### Post by daktari on 2007-07-07
> **p_quarles said:**
> 
It's grayed out because Firefox in Ubuntu is a custom build. Canonical releases security updates for it on a regular basis, but it doesn't track with every version released by Mozilla.

In other words, if you're looking for Firefox 3.0, you're not going to get it from the package manager. It's still in Alpha anyway, so if you don't know how to compile it from the source, you should probably stay away from it.

@ quarles: 
If that info isn't part of a master guide on LTS/Firefox, it *should* be.

Related:
To complicate matters, Automatix has broken sporatically in some LTS platforms with the following error msg (quote):
[I]Automatix WILL NOT run because of the repository GPG
keys could not be downloaded and further operation
might result in a breakage.  Try again later.[/I]

/ End of Post /

---

### Post by macogw on 2007-07-07
Don't use Automatix.  Automatix is, to put it nicely, "frowned upon."

And what did you think "stable" meant?  If they went around adding new versions of things all willy-nilly they'd be introducing more bugs left and right, and nobody wants that!

---

