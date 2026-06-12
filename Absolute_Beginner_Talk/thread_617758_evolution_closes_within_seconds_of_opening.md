---
title: "evolution closes within seconds of opening"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by rbtprkr on 2007-11-19
I'm using evolution for my mail, today it has started closing as soon as it opens I ran evolution from a terminal and got the following message:

CalDAV Eplugin starting up ...

(evolution-2.10:17488): evolution-mail-WARNING **: ignored this junk plugin: not enabled or we have already loaded one

(evolution-2.10:17488): e-utils-WARNING **: Plugin 'Spamassassin junk plugin' failed to load hook 'org.gnome.evolution.mail.junk:1.0'
** (evolution-2.10:17488): DEBUG: mailto URL command: evolution %s
** (evolution-2.10:17488): DEBUG: mailto URL program: evolution
libnm_glib_nm_state_cb: dbus returned an error.
  (org.freedesktop.DBus.Error.ServiceUnknown) The name org.freedesktop.NetworkManager was not provided by any .service files
Segmentation fault (core dumped)

anyone?

---

### Post by jken146 on 2007-11-19
You could try backing up and then deleting your ~/.evolution directory, that's worked for me for a couple of mysterious evolution crashes.

---

### Post by dwiedenfeld on 2007-11-19
I've seen this happen, too, although usually the second time I try, it loads just fine. But I'd be curious to know what's happening, too.

Possibly related  is that whenever I load evolution it tries to do an automatic send and receive, and always fails, giving me an error message. But if I just click cancel and then do a send and receive manually, it works fine, and works fine thereafter. 

So are these two things related? Can either or both be fixed?

I've got Evolution 2.10.1 on Ubuntu 7.04.

---

### Post by stchman on 2007-11-19
> **rbtprkr said:**
> I'm using evolution for my mail, today it has started closing as soon as it opens I ran evolution from a terminal and got the following message:

CalDAV Eplugin starting up ...

(evolution-2.10:17488): evolution-mail-WARNING **: ignored this junk plugin: not enabled or we have already loaded one

(evolution-2.10:17488): e-utils-WARNING **: Plugin 'Spamassassin junk plugin' failed to load hook 'org.gnome.evolution.mail.junk:1.0'
** (evolution-2.10:17488): DEBUG: mailto URL command: evolution %s
** (evolution-2.10:17488): DEBUG: mailto URL program: evolution
libnm_glib_nm_state_cb: dbus returned an error.
  (org.freedesktop.DBus.Error.ServiceUnknown) The name org.freedesktop.NetworkManager was not provided by any .service files
Segmentation fault (core dumped)

anyone?

A friend of mine had the same problem.  He fixed it doing this.

[http://ubuntuforums.org/showthread.php?t=508158](http://ubuntuforums.org/showthread.php?t=508158)

I personally have never had this problem and have been using Evolution for over 9 months.

---

### Post by rbtprkr on 2007-11-19
Thank you stchman that did the trick.

---

### Post by cydejsn on 2008-01-14
I had the same problem with Evolution closing immediately, however, when I launched it in Terminal I got a slightly different output, leading me to believe my problem was with the RSS plugin.  Here is what worked for me:

I went into the Configuration Editor and unchecked startup_check in the  apps/evolution/evolution-rss folder.  This kept Evolution from closing immediately, but it would close when I clicked on Send/Receive.  When I looked at my RSS feeds, I found one of the Feed URLs had been mysteriously changed.  When I re-entered the correct URL, everything was back to normal.

I hope this might be able to help someone else out there! :)

---

