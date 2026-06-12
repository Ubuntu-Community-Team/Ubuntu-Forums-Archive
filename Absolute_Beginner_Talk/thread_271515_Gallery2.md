---
title: "Gallery2"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by samuelkarush on 2006-10-04
I am almost embarassed to ask this:

I have installed gallery and gallery2 using synaptic, the database  named gallery2 was made, and a directory called 'albums' has appeared in my web directory.

Where exactly do i go from here? What needs to go into my web directory to allow photo uploads?

I'm using apache2 and php4.4.2
thanks!
sam


updated 10/8

with both gallery and gallery2, everything necessary was found using properties/installed files in synaptic. I had to move the folder /usr/share/gallery2 to my web directory, and work from there.

I'm wondering why synaptic doesnt install this in the web directory by default?

---

### Post by SeanTater on 2006-10-31
actually, I think it is intended to use an alias for that..

First, see if it works just by restarting it:
```
/etc/init.d/apache2 force-reload[/conf]

If it does not, try this:
(warning: YMMV)

Add [code]Include /etc/gallery2/apache.conf
``` to /etc/apache2/apache2.conf, then uncomment the alias line (the first line) in /etc/gallery2/apache.conf.. and restart apache2 just like you did above.

Apache started saying that that alias won't do anything because the alias is supposedly already in apache2.conf, but for me, it suddenly worked.

---

### Post by bsussman on 2006-10-31
I understand your embarrasment.

After all this is an ubuntu forum.

You might want to go to [http://gallery.menalto.com/forum](http://gallery.menalto.com/forum) for help.  They are a good supportive community.

---

