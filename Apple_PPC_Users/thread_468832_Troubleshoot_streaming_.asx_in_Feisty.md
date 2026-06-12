---
title: "Troubleshoot streaming .asx in Feisty"
date: 2007-06-09
forum: Apple PPC Users
---

### Post by thedarky on 2007-06-09
Howdy,

Does anyone have an idea how I can further troubleshoot this?

System:  eMac USB2.0 - 1.25  running Feisty, all video and sound runs well from optical media (congrats to the community!) and streaming Real audio also works well. 
No streaming Real or Windows video works.
Streaming radio, from .pls playlists works well in Rhythmbox. 

I am not interested in getting streaming video running, because it's not something I need, but streaming audio is pretty much integral to my web use  - - and it seems do-able for a newbie.

This is the url I want to run a stream from:
[http://www.abc.net.au/rn/allinthemind/audio/aim_09062007_28M.asx](http://www.abc.net.au/rn/allinthemind/audio/aim_09062007_28M.asx)

These are the web plugins listed from the about plugins command in Firefox:



/usr/lib/totem/libtotem-basic-plugin.so
/usr/lib/totem/libtotem-gmp-plugin.so
/usr/lib/mozilla/plugins/libvlcplugin.so

The vlc plugin lists handling of windows media video asx files.

The Firefox media handling prefs are set for VLC to handle a lot of windows media looking things but not asx. Mediaplayer(totem) doesn't get listed to handle it either.


I get the idea from the Restricted Formats community description that I need the restricted codecs but what I don't get is how to find the windows ones. (which if course I would only use if it is legal in my country).

I added the medibuntu repos to my update manager, ready for whatever. But I don't have a clue how to proceed.  That windows codecs package referred to all over the ubuntu documentation just seems to  be missing everywhere.

The behaviour of Firefox when I address the url is to open the required embedded player in a new window, with the activity described as "Read www.abc.net.au"  and after leaving the window and returning,  it reads "stopped.

I tried opening the url directly in the VLC player and it seemed to parse the link down to a mms protocol and then stalled.

What the next step I can take to troubleshoot this please?

---

### Post by thedarky on 2007-06-10
Think I'll leave this one alone; I've got all the medibuntu codecs possible, but none of the media players, including VLC can handle that kind of file.  
Probably a lack in the ppc codec bundle, because I've read that some intel hardware owners are getting asx files running in Feisty.

---

### Post by stmiller on 2007-06-10
.asx is sort of a metafile that stores the playlist of the windows audio stream files.

> access_mms: failed to open a connection (tcp)
access_mms: cannot connect to server
access_mms: cannot connect to media3.abc.net.au:80
main: no suitable access module for `mms://media3.abc.net.au/rn/mod/aim_09062007_28M.asf'
main: no suitable decoder module for fourcc `undf'.
VLC probably does not support this sound or video format.
access_http: error: HTTP/1.1 416 Requested Range Not Satisfiable
access_http: seek failed


Looks like it's a valid windows media 9 stream that VLC can read, but the encoder that ABC uses for the audio is not one which VLC has a decoder for. 'undf' is VLC's way of saying "I don't know what codec this is." Very weird. 

Mplayer might be able to play this. Let me see...

---

