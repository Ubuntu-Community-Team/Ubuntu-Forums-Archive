---
title: "Why does synaptic download *entire* packages after few days?"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by Turin Turambar on 2006-01-20
The title explains it all...
I guess this is easy question, yet I'm having troubles every few days, because Synaptic says then that it cannot find source files and then downloads them all. That's a real pain for me, because I'm still on dial-up!

---

### Post by matthew on 2006-01-20
There is a setting in Synaptic that should remedy this for you. 

Open Synaptic. Choose Settings->Preferences
Select the Files tab
Under Temporary Files choose the option titled Only delete packages that are no longer available

You will use more disk space, but you won't have to re-download packages all the time, unless they are updated.

---

### Post by Turin Turambar on 2006-01-20
No, it's not that. The problem are *source* files - the lists, you know "universe", "restricted", "main", etc files!
When I click on "reload", Synaptic updates them in seconds. However, after few days, Synaptic says that it cannot find those files so it downloads them entirely. And that's about 3megs!

Thanks anyway! :)

---

### Post by hen3rz on 2006-01-20
> No, it's not that. The problem are *source* files - the lists, you know "universe", "restricted", "main", etc files!
When I click on "reload", Synaptic updates them in seconds. However, after few days, Synaptic says that it cannot find those files so it downloads them entirely. And that's about 3megs!

That isnt always a bad thing.. By updating its list of packages it insures you have the latest of every program and will make sure you dont try download a program that is old or doesnt exist any more in the repositories.

---

### Post by morphodone on 2006-01-20
hen3rz is right,

however, if you want to avoid this you can use the console command apt-get

apt-get install packagename

---

### Post by Turin Turambar on 2006-01-20
It's ok to just update files - I do that myself with "reload", but I don't like when it downloads them entirely from scratch. That's what I'm talking about here. :) I would like to avoid that.

---

### Post by dueY on 2006-01-20
[QUOTE=Turin Turambar]It's ok to just update files - I do that myself with "reload", but I don't like when it downloads them entirely from scratch. That's what I'm talking about here. :) I would like to avoid that.[/QUOTE]

When you reload you are downloading them again from scratch.  :confused:

---

### Post by Turin Turambar on 2006-01-20
[QUOTE=dueY]When you reload you are downloading them again from scratch.  :confused:[/QUOTE]

No. When I click on reload, it just updates the package (source list). 
However, every few days when I enter the Synaptic program, it says that it cannot find the source files. Only then, when I click on reload it starts downloading them from scratch! That's so annoying - why it deletes the source packages?

Huh, I thought this was a simple question.  :lol:

---

### Post by az on 2006-01-20
[QUOTE=Turin Turambar]No. When I click on reload, it just updates the package (source list). 
However, every few days when I enter the Synaptic program, it says that it cannot find the source files. Only then, when I click on reload it starts downloading them from scratch! That's so annoying - why it deletes the source packages?

Huh, I thought this was a simple question.  :lol:[/QUOTE]
They only get reloaded (redownloaded) when they change.  The breezy-updates and the security updates get changed often.

You can comment out the updates and security updates sources.  The main, universe, multiverse and restricted from plain 'ol breezy should not change.

---

### Post by Aliby on 2008-03-28
> **matthew said:**
> There is a setting in Synaptic that should remedy this for you. 

Open Synaptic. Choose Settings->Preferences
Select the Files tab
Under Temporary Files choose the option titled Only delete packages that are no longer available

You will use more disk space, but you won't have to re-download packages all the time, unless they are updated.

I have seen this option, but have no idea as how to trigger the "clean up"?
I thought it may be automatic, but when I use the console it cleans out more.
```
apt-get autoclean
```

How does it work?
:confused:

---

