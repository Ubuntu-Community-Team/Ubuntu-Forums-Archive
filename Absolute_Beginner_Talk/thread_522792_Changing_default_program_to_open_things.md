---
title: "Changing default program to open things"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by Pas_sa on 2007-08-11
I am trying to stop CrossOver from opening .exe's instead of Wine.

I have tried right clicking and going to Open With and changing it to Wine but that won't work. I tried opening nautilus as root and doing it but it won't even let me select Wine from the list, or add the command 'wine'.

I tried deleting .local and .nautlius in my home directory but that did not help. Please help me out..

---

### Post by Pas_sa on 2007-08-11
Bump? Please?

---

### Post by mcduck on 2007-08-11
It's Right-click -> **Properties** -> Open With, otherwise you will just select the progaram you want to use at that time, not always.

---

### Post by Pas_sa on 2007-08-11
> **mcduck said:**
> It's Right-click -> **Properties** -> Open With, otherwise you will just select the progaram you want to use at that time, not always.

Thats what I've been doing.. it won't change once I select 'Wine Windows Emulator' over CrossOver.

It works for all my other file types.. just not .exes.. why?!

---

### Post by Pas_sa on 2007-08-11
Bump.

---

### Post by mc4man on 2007-08-11
you could try 
open with other app. then use custom command and insert
```
'/usr/bin/wine'
```

---

### Post by Pas_sa on 2007-08-11
It opens with Wine when I use '/usr/bin/wine' but it still uses CrossOver on double click. 'wine' is selected as my 'Open With' program in the properties of any EXE.... yet it still uses CrossOver..

---

### Post by Pas_sa on 2007-08-11
Bump

---

### Post by Pas_sa on 2007-08-12
Bump

---

### Post by undertakingyou on 2007-08-12
would it be so hard to select that program specifically every time?  I know how to do this in KDE.  In KDE you can choose your application preference order.  I will have to research for gnome if that is what you are using.

---

### Post by Dianoga on 2007-08-13
I just switched back to Ubuntu from Kubuntu and I am looking for this as well. KDE made it easy to make an application the default (Open With then check the Use this application every time box). Gnome doesn't appear to have such a dialog. And while it isn't terribly difficult to select an application everytime, I would expect there to be a way to make it so I don't have to. For example, Gnome thinks Firefox should be opening XML/XSLT documents. I think a text editor should as I don't ever need to view them in a browser...merely edit them.

---

### Post by mike102282 on 2007-08-13
> **Dianoga said:**
> I just switched back to Ubuntu from Kubuntu and I am looking for this as well. KDE made it easy to make an application the default (Open With then check the Use this application every time box). Gnome doesn't appear to have such a dialog. And while it isn't terribly difficult to select an application everytime, I would expect there to be a way to make it so I don't have to. For example, Gnome thinks Firefox should be opening XML/XSLT documents. I think a text editor should as I don't ever need to view them in a browser...merely edit them.

Why did you switch to Ubuntu? Weren't you happy with KDE?

---

### Post by Dianoga on 2007-08-13
I've never really been completely happy with KDE or Gnome. I really wish they could work together to find some kind of middle-ground between "Our users are stupid" and "Here is every option available ever". Yes, that is exagerating, but there it is.

As far as default applications, I just got the answer from one of my friends. Right click on the file, go to properties. Under the "Opens With" tab you will find what you are loking for.

---

### Post by Pas_sa on 2007-08-15
> **Dianoga said:**
> I've never really been completely happy with KDE or Gnome. I really wish they could work together to find some kind of middle-ground between "Our users are stupid" and "Here is every option available ever". Yes, that is exagerating, but there it is.

As far as default applications, I just got the answer from one of my friends. Right click on the file, go to properties. Under the "Opens With" tab you will find what you are loking for.

Err.. if you read my previous posts - I know this already, and have done this already but it isn't working for Wine. I go through this dialog window, set it to Wine Windows Emulator, then hit apply, but it still opens in CrossOver by default.

I have tried adding the option 'wine' command to the options too but it won't let me select that either.

](*,)](*,)](*,)](*,)](*,)](*,)

---

### Post by Dianoga on 2007-08-15
Is it possible that Crossover replaced Wine? I'm just guessing on that, but it seems like the only likely reason for you problem. Possibly wine is a symbolic link to crossover. I really don't know though.

---

