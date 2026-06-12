---
title: "php5 apache2 Internal Server Error premature end of  scripts header"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by egoldtech on 2007-12-11
I reinstalled PHP today but now all my .php scripts are broken. I receive an internal server error (500). The logs only give the additional information: "premature end of script headers."

I did a lot of searching around, and most recommendations were to check the permissions of my files. I used chmod to change some of my php files to 777 to test them, but it still didn't work.

The solution turned out to be that I had to chown all my files from root:root to user:userfor each website on my box. This is causing serious hassle, as I uploaded every one of my files using root (they're all owned by root)

---

### Post by nikoPSK on 2007-12-11
did you save all your scripts in a place owned by root?

---

