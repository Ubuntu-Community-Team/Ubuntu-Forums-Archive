---
title: "Trying to update Firefox??"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by Gemok on 2008-03-03
Hi Guys
I've just started playing with ubuntu after my last XP install died and since this lappy can't handle games figured there was no need for XP anymore.

I've gotten pretty much everything up and running although flashget is a bit unreliable in WINE :( so I tried to install the firefox extension downloadthemall.  Unfortunately the version on mozillas site requires 2.0.0.8 or above and I've got 2.0.0.6. 
Easy enough to fix I thought just update firefox ..................... 
option is greyed out bugger must a be user rights thingamy 
search forum come up with a post that says open terminal and use gksudo firefox 
no prob I can do that ...... option is still greyed out :mad:
I'm pretty sure the gksudo is working as when I use that the firefox that opens has none of the bookmarks or extensions that my usual one does but its still lacking the update option.

I've tried using ubuntuzilla but had a couple of issues firstly its asks what location you want I spotted UK and being from the United Kingdom used it, mistake UK in this instance is the Ukraine. Second firefox was stuck on a random google search page opening up not my homepage.

Can anyone help me sort this update thing out?

Chris

---

### Post by rolnics on 2008-03-03
gksudo firefox only runs firefox as root / super user. i think you might be after update manager found under the system menu

---

### Post by Superkoop on 2008-03-03
Are you on 32bit or 64bit?

---

### Post by Gemok on 2008-03-03
The update manager tells me my system is up to date so I assume the lastest firefox in the repositories is 2.0.0.6 compared to mozilla's 2.0.1.2.  

I'm running on 32bit

---

### Post by Superkoop on 2008-03-03
[http://www.mozilla.com/en-US/firefox/?from=getfirefox](http://www.mozilla.com/en-US/firefox/?from=getfirefox)

Install the official firefox, that way you  can get official updates when a new one comes out for firefox.

---

### Post by Nepherte on 2008-03-03
Run firefox as root:
```
gksudo firefox
```
and choose in the menu extra > check for updates. Firefox will update itself and afterwards you can use the latest version of firefox as a normal user.

---

### Post by rolnics on 2008-03-03
> **Nepherte said:**
> Run firefox as root:
```
gksudo firefox
```
and choose in the menu extra > check for updates. Firefox will update itself and afterwards you can use the latest version of firefox as a normal user.

There you go, you learn something new everyday! Nice one Nepherte.

---

### Post by nanotube on 2008-03-03
> **Gemok said:**
> 
I've tried using ubuntuzilla but had a couple of issues firstly its asks what location you want I spotted UK and being from the United Kingdom used it, mistake UK in this instance is the Ukraine. Second firefox was stuck on a random google search page opening up not my homepage.

Can anyone help me sort this update thing out?


so, why not run ubuntuzilla again, and this time choose "en-GB" for localization?
for homepage, why not go into preferences and reset your homepage?

---

### Post by jken146 on 2008-03-03
Please don't run firefox as root!  That is extremely dangerous!  There are other ways of getting the latest build!

The latest version of firefox in the Gutsy repos is 2.0.0.12.

[http://packages.ubuntu.com/gutsy/firefox](http://packages.ubuntu.com/gutsy/firefox)

Update Manager will automatically update you to this version.  If it doesn't, take a look at System -> Administration -> Software Sources and make sure that all the repos (except Source) there are ticked).

---

### Post by Gemok on 2008-03-03
> **nanotube said:**
> so, why not run ubuntuzilla again, and this time choose "en-GB" for localization?
for homepage, why not go into preferences and reset your homepage?

In the end I did rerun ubuntuzilla with the correct localization :) but the homepage thing perhaps I wasn't clear no mater what I set the homepage to be in preferences it opened the  random (one I'd run previously) google search.  Guessing the cause of that maybe I had an instance of firefox on another desktop that wasn't shut down when I ran the ubuntuzilla script.

As for the whole just run firefox as root if you take a look at my first post :lolflag: you'll notice I tried that and it didn't enable the check for updates option

Anyway its been updated via ubuntuzilla now so problem solved for now. :guitar: oh and with the new version the update option is avaliable as root! very strange

---

### Post by nanotube on 2008-03-03
> **Gemok said:**
> Guessing the cause of that maybe I had an instance of firefox on another desktop that wasn't shut down when I ran the ubuntuzilla script.

hm, i suppose that's possible, as sort of weirdness may happen if you do that. :)

> Anyway its been updated via ubuntuzilla now so problem solved for now. :guitar: oh and with the new version the update option is avaliable as root! very strange

not strange at all. in the repositories version, they disable the "check for updates" function in firefox because you are supposed to use the repos to update. the official mozilla build has that function enabled, so that's why it works (as long as you have permissions to write to the application directory, which you do when you run as root).

jken146's advice is sound, though - don't run firefox as root /while browsing the web/. to do a check for updates, it's quite safe to do (as long as you don't go browsing while you do that).

---

### Post by Nepherte on 2008-03-04
> **jken146 said:**
> Please don't run firefox as root!  That is extremely dangerous!  There are other ways of getting the latest build!

The latest version of firefox in the Gutsy repos is 2.0.0.12.

[http://packages.ubuntu.com/gutsy/firefox](http://packages.ubuntu.com/gutsy/firefox)

Update Manager will automatically update you to this version.  If it doesn't, take a look at System -> Administration -> Software Sources and make sure that all the repos (except Source) there are ticked).
You only run Firefox as root to update it, just like you have to run Synaptic as root to update other packages.

---

