---
title: "How do I alter a file inside /etc directory?"
date: 2010-09-17
forum: Apple Hardware Users
---

### Post by rumplestilts on 2010-09-17
I've copied a ".conf" file from /etc to my Desktop and edited it using gedit. I then used the "rm" command to delete the old file from that etc/ directory. Now I want to put my altered file into /etc.

I probably just don't know the syntax. I've been using this:

sudo cp 'path/to/my/source/file.conf' '/etc'

but I get some sort of permission error. The source file is named "macfancntld.conf" and that's the name it needs to be once it's copied into /etc.

Any advice would be appreciated.

Thanks!

---

### Post by flick on 2010-09-17
Could you paste in the permission error message you're getting here? The specifics could help troubleshooting.

---

### Post by rumplestilts on 2010-09-18
Sorry; I discovered my error. I wasn't typing things properly. What I did to fix things was:

sudo cp (and I dragged the file in here so the path was correct) {space} (and I dragged the destination file in here so I'd copy over it) {return}

I put in my password when prompted and it worked.

Thanks for your concern. :D

---

