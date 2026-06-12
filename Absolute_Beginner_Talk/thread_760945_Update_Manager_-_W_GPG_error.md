---
title: "Update Manager - W: GPG error"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by rangy on 2008-04-20
Runinning Ubuntu 7.10. Loadded, installed and updated from DVD.

Have been runnning with no problems.

While trying to use Update manager, I have been successfully updating most software, but keep getting this message:

[SIZE="3"]An error occured

The following details are provided:

W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991[/SIZE]

Since the message is related to the data within 'Update Manager' and its functions, it has nothing to do with what I might have for a GPG access error. It is internal to Update Manager. 

Any Ideas?

(Note: am not complete tyro in computers, have been slightly geeky for several Decades. Just finally learning Ubuntu and Linux. :confused:Am using this forum at 'your' suggestion.)

---

### Post by LowSky on 2008-04-20
It looks like one of the repos you installed is not working
are you trying install google earth or picassa?
 try installing  [medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by joshrobinson on 2008-04-20
all you need to do is import the key

[http://www.google.com/linuxrepositories/ubuntu704.html]("http://www.google.com/linuxrepositories/ubuntu704.html")

links for an old version of ubuntu, but the process is the same

---

### Post by rangy on 2008-04-20
The solution worked, although, it took a little con-figuring out.

The PGP key is now installed, and yes, the application seemed to be Google Earth.

Thank you for your time and trouble.

(PS: Had me shook when the message disappeared entirely, and I sent a note to the big 'Coffee Grinder' to see if I had innocently configured a no-no message)

rangy

---

