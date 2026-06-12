---
title: "photo sharing software?"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by viniosity on 2006-08-19
My wife and I want a nice secure place to put our pictures.  We both use separate computers but share an ubuntu server.  Is there any software we can load on our dapper server that allows us to upload, organize, and view those pictures?  We're not interested in sharing them with other people as much as having a private site that would act as a photo album.  Any suggestions?

---

### Post by GeekSpeek'r on 2006-08-19
we use " gallery2 " which is a simple, secure web-based gallery app.

you can get it via

 apt-get install gallery2

the website is [http://gallery.menalto.com/](http://gallery.menalto.com/)

---

### Post by Marsolin on 2006-08-19
You can also try Album Shaper ([http://linuxappfinder.com/package/albumshaper](http://linuxappfinder.com/package/albumshaper)).

If you don't want a web like interface, but would rather use a conventional photo manager, you could always create a shared folder on the server that both you and your wife have access to and point a program like F-Spot, Picasa, or Digikam to it.

---

### Post by viniosity on 2006-08-21
Cool, thanks for the replies.  I ended up installing gallery2 and it seems to be even more flexible than I expected.  Thanks again!

---

### Post by TVu on 2006-08-21
> **Marsolin said:**
> 
...and point a program like F-Spot, Picasa, or Digikam to it.

I jump in this thread if I may.

F-Spot imports pictures from defined location. Import-process either copies photos to user's home directory or reads them directly from the location.
In my case copying is not required since the location would be a shared directory in /home-partition, and users of this computer are allowed to access it. However, when there are new photos added to location, F-Spot won't show them without reimporting. 

Is there a way to automate this ie. allowing all users to see new photos with F-Spot without any action?

---

