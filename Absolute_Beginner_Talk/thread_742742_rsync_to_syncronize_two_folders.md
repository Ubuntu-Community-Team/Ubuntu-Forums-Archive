---
title: "rsync to syncronize two folders"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by peterlauri on 2008-04-02
Hi,

I have a remote server MASTER that stores documents in /docs, this will be the main repository.

I then have two machines LAPTOP1 and LAPTOP2 that have /docs folder.

How can I with ONE command on LAPTOPN make sure that MASTER:/docs and LAPTOPN:/docs are synced, meaning that any new file on MASTER:/docs that is not at LAPTOPN:/docs will be copied, and any new file on LAPTOPN:/docs that is not in MASTER:/docs will be copied to MASTER:/docs.

Right now I do it in two steps, but that doesn't feel right, as rsync should be able to sync between folders, not just copy from one place to another. This i my current two steps:

rsync -avz MASTER:/docs/ LAPTOPN:/docs/
rsync -avz LAPTOPN:/docs/ MASTER:/docs/

I feel a bit lost, but I might just be stupid :)

/Peter

---

### Post by .nedberg on 2008-04-02
I use Unison for that. Have a look at it!

---

### Post by mozetti on 2008-04-02
> **peterlauri said:**
> Right now I do it in two steps, but that doesn't feel right, as rsync should be able to sync between folders, not just copy from one place to another. This i my current two steps:

rsync -avz MASTER:/docs/ LAPTOPN:/docs/
rsync -avz LAPTOPN:/docs/ MASTER:/docs/

Actually, it is right. Rsync does one-way syncing so your method is the only way to accomplish it using rsync. As the other reply mentioned, Unison will give you what you're looking for. In fact, Unison is even mentioned as a 2-way sync solution on the rsync homepage.

---

