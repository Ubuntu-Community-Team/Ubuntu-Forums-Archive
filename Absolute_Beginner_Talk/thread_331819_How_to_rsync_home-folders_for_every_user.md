---
title: "How to rsync home-folders for every user?"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by gercokees on 2007-01-05
Hi,
At sartup, using a /etc/init/rc2.d/S99syncen link to a script, a script containing the following code is run:
```

rsync -arvuz                                                       \
    --exclude-from="$EXCLUDES"                         \
        -e "ssh -i /home/gercokees/.ssh/id_dsa"      \
                            /home/                                 \
        gercokees@gercokees:/home/ ;

```

Now, all works perfecly well, but: only my own documents (in /home/gercokees/ folder) are being synced. The script has no rootacces on the remote machine. How can i set everything up so that the script has write-acces in other users folders on the remote machine?

Thanks in advance...

---

### Post by gercokees on 2007-01-06
Hi,
I found out already... It had something to do with the root-password. Copied the contents of /home/user/.ssh/ to /root/.ssh/ and all works fine.

---

