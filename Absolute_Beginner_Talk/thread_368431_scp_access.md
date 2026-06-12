---
title: "scp access"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by frenchtomytoast on 2007-02-23
I'm attempting to use scp to copy files from a remote machine onto my server.
I want to copy into a different directory than /home/usernamehere
I would like to have it something like /otherdirectory
but everytime I try this I get an access denied error.
And /otherdirectory needs to allow www-data to access it.

The goal is to be able to backup all my files onto the server and then later be able to access them via a website (in read only form).

---

### Post by Strider on 2007-02-23
The directory you're trying to copy with needs to have the writeable permission for www-data so you will have to create that user on the server if you haven't already.  Then grant write permission to www-data to the /otherdirectory.  Should work.  As long you're scp'ing with www-data.

-Mike

---

### Post by frenchtomytoast on 2007-02-23
Excellent. Thank you so much! :)

---

