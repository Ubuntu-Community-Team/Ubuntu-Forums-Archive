---
title: "Mplayer plugin for firefox hijacks my m3u playlists"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by cjssmo on 2006-09-25
Have been using Ubuntu for about 6 months now.  Up till now I have not had any problems with it.  But I recently updated my system as per the automatic updates.  One of these updates was Mplayer.  I have a music server which creates a M3U playlist and streams music to my computer which I usually listen to with VLC.  The problem is that now Mplayer plugin for firefox won't let the download manager let me choose which program I want to use to listen to my music.  The mplayer plugin for firefox is great for movies but crap for listening to music.  Does anyone have any suggestions

---

### Post by tharsan on 2006-10-14
I've been looking for a solution to this problem as well.

As far as I can tell, Firefox's file associations can be viewed using 'about:plugins' (type that into your address bar.)
Clearly, mplayer is registered to open my streams (from GNUMP3d) but I haven't been able to change this registration.

I've tried editing ~/.mozilla/firefox/pluginreg.dat and ~/.mozilla/firefox/<token>/mimeTypes.rdf to no avail.

Any advice?

---

### Post by kaptkaos on 2008-02-08
I have figured out how to change the default application in firefox 2.x.

First start by setting xmms as your default within Ubuntu.
Click on System -> Preferences -> Preferred Applications.
Click on Multimedia.
Click the drop down and select XMMS from the menu.  If it is not in the menu click on Custom and enter XMMS.
Click close.

Now from within Firefox.
Click Edit -> Preferences
Click the content button.
Click Manage under File Types section.

This will give you a list of files types.  
In the search field enter m3u.
Click the Change Action button.
Click the radio button for "Open with this application"
It will open a file manager window.  XMMS should be located in /usr/bin/.

This should make XMMS your default m3u play list player.

Kapt Kaos

kaptkaos.com

---

