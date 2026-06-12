---
title: "desktop effects macbook + gutsy = wow !!"
date: 2007-09-27
forum: Apple Intel Users
---

### Post by anujseth on 2007-09-27
sorry to start a thread about this but for those who havent try this ... after setting visual effects to EXTRA ... you get your normal application switcher with Alt + tab ... also now the good part 

the apple key (with the funny symbol, on either side of the spacebar) + tab gives you a front row style application switcher

apple key + 1 
apple key + 2 
apple key + 3 

give you different zoom level, in which u can move around with ur mouse pointer

---

### Post by cyberdork33 on 2007-09-27
Install the compiz configuration manager and you can adjust several other aspects of compiz-fusion:
```
sudo aptitude install compizconfig-settings-manager
```

You might also want to install emerald to get the cool window borders.

---

### Post by anujseth on 2007-09-27
nice!

---

### Post by Sain on 2007-09-28
How do you install emerald exactly? Until now I've always used Beryl which came with emerald by default...

---

### Post by cyberdork33 on 2007-09-28
> **Sain said:**
> How do you install emerald exactly? Until now I've always used Beryl which came with emerald by default...

```
sudo aptitude install emerald
```Then to have emerald replace the current window decorator hit ALT+F2 (in gnome) and use the comand:
```
emerald --replace
```which you can put in your session to start automatically each time if you want.

Note, this does not install extra themes, just the default.

---

### Post by Sain on 2007-09-28
Ok, that was easy... Thanks!

And how do I start Emerald automatically? Sorry, I guess I should have put this question in Absolute beginner section... :)

---

### Post by cyberdork33 on 2007-09-28
> **Sain said:**
> Ok, that was easy... Thanks!

And how do I start Emerald automatically? Sorry, I guess I should have put this question in Absolute beginner section... :)

Go to System > Preferences > Sessions

Click the add button

Type whatever you want for the Name (Suggest: Emerald).

put emerald --replace as the command.

Click OK

Click Close.

Now it should start each time you login.

---

### Post by dmber on 2007-09-29
emerald replaces metacity, correct?

---

### Post by malachi on 2007-09-29
Correct.

---

### Post by dmber on 2007-09-29
if i want to try emerald (i'm on feisty), but end up wanting to go back to metacity, is that easy?

---

### Post by cyberdork33 on 2007-09-30
> **dmber said:**
> if i want to try emerald (i'm on feisty), but end up wanting to go back to metacity, is that easy?

yes, just don't start emerald. If you want a nifty icon to switch between stuff like you could with beryl, search for 'fusion-icon'

---

### Post by maduranga on 2007-09-30
what repos u r using? or can u give the direct link for a guide? most repos don't hae fusion-icon. I had to install them separately as deb packages.

---

### Post by cyberdork33 on 2007-09-30
> **maduranga said:**
> what repos u r using? or can u give the direct link for a guide? most repos don't hae fusion-icon. I had to install them separately as deb packages.

I compile using git sources

---

### Post by schauerlich on 2007-10-27
When I run
```
sudo aptitude install compizconfig-settings-manager
```
It says it 
```
Couldn't find any package whose name or description matched "compizconfig-settings-manager"
```
Synaptics can't find it either. Has it changed since this was posted?

---

### Post by schauerlich on 2007-10-28
Nevermind, I figured it out. Had to enable the software sources.

---

