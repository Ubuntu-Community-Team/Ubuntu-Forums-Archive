---
title: "Mplayer plugin not recocgnized by Firebird for Quicktime embeds ..."
date: 2006-12-16
forum: Apple PPC Users
---

### Post by magnolia fan on 2006-12-16
I'm not having any luck getting Firebird to recognize that the Mplayer plug-ins are installed.  I used Synaptic to install them and they're all in the plugin and component folders where they belong, but embedded Quicktime trailers always give me Totem error messages when the page loads.  I'm trying to make changes in Edit -> Preferences -> Content ->  Manage file types, but there are no other plugin choices for Quicktime .  It only offers the "QuickTime Plug-in 6.0 / 7" option and nothing else.

I've seen a few posts where people have had success, so it must be possible to make it work.  Any ideas?
Thanks

---

### Post by magnolia fan on 2006-12-16
:D  Found a solution for this one today.  I ended up uninstalling Firefox and then re-installing it using Synaptic Package Manager.  I then re-installed the mplayer plug-in as well.  Now Firefox brings up the mplayer interface when visiting links from the Apple Quicktime Trailer page.  There seems to be an issue with installing FireFox 2.0 over the last release when upgrading to Edgy that prevents Firefox from using the plugin.

There was still an issue with the mplayer plugin not wanting to show video on embedded clips right away until I unchecked and rechecked some of the preferences while it was playing.  I've solved this issue by adding  the line, "noembed=1" to the /etc/mplayerplug-in.conf file.    This forces the movie clips out into a small movie window that will scale if you drag the corners.  Not too shabby.

---

### Post by chinocracy on 2007-01-01
Hmm, don't know if it's appropriate to ask it here, but have you tried to view trailers on Yahoo's movie page? I'm trying to view the Transformers 2nd trailer there, but it doesn't work. I wonder how to make that work in Firefox. Thanks.

---

### Post by chinocracy on 2007-01-01
Uh, forgot to say... I already have the Mplayer plugin. I also got Mediaplayer Connectivity... Still doesn't work. Maybe the plugins get confused.

---

