---
title: "[SOLVED] Makin cdrom0 unaccessible"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by brunoskrebs on 2007-08-27
Hi,

I`m learning Linux reading the book "Beginning Ubuntu Linux - From Novice to Professional". And I learned already about the permissions (at least the basic) and how to change it. And I also learn that Linux treats everything like a file or a directory (or almost everything).

So I tried to set my cdrom accessible only by the root to do some exercises and learn more. But I got frustrated because it didnt work :(

The steps that I tried:

```

root@bruno-laptop:/media# chmod a-x cdrom0
chmod: changing permissions of `cdrom0': Read-only file system

```

I also tried to turn the cdrom0 writable for the root. But it didn`t work as well.
```

root@bruno-laptop:/media# chmod +w cdrom0
chmod: changing permissions of `cdrom0': Read-only file system

```

What does this means? How do I turn the cdrom0 unaccessible by the others users?

By the way, I know that is not a good idea to have a root user and to login as it but I did it anyway.

Thank you.

Bruno Krebs

---

### Post by Jimmyfj on 2007-08-27
You are able to restrict users by editing their user profile. Go to System/Administration/Users & Groups and create a test user. In User rights you are able to define which rights the user has and amongst those access rights to some hardware.

---

### Post by brunoskrebs on 2007-08-27
Hey man hanks for your help.

But acctually I don`t want to create a new user from the GNOME GUI, I am trying to learn about linux, and its methods (avoiding GUIs).
And I thought that I was able to turn the cdrom0 accessible (browsable) only by the root user. And I was trying to do it from the bash.

 From what I read (the autor sas that I have the full control of my system) I`m pretty sure that I can do this, but I don`t have enough knowledge yet to do.

If you or anyone could explain to me where I misunderstood, and how I have to proceed to turn the cdrom0 unaccessible for the others, I would be very grateful...

Bye
Bruno Krebs

---

