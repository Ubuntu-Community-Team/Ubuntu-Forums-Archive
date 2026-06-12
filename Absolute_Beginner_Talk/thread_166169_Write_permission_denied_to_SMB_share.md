---
title: "Write permission denied to SMB share"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by gantww on 2006-04-25
Hello all,
I've created a few folders and shared them using SMB. I can browse to them in Windows, but the system won't let me write to them (permission denied). Initially, I thought the problem was because the files were owned by root, but I used chown to change the owner to my user. However, I'm stuck as far as what to do next to make them usable from Windows.

Any hints?

---

### Post by echo $USER on 2006-04-25
Check [this]("http://ubuntuguide.org/#sharepublicfoldersreadwritesecurityuser") out.

---

### Post by gantww on 2006-04-25
Hmm. That fixed it.

Still a little slow copying data across. Any way to improve performance?

---

### Post by echo $USER on 2006-04-25
[QUOTE=gantww]Still a little slow copying data across. Any way to improve performance?[/QUOTE]

What kind of infastructure are you using?  Wireless or wired?  Router, switch, or hub?

---

### Post by gantww on 2006-04-25
It's a wired connection with a router - nobody else is using it at the moment. I'm thinking that it may just be because I am using SMB. According to the docs I read, I can switch to NFS once I'm totally on Linux - supposedly it's faster. I think it may also be because I'm moving a lot of very small files around.

---

### Post by echo $USER on 2006-04-25
Yeah, I think you are right; especially if you are writing to and from a ntfs filesystem.  I never thought about that until you brought it up.

---

