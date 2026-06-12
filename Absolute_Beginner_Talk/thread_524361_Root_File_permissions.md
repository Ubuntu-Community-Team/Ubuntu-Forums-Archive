---
title: "Root File permissions"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by ZootNerper on 2007-08-13
Hi Folks,

Being a beginner I can do stupid things like adjust the file permissions in my root directory. Could anybody tell me the defaults so I can set them back?

I mean "sudo chmod xxxx" What should the number be? (I think)

Not so clever.

-- Zoot

---

### Post by proalan on 2007-08-13
I don't think its wise to alter the root directory permissions if you don't really need to because of security reasons but heres the gist of using permissions...

3 numbers denote user, group, others respectively in that order

read, write, execute permissions = 7
read, write permission = 6
read, execute permissions = 5
read, permission = 4
write, execute permission = 3
write permission = 2
execute permission = 1

so for example

sudo chmod 755 -R /var/www

would grant read,write,execute permissions for the user, read execute for group and read execute for others for the directory and containing folders of /var/www

note the user in this case is 'root'

Heres a decent guide to permissions [http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html) 
It is worth taking the time to understand the permissions, it is fundamental to how linux operates.

---

### Post by ZootNerper on 2007-08-13
Thanks Proalan,

Everything seems back to normal (the boot sequence didn't stop t complain about some .file thing).

It was pretty stupid, but I didn't realise I was adjusting root and may not faired any better if I had realised. It's 20 years since I had a rudimentary experience with Unix.

Thanks for the help.

-- Zoot

---

