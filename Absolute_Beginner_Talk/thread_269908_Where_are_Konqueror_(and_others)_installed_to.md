---
title: "Where are Konqueror (and others) installed to?"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by UnknownVariable on 2006-10-02
I recently installed Konqueror using Synaptic. I started browsing as normal, and I'm pretty impressed with this browser, being a web dev myself. I passed by one of my usual sites and realized "Oh wait, I need the flash plugin, don't I?" I clicked on the little button that said I needed additional plugins, and it redirected me to the Adobe Flash Linux download page. I download the Tarbell and navigated to it in the Terminal, and it's asking for the installation path of a Mozilla, Netscape, or Opera browser. I assume it's just not listing Konqueror because that's a KDE based browser, so I also assumed if I entered the Konqueror installation path, I could install the flash player to that just as easily.

So I have two main questions:

1. Am I correct in my thinking for installing the flash player to Konqueror?
2. Where are my programs (incl. Konqueror) installed? I noticed that many of them are installed to /usr/lib, but this isn't true for Konqueror. I tried a system search, but all that was returned was a few PNGs of Konqueror's interface.

Thanks once again. :D

---

### Post by Ben Sprinkle on 2006-10-02
'/user/bin'?
Or try the application shortcut in the ubuntu meny, it should be under networking/internet.

---

### Post by jordanmthomas on 2006-10-02
Install the flash plugin for mozilla.  Konqueror automatically looks there.
If it doesn't, look in the Konqueror settings and make sure /usr/lib/firefox/plugins is on the list

---

### Post by jaboua on 2006-10-02
Konqueror uses nsplugin to use mozilla/netscape plugins - if you (as root) put the file flashplayer.xpt and libflashplayer.so into /usr/lib/mozilla/plugins (create it if it doesn't exist), konqueror should be able to detect it:

sudo mkdir -p /usr/lib/mozilla/plugins
sudo cp flashplayer.xpt libflashplayer.so /usr/lib/mozilla/plugins

Click on Settings -> Configure Konqueror -> "Plugins" tab (on the left) -> Scan for New Plugins

---

### Post by UnknownVariable on 2006-10-02
That's funny... I compared my Konqueror to the screenshot posted above, and "plugins" is the only tab that I don't have. I'll check for updates of any kind in a few minutes, see if that helps any (gotta bring the laptop to the basement for a direct router connection).

---

### Post by kerry_s on 2006-10-02
You have to install it->
sudo apt-get install konqueror-nsplugins

You proably missed that when installed konqueror

---

### Post by UnknownVariable on 2006-10-02
Lol I probably did. When installing I just went to synaptic, clicked Konqueror for install, and let the other dependancies install. I didn't check off anything else manually. Heading down to the router now to install some stuff :) Thanks for the help~

---

