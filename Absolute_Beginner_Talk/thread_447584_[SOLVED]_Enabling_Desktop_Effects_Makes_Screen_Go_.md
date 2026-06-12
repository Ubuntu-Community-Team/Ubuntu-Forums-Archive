---
title: "[SOLVED] Enabling Desktop Effects Makes Screen Go White"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by WorldTripping on 2007-05-18
Morning,

I have an nVidia 'GeForce4 420 Go'  graphics card in a Toshiba 'Satellite' 1.6GHz 256MB RAM laptop.

I've just installed Feisty, and cannot get the desktop effects to activate.

Using System | Preferences | Desktop Effects | Enable Desktp Effects, the screen goe white for about 30 seconds, then back to the desktop, with the Desktop Effects dialog box still in place and unchanged.

Any ideas ?

---

### Post by Acglaphotis on 2007-05-18
You have to install the driver for your card. ( system>administration>restricted drivers manager ).

-Acgla

---

### Post by WorldTripping on 2007-05-18
Cheers for the quick response.

Doing that ( System | Administration | Restricted Drivers Manager ) got me a message that I needed to install the package:

linux-restricted-modules-2.6.20-15-server

Which synaptic could not find in the repositories.

A quick Google told me that it indeed does not exist, and to install the package:

linux-restricted-modules-2.6.20-15-generic

Which does exist im my repositories ( they are on DVD's ).

This I have now done, and there is no change, the screen still whites out, then reverts to the desktop, complete with unchanged dialog box.

Any ideas ?

---

### Post by WorldTripping on 2007-05-18
[[ bump ]]

---

### Post by Terl on 2007-05-18
Search synaptic for nvidia... you need to install nvidia-glx also.

Bear in mind your system specs...I am not sure how well the effects will run for you.

---

### Post by WorldTripping on 2007-05-18
hmmm,

Cheers for that.

I did as you suggested.

The screen no longer whites out, now I get an error message saying 'Desktop effects could not be enabled'

I'm wondering whether I should give up on this one.

Any ideas ?

---

### Post by Terl on 2007-05-18
After checking around a bit trying to find out more about the laptop (guessed at the model by googling with brand and specs) it looks like it may not be up to task as it is now.  It could use a definite boost in ram.  At 256 it is sitting at the minimum for Feisty.  The graphics card (if I found the right info) is not the best.  What I found is that it is a 16MB card, not certain; I am at work so did a quick look.

I think you can run ubuntu but just not with the effects.  Could you boost the ram?

---

### Post by WorldTripping on 2007-05-18
Thanks for the reply,

I think I'm going to let this one slide,as it is a four year old laptop, and upping the RAM would be a pain.

At the moment, I can run Ubuntu, and just about get what I want done.

Still having issues with irfan-view under wine, and truecrypt running under Feisty, but they are the subject of next weeks posts.

So it looks like there is no eye-candy for me today.

Thanks for your time.

Cheers.

---

