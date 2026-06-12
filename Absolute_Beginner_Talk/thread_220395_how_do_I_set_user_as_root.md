---
title: "how do I set user as root?"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by anubis2814 on 2006-07-21
How do I set user as root, and please be very specific please, I'm very new.  I'm sure its simple.

---

### Post by skale on 2006-07-21
go to the terminal, type in **sudo su**, press enter, andgive your password when it asks for it. Little stars won't show up for the letters, but type it in anyway and press enter.

But, the better way is to type in **sudo** before the command as a normal user, so that you are not encouraged to do all tasks as root. 

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by stricevics on 2006-07-21
Someone already answered this one I believe, but here it is again.

Open terminal and type: ```
sudo command
```

where [FONT="Courier New"]command[/FONT] is the executable that you wish to run as root.

---

