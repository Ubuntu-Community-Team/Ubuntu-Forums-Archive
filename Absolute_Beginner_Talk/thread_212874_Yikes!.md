---
title: "Yikes!"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by urbaneezer on 2006-07-10
I received my Dapper disc last week and upgraded.  But now I have no sound.  Not only that, but I keep mp3's stored on an external drive and Rythymbox will not play them...I get an error that says 'The file is not an audio stream...'

I went out to the repository and downloaded everything for gstreamer0.10.  Still...nothing.  

I don't even have system sounds (except for the startup sound at startup).  

Oh, and Sound Juicer won't play cd's either.  I'm getting "Error playing cd"..."Reason:  could not get/set settings from/on resource".  As well, another box pops up that says "Error playing cd"..."Reason:  internal data flow error".  

Also, I installed the flashplayer plug-in from the repository (or at least I thought I did) and still when I visit flash sites via Firefox...I'm still getting the 'need plugin' bs.  

I know there is some tweaking that needs to be done...I'm just not sure what I am/have done wrong or what I might still need to do. 

Can anyone help?  [-o<

---

### Post by urbaneezer on 2006-07-10
*bump*  #-o

---

### Post by T700 on 2006-07-10
You might give the Automatix script in my sig a go.  I ran into some of the same problems when I upgraded to Dapper and that was a quick and simple fix.

Paul

---

### Post by Brunellus on 2006-07-10
this stumped me for a while.   Mp3 support for gstreamer changed between Breezy and Dapper.  Details are on the RestrictedFormats wikipage:

[http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats)

---

### Post by Sonofmoog on 2006-07-10
Go here:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by urbaneezer on 2006-07-10
Alright...so I followed the instructions at the 'Restricted Formats' link and it did correct my system sounds...they are working normally now.

But I still get the message for Sound Juicer:

Error playing CD.
Reason:  could not get/set settings from/on resource

Error playing CD.
Reason:  internal data flow error

I am also still getting the 'internal data flow error' message with Rhythymbox when I try to play MP3's.

Baby steps!  :)

---

### Post by urbaneezer on 2006-07-10
*bump*  :neutral:

---

