---
title: "Automatic logon = more proned to be hacked ???"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by Browser_ice on 2007-07-17
I am the only user of my Ubuntu 7.04 PC (Dual boot) and was wondering about seting up to automaticaly logon on (meaning not having to enter a logon-id + password) but was wondering if that would it make it more proned to be hacked.

---

### Post by jfinkels on 2007-07-17
> **Browser_ice said:**
> I am the only user of my Ubuntu 7.04 PC (Dual boot) and was wondering about seting up to automaticaly logon on (meaning not having to enter a logon-id + password) but was wondering if that would it make it more proned to be hacked.

Go for it, you're fine.

"Hacked" is one of those words put out there by the media which could mean any of a broad range of things. Most of the time, when we talk about security, we talk about things like vulnerabilities within programs that allow code to be remotely executed or allow increased access to an unwanted user or program. If someone could access your computer through your internet connection, the graphical login screen wouldn't matter, anyway :D

---

### Post by bodhi.zazen on 2007-07-17
IMO, no

You are giving (physical) access to your box without a log in, which is disturbing to  me, but bottom line, physical access = bad news no matter what you do (one can always boot a live CD) with the possibility of encryption of your drive / data.

---

### Post by Browser_ice on 2007-07-18
ok, so I got 2 replies : one says Yes and one says No.

Hard to take a decision based on this !

I need more answers (with explanations). This isn't only for me for the whole community also.

---

### Post by Hobo Joe on 2007-07-18
Most likely not, But I'm not sure how to do it.

One thing you do NOT want to do though, is log in as root. THAT will make you much more 'prone to be hacked'.

---

### Post by CautionaryX on 2007-07-18
The auto-login isn't really a problem over the Internet.  However if other people can come in contact physically with your computer then they can access whatever you can access (without sudo, as that still requires a password).

If you live alone then it really shouldn't be a problem.

Edit: As Hobo Joe said, whatever you do, do not configure root to autologin.

---

### Post by Nythain on 2007-07-18
if you are the only person who uses the pc you shouldnt have a problem... its basically there to keep multiple users out of other users stuff.

its not going to open a backdoor on the net as far as i know, and if someone is able to get that far into "hacking" you chances are they are going to be able to circumvent what little protection that screen would theoretically provide anyway.

---

### Post by Seisen on 2007-07-18
If it's a desktop and you are the only that has access to it than it will be fine. Its its a laptop than I would not do it.

---

### Post by aysiu on 2007-07-18
The only differences between an autologin and a manual login in Ubuntu are these:

**Manual login**:
If other users want to see your files, they have to have accounts themselves, boot into recovery mode and know how to use the command-line, or have a live CD and know how to mount partitions.

If other users want to delete your files, they have to boot into recovery mode and know how to use the command-line, or have a live CD and know how to mount partitions.

**Autologin**:
If other users want to view or delete your files, they just have to walk up to your computer.

---

### Post by bodhi.zazen on 2007-07-18
LOL

no = not more prone to be hacked :twisted:

1. The prefered term = cracker by the way. Hacker is an old term and refers to people with tweak or contribute to code in a effort to improve or customize functionality.

[http://www.catb.org/~esr/faqs/hacker-howto.html](http://www.catb.org/~esr/faqs/hacker-howto.html)

2. I advise you look into linux security. The main issues are :

[list][*]Enforce strong passwords[*]Limit root access[*]Physical access (as I said physical access = big security hole)[*]Do not install software from untrusted sources[*]If you run a server, it is your responsibility to learn how to secure it.[/list]

By default, there are no servers running so there is nothing to crack into. If, however, you enable NFS,Samba,ftp,http, etc this opens the door to crackers.

Anyone that can crack your system outside of those issues will not be deterred by that lack of automatic log in.

---

### Post by jfinkels on 2007-07-18
> **bodhi.zazen said:**
> LOL

no = not more prone to be hacked :twisted:

1. The prefered term = cracker by the way. Hacker is an old term and refers to people with tweak or contribute to code in a effort to improve or customize functionality.

[http://www.catb.org/~esr/faqs/hacker-howto.html](http://www.catb.org/~esr/faqs/hacker-howto.html)

2. I advise you look into linux security. The main issues are :

[list][*]Enforce strong passwords[*]Limit root access[*]Physical access (as I said physical access = big security hole)[*]Do not install software from untrusted sources[*]If you run a server, it is your responsibility to learn how to secure it.[/list]

By default, there are no servers running so there is nothing to crack into. If, however, you enable NFS,Samba,ftp,http, etc this opens the door to crackers.

Anyone that can crack your system outside of those issues will not be deterred by that lack of automatic log in.

I was going to say, "I think he meant, 'You are not more prone to being "hacked"'" but you got here first :D Good clarification, bodhi.zazen.

---

