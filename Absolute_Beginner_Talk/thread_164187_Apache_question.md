---
title: "Apache question"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by seshomaru samma on 2006-04-22
Hi
Installed Apache2 and want to change the index.html file . But where is it?
Where is the server's root?
And how do I search for a file on Ubuntu? in Nautilus and the terminal.
Thanks

---

### Post by ruzle0 on 2006-04-22
have a look at /var/www/
you can set it so each user has a directory in thier home directory seen by apache but if you are just experimenting on your own its fine to use here
to find file with the terminal use find eg find /tmp -name filename 
see 'man find' as it has many options

---

### Post by seshomaru samma on 2006-04-23
Found it , thanks

---

