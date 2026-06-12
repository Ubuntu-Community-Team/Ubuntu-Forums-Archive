---
title: "ACL's (access control lists)"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by grim918 on 2006-08-16
I was wondering if ACL's are supported in Ubuntu. I ran the command:
> man setfacl

I get a No manual entry for setfacl message. Is there a way to install ACL's in Ubuntu or are they not really all that important and should just forget about them. I am currently learning how to set up a multi-user system, which deals with file permissions and the creation of groups. While reading I ran into this ACL subject, is there a way to get it to work on Ubuntu. Thank you for any help.

---

### Post by Cone on 2006-08-16
Try ....
```
sudo aptitude install acl
```
if "ACL" is what you're looking for.

Not sure if that's right, and I have no experience with it, but I did a dry run with the -s modifier on aptitude and it appears an "acl" package exists...I would say give that a shot.

Hope this helps,
~Cone

---

### Post by grim918 on 2006-08-17
Yes this is what I was looking for. Thank you.

---

