---
title: "I did a silly thing..."
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by Chipmunk on 2006-01-05
I changed the /etc/hosts file to add a new host on the LAN, and overwrote the default entry for the system.

sudo now returns sudo: unable to lookup (my computer) via gethostbyname()

I know I have to boot to single user mode in order to edit it back, how do I do this? I tried recovery mode, it keeps asking for the (nonexistent) root password.

---

### Post by Juergen on 2006-01-05
> I tried recovery mode, it keeps asking for the (nonexistent) root password.
I don't know why it would do this.

Do you have any Linux Live-CD?
Then you could start this, mount your root-partition somewhere and edit hosts there.

---

### Post by Chipmunk on 2006-01-05
That's what I was afraid of... :)  Off to get the DSL cd out of the box...

---

### Post by Chipmunk on 2006-01-05
Done, and done. That was 'unpleasant' to say the least but the live cd worked great:)

---

### Post by equal on 2006-01-05
I think every Linux user should be issued a DSL disc. That thing has saved my ass several times!

---

### Post by Chipmunk on 2006-01-05
Indeed, it's what originally convinced me LINS (Linux Is Not Scary).
I hand copies to anyone who's interested and tell them "If you decide you like Linux, I'll hand you an Ubuntu cd too" :)

The thing is, with Linux, even major foulups like I just did, generally have a fix available, even if it's complex. With certain other systems, the 'fix' is likely to be 'reinstall'.

---

