---
title: "[SOLVED] Remove Evolution"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-05-22
I was trying to remove Evolution from my system as I like Thunderbird better
when I did a 
```

sudo aptitude remove evolution

```
This is what it gave me
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  evolution-exchange evolution-plugins 
The following packages will be REMOVED:
  evolution 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 7889kB will be freed.
The following packages have unmet dependencies:
  evolution-exchange: Depends: evolution (>= 2.10.0) but it is not installable
  evolution-plugins: Depends: evolution (>= 2.10.1) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
evolution-exchange
evolution-plugins
ubuntu-desktop

Leave the following dependencies unresolved:
contact-lookup-applet recommends evolution (>= 2.0)
evolution-common recommends evolution
nautilus-sendto recommends evolution (>= 2.4)
openoffice.org-evolution recommends evolution
Score is -1803

Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.

```

Removing evolution-exchange and evolution-plugins shouldn't be a problem, but why does it wanna remove ubuntu-desktop ?

Also in the unresolved dependencies will it be ok to remove all of them since I dont intend to use Evolution ?
Why do those software *recommend* Evolution ?

---

### Post by %hMa@?b&lt;C on 2007-05-22
ubuntu-desktop is a metapackage it is fine to remove it, but if you do a dist-upgrade it is a good idea to have it installed. you should have no problem if you remove "ubuntu-desktop"

---

### Post by Sef on 2007-05-22
> Removing evolution-exchange and evolution-plugins shouldn't be a problem, but why does it wanna remove ubuntu-desktop ?

Also in the unresolved dependencies will it be ok to remove all of them since I dont intend to use Evolution ?
Why do those software *recommend* Evolution ?

Evolution is tied into the desktop, so if you remove it, you remove the desktop.  An alternative, which I did, is to remove the icon.  System > Preferences > Main Menu > Internet > unclick Evolution Mail.  (That removes the icon from the desktop.)

---

### Post by Inxsible on 2007-05-22
> **Sef said:**
> Evolution is tied into the desktop, so if you remove it, you remove the desktop.  An alternative, which I did, is to remove the icon.  System > Preferences > Main Menu > Internet > unclick Evolution Mail.  (That removes the icon from the desktop.)

Ok. So should I still remove all the packages except ubuntu-desktop and then remove the icon?

Also, what about those software that recommend Evolution ? Can I remove those packages without affecting the softwares ?

---

### Post by Inxsible on 2007-05-22
> **jeffc313 said:**
> ubuntu-desktop is a metapackage it is fine to remove it, but if you do a dist-upgrade it is a good idea to have it installed. you should have no problem if you remove "ubuntu-desktop"
So if I remove ubuntu-desktop now, will this create problems for me when I upgrade other software or the OS itself ?

And if I have to install ubuntu-desktop before the upgrade, it will probably install Evolution again, so I might as well keep it now .. I guess

I shall simply remove the icons for now as Sef suggested

Thanks

---

### Post by macogw on 2007-05-22
You can have both installed and just set Thunderbird to default.  It's not a great idea to remove ubuntu-desktop because it'll make it harder to upgrade the full OS (like Feisty -> Gutsy).  And yes, it'll re-isntall evolution if you re-install ubuntu-desktop.

---

### Post by rstana on 2007-05-23
what 'problems' I am most likely to face if I remove ubuntu-desktop? I have removed it when I removed gaim (installed pidgin)

---

