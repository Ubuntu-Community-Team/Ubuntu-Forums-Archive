---
title: "Trouble Writing to Folders other than Desktop"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by 42Wired on 2007-02-19
There are some files I have downloaded onto my Desktop that I would like to move to their corresponding program folders. Every time I try to move a file into another directory, an error message comes up that says, "[I]Error while copying to "[directory]"
You do not have permissions to write to this folder.[/I]"

Would adding a file to a directory make that much of a difference, or do I just need to put my password in somewhere?

---

### Post by EvilMarshmallow on 2007-02-19
The easiest way is to do this from the command line.  You'll have to use sudo to do it:

sudo cp /home/___/Desktop/file /path/program/file

Write access to basically everywhere on the system (except for your home directory) is restricted.

---

### Post by bodhi.zazen on 2007-02-19
LOL

Permissions : [http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[http://psychocats.net/ubuntu/security](http://psychocats.net/ubuntu/security)

---

### Post by MrKlean on 2007-02-19
I would replace cp with mv.... I think cp is for copy...mv is for move ; )

---

### Post by 42Wired on 2007-02-19
Worked perfectly. Thanks.

---

### Post by EvilMarshmallow on 2007-02-19
Good point, I stand corrected.

mv instead of cp.

---

