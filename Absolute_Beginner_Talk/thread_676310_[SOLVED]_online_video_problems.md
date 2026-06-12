---
title: "[SOLVED] online video problems"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by Jeezus on 2008-01-23
I can't get online video to play through firefox. It's not asking for missing components, and the video displays... sometimes... kind of half there. but it won't play

---

### Post by rhc on 2008-01-23
Are you using Gnash or Adobe Flash player?

---

### Post by Jeezus on 2008-01-23
not sure...
how do I check?

---

### Post by nikoPSK on 2008-01-23
I'm pretty sure flash is broken for the moment. :(

---

### Post by rhc on 2008-01-23
I think so.
Just go to [http://www.adobe.com/products/flashplayer/](http://www.adobe.com/products/flashplayer/) .
Then click download now.
It's a tar.gz file.
Open it.
From terminal go to that directory.
write > ./flashplayer-installer .
then "y" and continue.

Can you make these?

---

### Post by Jeezus on 2008-01-23
can I install it as a super-user? so that it's not floating my home folder?

---

### Post by smurphy_it on 2008-01-23
Open up firefox and in the address bar type **about:plugins** and hit enter.

The first entry is shockwave.  It will tell you what you are running (adobe flash vs. gnash).

For Adobe flash, the steps below work good (in a 64 bit environment).

cd
rm .mozilla/firefox/pluginreg.dat
sudo apt-get remove flashplugin-nonfree
sudo apt-get install nspluginwrapper
wget [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
tar -xzvf install_flash_player_9_linux.tar.gz
sudo cp install_flash_player_9_linux/libflashplayer.so /usr/lib/mozilla/plugins
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
rm -rf install_flash_player_9_linux
rm install_flash_player_9_linux.tar.gz

That's it.... If flash ever stops working in firefox type the following line (without the browser running) to fix it.

sudo nspluginwrapper -u /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so

---

### Post by rhc on 2008-01-23
Where did you downloaded it and,where did you blocked?
You should be doing it?

---

### Post by rhc on 2008-01-23
You should be doing it without "sudo".

---

### Post by bwtranch on 2008-01-23
Doesn't matter if you are root or sudo or whatever, You tell it where to put the files.

---

### Post by r4ik on 2008-01-23
Or just install the deb.

[http://mirror.ne.gov/ubuntu/pool/mul....7.10_i386.deb](http://mirror.ne.gov/ubuntu/pool/mul....7.10_i386.deb)

---

### Post by Jeezus on 2008-01-23
NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.

...where is that file? I can't find it in .mozilla in my home folde, where else would it be?

---

### Post by rhc on 2008-01-23
You don't need to do anything about that alert.
It should work now.

---

### Post by Jeezus on 2008-01-23
and it does!
Hurrah!
Thanks guys

---

### Post by rhc on 2008-01-23
:)
Nope.

---

