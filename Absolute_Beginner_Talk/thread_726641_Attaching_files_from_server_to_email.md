---
title: "Attaching files from server to email"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by tqprvn on 2008-03-16
hi there

How do we attach files from a server direct to emails.  Server address is some smb thing - which I suspect is part of the problem...but I also totally dont know what I am talking about :)

Copy-and-pasting on to the desktop seems like a long and painful way to do this, but the tech guy here seems pretty insistent that there is no other way.

Anyone?

- M

---

### Post by gam3r4eva on 2008-03-16
Are you using an email client or web-based email?  If a client, which client?  If webmail, what service?

What exactly have you tried that didn't work?

With a little more information we should be able to figure this out.

---

### Post by Oldsoldier2003 on 2008-03-16
> **tqprvn said:**
> hi there

How do we attach files from a server direct to emails.  Server address is some smb thing - which I suspect is part of the problem...but I also totally dont know what I am talking about :)

Copy-and-pasting on to the desktop seems like a long and painful way to do this, but the tech guy here seems pretty insistent that there is no other way.

Anyone?

- M

files stored on a network share have to be saved to your local file system before they can be attached to an email

---

### Post by tqprvn on 2008-03-16
> **gam3r4eva said:**
> Are you using an email client or web-based email?  If a client, which client?  If webmail, what service?

What exactly have you tried that didn't work?

With a little more information we should be able to figure this out.

using Thunderbird.  Tried dragging and dropping, tried using the little paperclip attach thing....

> **Oldsoldier2003 said:**
> files stored on a network share have to be saved to your local file system before they can be attached to an email

hmm - is there any way around this?

Running a company, and this is pretty-damn-inefficient for us, plus it inadvertently encourages staff to store files locally which means that we will have a godawful mess on our hands in due course.

---

### Post by bsharp on 2008-03-16
Maybe if the network store was mounted locally, it might be allowed, but I have never done this and have no idea how, but it might give you something to look for.

---

### Post by Oldsoldier2003 on 2008-03-16
> **bsharp said:**
> Maybe if the network store was mounted locally, it might be allowed, but I have never done this and have no idea how, but it might give you something to look for.

actually bsharp has the answer. if you actually mount the smb share your email client will think its part of the local file system and you can send the attachments. Tested in evolution.

---

### Post by Oldsoldier2003 on 2008-03-16
> **tqprvn said:**
> using Thunderbird.  Tried dragging and dropping, tried using the little paperclip attach thing....



hmm - is there any way around this?

Running a company, and this is pretty-damn-inefficient for us, plus it inadvertently encourages staff to store files locally which means that we will have a godawful mess on our hands in due course.

Mounting the samba shares is the the key to this issue. They wont just be able to browse and drag drop.

---

### Post by tqprvn on 2008-03-16
ok, so how do we do mount the share?  I am stupid with these matters and am starting to get the impression that even with my ignorance I am 10% smarter than DeploymentBoy here.

also, what do you mean by 'wont be able to browse'?

---

### Post by Oldsoldier2003 on 2008-03-16
> **tqprvn said:**
> ok, so how do we do mount the share?  I am stupid with these matters and am starting to get the impression that even with my ignorance I am 10% smarter than DeploymentBoy here.

also, what do you mean by 'wont be able to browse'?

okay basically heres the deal with trying to send files from a samba share. disclaimer: 7.10 Ubuntu Gutsy using evolution. other configs may work differently.

1. right clicking and send to just doesn't work in nautilus since the samba share isn't part of the local file system

2. dragging and dropping into most email clients From a samba share doesn't work either because the client seems to lose the network path.

3. the only way I've so far managed to get a file to be attached to an email is to attach the file using the file attachment dialog. (Having the share mounted makes this possible and within the realm of average user ability)

4. you don't have to actually mount the share via fstab, this means your deployment boy doesn't have to mess things up- if you can already connect and you save it as a place in nautilus it will work. so far using the smb path to attach an email has been broken, but using the attach dialog works well.

---

