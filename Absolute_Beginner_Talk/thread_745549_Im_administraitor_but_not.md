---
title: "Im administraitor but not?"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by oblivioncth on 2008-04-04
I installed this my self, I made the only account myself, and am the owner of the machine (not that ubuntu would know that). But for some reason, sometimes it will ask me for and administrative password or say I can't do something because I'm not and administrator.

I'd like to know how to fix this. :confused:

Thanks

---

### Post by wolfen69 on 2008-04-04
> I'd like to know how to fix this
there is nothing to fix. that is normal. it does that to protect your computer. that is the default way of doing things in linux. remember, this is not windows. (thank god)

---

### Post by SOULRiDER on 2008-04-04
Your user is NOT an administrator, actually, you cant use the administrator (root) account on Ubuntu. What you can do is use sudo and gksu (thats what appears when you open synaptic for example and asks for your pasword) to become an administrator temporarily.

Check this out:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by northern lights on 2008-04-04
Linux won't let you alter certain files, for instance, unless you put you're password. This is a security issue.

In Windows, for example, you may delete any system file without reconfirming it's you who wants to do it. Malicious software can too. Whether it's you or malware, you'll likely only notice the neccessity of the file after reboot, when you'll be greeted by a bluescreen...

---

### Post by oblivioncth on 2008-04-04
That is some great security! :biggrin:

---

### Post by Gen2ly on 2008-04-04
If you're asking if you can disable the root password it is possible but if you ever have bad people in your place be careful: :)

[http://www.linux.com/forums/topic/1332](http://www.linux.com/forums/topic/1332)

---

### Post by Tatty on 2008-04-04
[https://help.ubuntu.com/community/RootSudo?highlight=%28rootsudo%29]("https://help.ubuntu.com/community/RootSudo?highlight=%28rootsudo%29")

This is well worth a read if you are a new linux user.

---

### Post by erginemr on 2008-04-04
Following that, I'd suggest you to read this excellent article:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

to convince yourself to the necessity of using Linux in limited user mode. Whenever you need to have root access, you will always have sudo/gksudo by your side.

---

