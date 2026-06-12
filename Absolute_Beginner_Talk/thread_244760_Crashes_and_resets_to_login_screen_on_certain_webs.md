---
title: "Crashes and resets to login screen on certain website"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by DeathOnJuice on 2006-08-26
Hey, everyone. I finally got Ubuntu working on my computer using the Safe Graphics install. Since then, I have installed and enables the NVidia driver, downloaded some games (all through Synaptic), set up Wine and played N, a game ([http://en.wikipedia.org/wiki/N_%28game%29](http://en.wikipedia.org/wiki/N_%28game%29)) through it (the game was on my Windows partition, and I copied it to my home folder). Also, I started setting up XGL using a guide I found on Digg ([http://justpretending.net/wp/2006/08/14/new-and-improved-enable-xglcompiz-on-ubuntu-dapper-drake/)](http://justpretending.net/wp/2006/08/14/new-and-improved-enable-xglcompiz-on-ubuntu-dapper-drake/)).

However, after I apt-got these packages as directed in the install: compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome, I decided that since it was alpha software, I would wait to do it until later. So, I opened up Synaptic, removed these packages from the guide: compiz xserver-xgl compiz-gnome (it didn't seem smart to remove the others ones), removed the GPG key from the guide, and finally removed the repositories from the guide. I think this may be the cause of the problem; it may not have been a complete uninstall. Still, this seems like a weird cause. I'd like someone to look into it.

Anyway, ON TO THE PROBLEM! Sorry for the wall of text. I went to this site after all that (I think): numa.notdot.net which has user-created maps for the N game I mentioned earlier. At first it worked smoothly, but at one point I closed one of the multiple tabs from the site. Immediately, I saw the NVidia logo from my driver and was dropped at the login screen. I logged back in, and that problem happened several more times. Once, I clicked on a map and the machine froze entirely. I turned off the power, and the I was dropped at the login screen again the next time I went to the site. This doesn't happen to any other site or program. I'm running Firefox, Adblock Plus, and NoScript, with the cache and history disabled which all work for this site in Windows. Does anyone know what's up? Maybe I have some unheard of Linux virus that only targets the site of a relatively obscure game... Doubtful.

Sorry for the long post. Any help would be very, VERY appreciated.

---

### Post by DeathOnJuice on 2006-08-26
Bump.

---

### Post by DeathOnJuice on 2006-08-27
Bump again. I need help on this one!

---

### Post by DeathOnJuice on 2006-08-27
Here's a topic with a similar problem to mine, in case it helps:

[http://www.ubuntuforums.org/showthread.php?p=1429337#post1429337](http://www.ubuntuforums.org/showthread.php?p=1429337#post1429337)

Also, here are some errors I found in my ~/.xsession-errors:

```

(gnome-app-install:10581): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(gnome-app-install:10581): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(gnome-app-install:10581): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(gnome-app-install:10581): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(gnome-app-install:10581): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(gnome-app-install:10581): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(gnome-app-install:10581): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed
no listening object (The name org.freedesktop.AppInstall was not provided by any .service files) 
Got non-package menu entry gnome-commander.desktop
Got non-package menu entry kiso.desktop
Got non-package menu entry k3dsurf.desktop
Got non-package menu entry xchm.desktop
Got non-package menu entry grdesktop.desktop
Got non-package menu entry tsclient.desktop
Got non-package menu entry granule.desktop
Got non-package menu entry kmyfirewall.desktop

```

---

### Post by DeathOnJuice on 2006-08-27
Bump.

---

### Post by DeathOnJuice on 2006-08-28
Bump.

---

### Post by DeathOnJuice on 2006-08-28
Bump.

---

### Post by DeathOnJuice on 2006-08-28
Bump.

---

### Post by DeathOnJuice on 2006-08-28
Bump.

---

### Post by DeathOnJuice on 2006-08-28
Bump.

---

### Post by DeathOnJuice on 2006-08-30
Bump.

---

### Post by DeathOnJuice on 2006-08-30
Bump.

---

### Post by DeathOnJuice on 2006-08-31
Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump. Bump.

---

### Post by be0wulf on 2006-09-01
Bump

---

### Post by DeathOnJuice on 2006-09-02
Bump.

---

