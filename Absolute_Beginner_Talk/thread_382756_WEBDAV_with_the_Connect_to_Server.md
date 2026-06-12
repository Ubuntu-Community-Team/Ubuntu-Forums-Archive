---
title: "WEBDAV with the Connect to Server"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by beakerman30 on 2007-03-12
I have a WEBDAV folder that I want to connect to using the places and then connect to server I put in the folder name and then the username and give the folder an alias like offsite files for example. After I do that I see the mounted volume on my desktop and click to open it and it comes back with an error message..Can't display XXXXXXXX login attempt failed. It didn't prompt me for a password so of course it failed and most of the info I see says it should be part of the setup however I must be blind. Any suggestions ??

---

### Post by matlj on 2007-09-02
I am having the same problem. I am unable to connect to my University's Webdav. The little setup never seems to have a spot for the password.

If it changes anything i'm using the AMD64 build.

---

### Post by matlj on 2007-09-02
Oh and if anybody knows how to make it work pls send me a message.

---

### Post by cmonspike on 2007-12-20
Select Service Type -> Webdav (HTTP)
In the server box type ->  yourusername:yourpassword@yourserverip_or_hostname
In the folder box type -> thenameofthewebdavfolder

Leave all other boxes blank. Click on Connect.

A folder will will appear on the desktop with thenameofyourwebdavlocation@yourserverip_or_hostname

Double click and the contents of the remote folder will appear.

---

### Post by ccrs8 on 2008-02-07
I have set it up the way cmonspike recommends and also without the 'username:password@' in front of the servername.  When I did not put the username:pass in the server field, when I tried to open the share, a username/pass box came up.  However, no matter how I set it up (user:pass or not, HTTP or HTTPS type of WebDAV, etc) I always get the same thing:

Firefox doesn't know how to open this address, because the protocol (dav) isn't associated with any program.

or

Firefox doesn't know how to open this address, because the protocol (davs) isn't associated with any program.

depending on whether I use WebDAV(HTTP) or WebDAV(HTTPS).  Any idea how to get the share to open in the file browser instead of the web browers?

---

