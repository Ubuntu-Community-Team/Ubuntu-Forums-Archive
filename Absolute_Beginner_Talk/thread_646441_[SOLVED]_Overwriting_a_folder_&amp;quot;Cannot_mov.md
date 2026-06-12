---
title: "[SOLVED] Overwriting a folder: &amp;quot;Cannot move (dir) to a subdirectory of itself&amp;quot;"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by supergrover1981 on 2007-12-21
Hi Gang,

Filthy Ubuntu newbie here - any help greatly appreciated.

I'm trying to overwrite a folder (and included files) on my local apache server. I need to do this in order to upgrade a Drupal install. I first tried doing this through Nautilus, but couldn't do so (I assume due to a permissions problem, which is fair enough).

Confident I could get around the problem, I tried opening terminal and running: 

> sudo mv testsite /var/www/

This presented the message: > cannot move 'testsite' to a subdirectory of itself, '/var/www/testsite'

So, my question is, how can I overwrite this folder without loosening all the permissions on that folder & it's underlings?

Any help greatly appreciated,
                                        - JB

---

### Post by chippy99 on 2007-12-21
There must already be a folder called testsite in the /var/www directory. If you dont want that directory you can remove it with sudo rm -r /var/www/testsite
Better still move it to somewhere else just in case :)
Once the offending directory is gone your mv command will work. If you prefer you can overwrite the contents of /var/www/testsite by doing cp-arv testsite/* /var/www/testsite/

Be careful, if its important data and your not sure what you are doing make a temporary backup of your files in a subirectory somewhere using cp -a which preserves file ownerships and permissions.

---

### Post by supergrover1981 on 2007-12-21
*grin*

Many thanks Chippy. The cp-arv is what I was looking for. Cheers. :-)

---

