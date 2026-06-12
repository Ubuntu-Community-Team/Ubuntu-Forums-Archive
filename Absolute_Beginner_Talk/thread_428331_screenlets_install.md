---
title: "screenlets install"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by shadowboxer_k on 2007-04-30
hey,

my machine is pretty weak - 128RAM, 20 GB harddisk - and i don't think it could manage beryl. i do, however, want to make it a bit prettier so i'd like to install screenlets. my question might be a bit silly, but do i need beryl to run screenlets?

thanks.

---

### Post by renzokuken on 2007-04-30
i dont know the answer to that but more than likely you can yes.

a couple of alternatives that DO work without beryl are 'gdesklets' (gnome) and 'superkaramba' (KDE)

---

### Post by khughitt on 2007-04-30
You should be able to install screenlets without beryl / compiz. If you want to make your desktop look nice- if you havn't already, i would start at [www.gnome-look.org](www.gnome-look.org) and art.gnome.org, and try to find a nice-looking theme and background to use. Then you can change your fonts for some nicer looking ones, change the image for the gnome panel if theme does not do it for you. That will take you a long way without too much effort.

goodluck!

---

### Post by shadowboxer_k on 2007-04-30
i've spent a good chunk of time customizing my desktop and i've frocked it up quite nicely :) the only thing that's missing are some tchotchkes on the desktop - namely the screenlets. 

can i be a pain in the *** and ask how does one install them on feisty? thanks again.

---

### Post by khughitt on 2007-04-30
Easiest way is to add the repository to your sources.list file

**sudo gedit /etc/apt/sources.list**

Add the line:
> deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty screenlets

then, execute these two commands in a terminal
**wget [http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg](http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg) -O- | sudo apt-key add - && sudo apt-get update**
**sudo aptitude install screenlets**

That should do the trick! Check out [http://hendrik.kaju.pri.ee/screenlets/?q=node/5](http://hendrik.kaju.pri.ee/screenlets/?q=node/5) which has installation instructions, and says basically the same as above.. Also try [http://hendrik.kaju.pri.ee/screenlets/](http://hendrik.kaju.pri.ee/screenlets/) to see some more screenlets you can download.

goodluck :)

---

### Post by mumushi on 2007-05-02
> **pwnedd said:**
> Easiest way is to add the repository to your sources.list file

**sudo gedit /etc/apt/sources.list**

Add the line:


then, execute these two commands in a terminal
**wget [http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg](http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg) -O- | sudo apt-key add - && sudo apt-get update**
**sudo aptitude install screenlets**

That should do the trick! Check out [http://hendrik.kaju.pri.ee/screenlets/?q=node/5](http://hendrik.kaju.pri.ee/screenlets/?q=node/5) which has installation instructions, and says basically the same as above.. Also try [http://hendrik.kaju.pri.ee/screenlets/](http://hendrik.kaju.pri.ee/screenlets/) to see some more screenlets you can download.

goodluck :)

tried it and everything did well. thanks alot... :)

---

### Post by khughitt on 2007-05-02
Cool. Glad everything worked :)

---

### Post by lepz on 2007-05-02
How do you get the weather code for places outside America? hmmmm like London UK ;)

---

### Post by -sands-o-time- on 2007-05-24
Google to Weather.com
In the local weather search bar enter your city name i.e London. From the list choose London U.K
Once the page with the London weather appears look at your address bar. Left click,hold and scroll
the address to the end. There you will see the code for that area, in this instance, London U.K, it
should be UKXX0085. Enter that code into your weather screenlet as required.
Bit of a late reply but suppose it might help anyone else looking for same info.

Good Luck
Sands

---

### Post by GlennW on 2007-07-26
This thread has been invaluable.  Thanks to all the contributors! Being a newb to Ubuntu, I can dutifully follow terminal commands and the like but now that I've got screenlets downloaded from hendrik's, where do I find them on my machine? I've got compiz fusion running. I see now that Beryl has re-emerged (after removing a long time ago due to a bad attitude). What does Beryl have to do with the screenlets? 

Some clarification would be very helpful. Thanks.

---

