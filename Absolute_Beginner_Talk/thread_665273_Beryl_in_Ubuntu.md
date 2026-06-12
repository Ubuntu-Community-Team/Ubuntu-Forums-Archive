---
title: "Beryl in Ubuntu"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by Masterpooboo on 2008-01-12
I am really an absolute beginner.... Sorry if my problems are not worthy, but they're problems nonetheless:

I am running Ubuntu 7.04

I have downloaded Beryl and Emerald which both installed just fine. 

None of the changes that I make in the beyrl manage seem to take effect. Can someone explain what is going on.

Secondly, I would like to have my windows "burn up" when I close them and "Ripple" when I choose them Can someone explain how I can choose  these settings.

I appreciate the help.

Just to let any potetial answerers know, I am dedicated (although only at it for a week) to learning all I can about this new world of Linux that I have stubbled upon, so your assistance is not in vain!

thanks, Masterpooboo

---

### Post by barrack on 2008-01-12
Once beryl is installed, to run it type "beryl" in a terminal. Apps>Accessories>Terminal

To have it always on upon log in, add it to your start up programs in System>Preferences>Sessions.

To get those effects you want, you'll need to install the package called beryl-manager. If you were able to install beryl, I think you should be able to get the manager installed too.

---

### Post by ggaaron on 2008-01-12
Just a note - beryl is dead, it has been merged with compiz and now you should use compiz fusion.

---

### Post by Masterpooboo on 2008-01-12
I have Beryl-Manager already installed, the problem is that I can't seem to make any of the settings that I put in work. That's my problem.

If it's dead and I should use compiz fusion, should I uninstall beryl and then install compiz fusion? Does it have the same features and do i have to pay attention to any special things.

Thanks!

---

### Post by Malta paul on 2008-01-12
Hi, If it was me I would install Ubuntu 7.10 because as mentioned Compiz is now the best and will work well with your video card
Good luck:)

---

### Post by ggaaron on 2008-01-12
It probably has even more features, certainly the ones you want. I'm not using ubuntu, but it should work the same, I start compiz using:

(LIBGL_ALWAYS_INDIRECT=1 compiz --replace ccp &) && (emerald --replace &)

Probably you don't have to uninstall beryl first, but it is unsupported for more than a year.
You can read more about compiz and beryl on wikipedia, for example:
[http://en.wikipedia.org/wiki/Beryl_%28window_manager%29#Beryl-Compiz_Merge](http://en.wikipedia.org/wiki/Beryl_%28window_manager%29#Beryl-Compiz_Merge)

---

