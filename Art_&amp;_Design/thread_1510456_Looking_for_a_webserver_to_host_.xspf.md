---
title: "Looking for a webserver to host .xspf"
date: 2010-06-15
forum: Art &amp; Design
---

### Post by Emmtor on 2010-06-15
Hello there,

I would like to use a .xspf playlist I've written to play some music with a flash player, but I have had trouble finding a server to host the playlist. The servers I use do not support serving files with the MIME type "applications/xspf+xml", can anyone suggest one,or point me to a free server that i can configure so it will server with that specific MIME type?

I hope I included all the information that you might need. =)

---

### Post by kieransimkin on 2010-06-20
With apache you can set the outgoing content type using an .htaccess file and the AddType directive, something like:
AddType applications/xspf+xml .xspf

[See the mod_mome documentation for further details]("http://httpd.apache.org/docs/1.3/mod/mod_mime.html").

---

### Post by dhayfule on 2010-06-21
do this
go to [www.flexilinuxhost.com](www.flexilinuxhost.com)

Click Live chat and ask the customer care if u can do it. I am sure they will help you

---

### Post by Emmtor on 2010-06-27
Thanks for replying, but I'm afraid that my post is a bit misleading.
As far as I know, only server owners use apache, so you must have understood that i have my own server. I do not own any kind of server, and I am not willing to pay for one.
What i need is a free hosting service site, which i can configure to serve an .xspf playlist so it can be played by flash players.

---

### Post by Penguin Guy on 2010-06-27
> **Emmtor said:**
> only server owners use apache
**...**
What i need is a free hosting service site, which i can configure to serve an .xspf playlist so it can be played by flash players.
Free hosting servers usually let you modify the Apache configuration for your website - you usually do this using a [FONT="Courier New"].htaccess[/FONT] file in your website's root directory.

---

### Post by Emmtor on 2010-06-27
I understand. Forgive my ignorance, i am sorry about this. I will read about the .htaccess file.
Thanks for pointing me in the right direction. =)

---

