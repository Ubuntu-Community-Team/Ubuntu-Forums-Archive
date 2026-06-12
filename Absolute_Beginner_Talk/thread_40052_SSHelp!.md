---
title: "SSHelp!"
date: 2005-06-07
forum: Absolute Beginner Talk
---

### Post by AndEat on 2005-06-07
I was thinking to myself that there should be a place for a noob to ask for directions..and here I am.

I am trying to get together the wherewithal to browse the web anonymously. 

I understand the concept: I need to find a proxy of some sort, encrpyt a connection, and voila, the nosy and petty can go mind their own business. Maybe there is more, but this seems simple enough.  

But - I haven't been able get all the info together I need. I think I can use SSH   but haven't been able to yet. The key business is a bit tricky but understandable in the long run. A don't even know where to start for a proxy.

I'm really just looking for basic cloaking. Enough to keep out the nosy that would require a serious time and hardware effort to deter only the most determined. I'm not looking to run banking transactions or espionage.

The time and effort have not been invested - yet.  I'd like to ask for help from those with more experience as well as connect with those who are in the same boat. 

Any and all help is appreciated

Thanks    :?

---

### Post by Gtaylor on 2005-06-07
Well to begin with, what are you wanting to SSH to? You can open up terminal SSH session with another box by doing something like:
> 
ssh [email]user@somewhere.com[/email]

You'll be prompted for a password and you'll be greeted with a shell prompt much like your own.

File transfer may be done via SCP/SSH, I recommend using gFTP
> 
sudo apt-get install gftp

It's under the Internet sub-menu, select SSH2 from the drop-down protocol.

Keep in mind that all of this requires that you have an SSH server on the other side ready to accept your connection. If you want to allow SSH connections to your machine (from the outside):

> 
sudo apt-get install openssh-server


Hope that helps.

---

### Post by AndEat on 2005-06-12
[QUOTE=Gtaylor]
Hope that helps.[/QUOTE]

Definitely, any clue helps.


A. :)

---

