---
title: "Noob question: cant figure out what this is..."
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by walmartboi on 2008-03-18
trying to configure samba.
i ran the test on .conf and it said it was running fine.
---------------------------------------------------------------------------------
typed command: smbclient -L "hostname"

got:

session setup failed: NT_STATUS_LOGON_FAILURE

"i supose i got the session setup failure because my pc isnt setup
although im not sure at this point"
---------------------------------------------------------------------------------
next:

typed command: nmblookup -B "myhostname" __SAMBA__

got:

querying __SAMBA__ on "myhostname"
"myhostname" __SAMBA__<00>

"not sure what that means"
---------------------------------------------------------------------------------
next:

typed command: nmblookup -B "myhostname" `*'

i was then prompted with this:

>

what is this prompt and how do i get out of it? thanks.

not sure what this means but here is a copy of how the last 3 lines on my screen reads:

"me@mybox":~/www$ nmblookup -B "myhostname" `*'
>
>

i dont think ~/www$ was there when i hit enter but im not sure i may have inadvertently hit something as i hit enter... i just need to know what this prompt is and how to get out of it.

---

### Post by njparton on 2008-03-18
Can you start by telling us what your trying to accomplish with samba?

---

### Post by walmartboi on 2008-03-18
well i figured out what the prompt was, apparently i did something and went into interactive mode.

as to what i need to accomplish with samba, is a system to transfer files from my xp machine to my my ubuntu server. samba is running fine according to the tests i ran so from what i can tell some is wrong with my configuration and or something wrong with my xp machine.

---

### Post by Neo0351 on 2008-03-18
I've always used this thread for samba.  It works and is simple.
[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba)

---

### Post by njparton on 2008-03-19
Post your smb.conf file here

---

