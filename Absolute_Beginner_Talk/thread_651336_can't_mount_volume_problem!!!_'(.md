---
title: "can't mount volume problem!!! :'("
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by Heathz on 2007-12-27
I'm new in linux. I'm use Xubuntu version 7.10 and I install it completely yesterday
and now I have problem when I first enter to C: or D: I must type my password so I go to System -> user and group and It show me

User
Root

I go to User and check off the second button I'm not sure but it about "access  ??" and then I restart my laptop

when enter to xubuntu again and I type my user and password I can't mount C: and D: It show me "unable mount" error

and when I go to System -> user and group to set it like before error it ask me password and then I type my password I show me "failed to run users-admin as user root"

please help me!!! :'(

---

### Post by jas0 on 2007-12-27
Could you try to describe exactly you want to accomplish and the steps that you take to do it? I'm really not sure what the situation is.

---

### Post by taurus on 2007-12-27
You want to mount your windows partitions?  Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
mount
```

---

### Post by rickycodie on 2007-12-27
yes the description was a little confusing, linux has no designators like C: or D: as it is not windows. all of your personal files should be in the home folder. open places and thne click on home. all your stuff should be in there, provided that it's not still on windows.

---

