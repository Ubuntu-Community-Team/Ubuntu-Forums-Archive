---
title: "Make new user and it's setting."
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by kpham.p on 2006-09-27
Hi guys,

I've installed ubuntu and setup compiz as well as other apps for the main user.  I would like to create a new user which would have the setting as well as the apps just like the main user (with the exception of sudo capability).  How would I do that?

Because, when I create the 2nd user, I end up with the default Ubuntu setting.  

Thank all in advance.
kpham

---

### Post by henriquemaia on 2006-09-27
Well, you can create a 2nd user, then delete his /home/2nd_user partition, copy your /home/1st_user to a folder called /home/2nd_user and then change the permissions of that folder /home/2nd_user to mathc its new owner, the 2nd_user.

Sounds confusing? You can do like this. Create the 2nd_user. Then, on a terminal, do:

```
sudo rm -r /home/2nd_user
```

Then do:

```
sudo cp -r /home/1st_user /home/2nd_user
```

Then do:

```
sudo chown -R 2nd_user:2nd_user_group /home/2nd_user
```


After that you should have an exact copy of your 1st user configurations.

But remember to backup things first.

---

### Post by kpham.p on 2006-09-27
AWESOME!!!!!!!  very clear... thank you thank you.

kpham.

---

