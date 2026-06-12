---
title: "I did chown /var to some user :("
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by ThaNerd on 2007-05-17
I know, this is my mistake...

I had a directory in /var -- namely /var/www -- which i wanted to chown to www-data (Apache user) so that it would be allowed to access everything.
Unfortunately, when i had the idea, i was in /var/www/foo/bar/baz/very/far/dir and i ran a few "cd .." before i issued chown -r www-data:www-data *
Result : i was in /var instead of being in /var/www and the chown was applied in all subdirs of /var.

First, even ssh daemon wouldn't work anymore. Theni could re-chown most subdirs to root:root thanks to webmin and ssh works again. But for example, my mysql daemon refuses to start, and i can't find an error log telling me what's wrong with it...

Would there be a list of what user should be owning each directory/file?

---

### Post by compwiz18 on 2007-05-17
I would suggest you completely remove packages that got screwed up, then reinstall them (warning: this **will** remove config files).

If you don't want to do that, I've attached an ls -ahlR of my /var so you can compare, if you need any more specifics just ask :)

edit: sry, I don't know of any guide that would outline permissions for you.

---

### Post by rich.bradshaw on 2007-05-17
You can avoid this by always specifing the full path when you are doing things - you shouldn't just type chown -r blahblah, type the path as well. Good tip for others who are new!

---

