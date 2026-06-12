---
title: "creating a real root"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by bnj on 2006-02-16
Hello,

I wonder about ununtu's strange way of having no root user.
I read somewhere on a forum saying that, if one wants to have a real root user that can log in and such kind of things, than he has to type something like 
```
su passwd root
```
I did this and now I can ssh to my computer as root. 

But whenever i want to use a system application (Like, for example, creating new users or  add applications), I have to give my user password, instead of the root's password. Why that? I would like only the root to be able to make such operations. How can I change that?

Thank you,

Benjamin

---

### Post by LordBug on 2006-02-16
#1 - Enabling the root account is unnecessary, and (IMO) a bad idea.  There are many threads and Wiki entries on WHY the root account is not enabled.  I would suggest reading them to understand better.

#2 - Enabling root login via SSH is a HORRIBLY bad idea.  This creates a huge security hole in your system.

#3 - This is because Ubuntu uses SUDO, and that uses it's own information.  It will always be the user's password, and not root's.  Sudo is the recommended and preferred way to do any root-level activity.

I would suggest nuking root login via SSH, and using Sudo for all root-level activity.  You'll have a more secure system this way.

---

### Post by bnj on 2006-02-16
OK. I see.
So I will change my mind and try to respect Ubuntu's philosophy. But now, one question remains:

*I have created the root user. How can I delete it?*

Besides that, i wonder why enabling root login via SSH is such a bad idea. Suppose I have a computer that is accessible via SSH (which most linux computers are). Suppose that this computer has a root account (which most linux computers have, i believe), how can I enable users to SSH to their account and not to the root account? Is this possible at all?

Finally, just in case anybody would read this thread, I would like to point out that > There are many threads and Wiki entries on WHY the root account is not enabled. refers to, among others, [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Best regards,

Benjamin

---

### Post by aragorn2909 on 2006-02-16
[QUOTE=bnj]*I have created the root user. How can I delete it?*[/QUOTE]

```
sudo passwd -l root
``` to disable root acccount
That being said, however, IMHO there is a place for a root account, as I've discussed in other threads.  Its just another tool that we don't necessarily need to deny ourselves.  The creation of a root account doesn't make one's system insecure in and of itself.

A

---

### Post by Iowan on 2006-02-16
[QUOTE=bnj]
Besides that, i wonder why enabling root login via SSH is such a bad idea. [/QUOTE]
Because, as you said, most Linux boxes have a **root** user, and most SSH programs use port 22, the job of breaking in is considerably simplified.  It IS possible to change **root**'s name (in a sense), and it IS possible to use different ports.

---

