---
title: "PHPMyAdmin broken"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by Siggy75 on 2007-12-27
PHPMyAdmin was 'responding' yesterday: now I get a "save as..." dialog from the browser for the file "index.php". I did some reading and found the message means the php interpreter is not interpreting! I used the package manager to re-install phpmyadmin but still no luck. Well, I have been pulling in pipe-delimited text files off of Windows machines inside our network, and moving and copying them to www/cgi-bin directories where a tech support database looks for them to import. I did use a "sudo nautilus" command to run nautilus as root and move those text files around. What else could be the culprit? Still a newbee...thanks for suggestions.:)

---

### Post by georider on 2007-12-28
Do other .php files work?

You might check permissions on the files and directory. I had this issue with one of my servers the other day and it turned out to be the permissions were changed on the directory and files.

---

### Post by Siggy75 on 2007-12-28
> **georider said:**
> Do other .php files work?

You might check permissions on the files and directory. I had this issue with one of my servers the other day and it turned out to be the permissions were changed on the directory and files.
Thank you! That is probably what happened with me futzing around with it. I will go check that and let you know. - Anthony

---

### Post by Siggy75 on 2007-12-28
That was apparently, it. I cannot remember, however, what the permissions on "groups" and "others" were, before I started fiddling with the permissions (because there's no 'cancel' button on the dialog so I can see what the permissions started out to be). Silly me. I assumed there would be a cancel button on the dialog! Well, it's working now from other computers on the network. Thank you : >]

---

### Post by georider on 2007-12-28
Good to hear you're working again.

You're very welcome.

Have a better day!! :)

---

