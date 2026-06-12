---
title: "Default Firefox behaviour on files (mp3s)"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by qprfact on 2007-07-01
Whenever I click on an MP3, I get the options of "Play with Totem (default)" or Save.

I want the latter to be my default, but the option to "Do this action on files like this from now on" is greyed out.

How can I change this default behaviour?

---

### Post by pyros on 2007-07-01
For some file types you can go to Edit>Preferences>Content and press the File Types button. But, if it isn't giving you the option to set the default action, it probably isn't there. 

The only way I have found to add them is to go to ~/.mozilla/firefox/yourprofile/mimeTypes.rdf and add them manually.

---

### Post by pyros on 2007-07-01
these pages might be of some help to you:

[http://kb.mozillazine.org/MimeTypes.rdf](http://kb.mozillazine.org/MimeTypes.rdf)
[http://kb.mozillazine.org/Actions_for_attachment_file_types](http://kb.mozillazine.org/Actions_for_attachment_file_types)

---

### Post by qprfact on 2007-07-02
Thanks! I had a look at MimeTypes.rdf, and I think I need to go back in more detail - didn't want to tinker and break things!

Unless anyone here already has set those defaults for mp3s and can tell me the syntax?!

---

### Post by pyros on 2007-07-02
> **qprfact said:**
> Thanks! I had a look at MimeTypes.rdf, and I think I need to go back in more detail - didn't want to tinker and break things!

Unless anyone here already has set those defaults for mp3s and can tell me the syntax?!

It always helps to make a copy. Give me a few and I'll see about posting that for you.

---

### Post by pyros on 2007-07-04
really sorry for the late reply, cable internet problems.

ok, forgetting everything I posted before: 
open firefox
go to the edit menu and click on preferences.
in the preferences windows, click on the content icon
towards the bottom of that panel, look for the "file types" heading, and click on manage
that should open the "download actions" window. 
typing mp3 into search should narrow the list down to mp3 and m3u files.
select "MPGA MP3 audio" and click on "change action"
click the round circle to the left of "save them on my computer" 
press ok to close out of the "change action" window
press "close" on the download actions and firefox preferences windows as well

once I did that, I had the option of checking the "do this automatically..." box
that should (hopefully) do it for you.

---

### Post by qprfact on 2007-07-04
Sounds much easier, and I made the change OK, but does an MP3 extension map to an MPGA one though?

---

### Post by pyros on 2007-07-04
> **qprfact said:**
> Sounds much easier, and I made the change OK, but does an MP3 extension map to an MPGA one though?

It should, because MPGA is just mpeg audio. I tested it on my box and it works.  If the server deos not have the proper mime settings it may not work.

---

### Post by qprfact on 2007-07-05
I'll try a few different sites and see if it works! (maybe I was unlucky with the one I tried)

---

### Post by pyros on 2007-07-06
> **qprfact said:**
> I'll try a few different sites and see if it works! (maybe I was unlucky with the one I tried)

I tested it with lugradio and it worked every time.

---

