---
title: "Sort of a nested NFS issue?"
date: 2010-10-25
forum: Apple Hardware Users
---

### Post by repsol05 on 2010-10-25
Ok I have a Red Hat server exporting  a share that is mounted on an ext3 externally mounted mount. Looks like this:
export /remote/server

/dev/sdc1 /remote/server/folder1 nfs defaults,intro 0 0

Now I mount from my mactel 5.1 running Ubuntu 10.10

mount server:/remote/server /mnt/share

Now there are other folders in /remote/server that are local to the server and I can see and get to everything fine, but since folder1 is mounted on /dev/sdc It looks empty from my mactel running Ubuntu 10/10.

Here is the thing. My Ubuntu running 10/4 sees the share fine. in fact all of my other boxes whether it be my Android, My Mac, or older linux, can see it fine. It is an Issue I believe with either the mactel or the latest version of Ubuntu.

This is kind of hard to explain in the forum, but I am hoping someone understands and can give me something to try, or maybe I can explain a little better.

Summary I mount a partition on an external drive as an ext3 share. I then export a folder that has this mount downstream. Then when I mount the folder via nfs the share is empty, but only on my mactel running Ubuntu10.10.

Thanks in advance

---

