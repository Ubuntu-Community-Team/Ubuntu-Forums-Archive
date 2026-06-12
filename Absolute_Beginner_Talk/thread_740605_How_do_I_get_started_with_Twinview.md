---
title: "How do I get started with Twinview?"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by gatorbrit on 2008-03-30
I have installed ubuntu 7.10 on a dell PC with twin monitors running from a jaton dual video card - the card is nvidia based. 

Initially, just the left hand monitor is showing up, although the login screen appears on both screens.  

So I want to get the second monitor running and I think I need to use Twinview.  Where do I find this?  

What steps should I take to set this up?

Thanks

Rich

---

### Post by Inxsible on 2008-03-30
Press Alt+F2 and type in ```
nvidia-settings
```This will open up a new app from NVidia for monitor settings. You can set up Twinview in there.

---

### Post by gatorbrit on 2008-03-31
Thanks, I got nvidia-settings, it found both monitors but when I selected twin view the screen on both went white,  I could see something on the second monitor, but the display was unusable.  I am sure that I need to invest some time in exploring my video card settings.

---

### Post by Nythain on 2008-03-31
hmmm... where to start...
gksu nvidia-settings is a good place... gksu so it can save changes to xorg.conf... without the gksu it wont have the access it needs...

next bit of advice... use a very up to date driver... the ones in gutsy's repos just didnt do it for me... took me two days of tweaking and googling before someone pointed it out to me... with the gutsy repos, i was unable to go higher than 640x480 on the second monitor, if i could get it to come on at all... after upgrading drivers, worked like a charm...

also, make sure you make all your changes before you apply and or save... by all i mean, configure both screens, set teh right resolutions on each one, right refresh, wether you want to use twinview or seperate x sessions/screens, etc...

thats about all i got, it should work pretty good really

---

### Post by gatorbrit on 2008-03-31
Thanks, I bet it is a driver issue.  How do I go about making sure that I have the latest drivers for the card?

Thanks again

---

