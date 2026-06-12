---
title: "Hi all : ) Just a tiny question (1st post)"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by Jabb3r on 2007-08-18
First off I just want to say that switching to linux has interested and excited me for a long time (yes I'm sad like that) but I think I've finally found a distro I feel comfortable doing this with and with the ever increasing functionality of vmware it's a match made in heaven so cheers!

Now, about that small problem I'm having. It seems that no matter how I try I can't seem to add anymore users, I've tried from the command line and got errors about things not starting when I tried to login, tried with the  gui and it just doesn't create a home dir etc and when I go back to the user panel in the gui my newly created user has dissapeared and can't work out for the life of me why. Couldn't find much about problems I'm havin either on the boards or in google and what I did find relaed to a diff version and wasn't helpful

I'm using Ubuntu 7.04

I am a complete novice to this, been reading tutorials like they goin outta fashion to try and get a grip on linux, but I am very limited on my knowledge atm, but more than willing to learn, I'm havin such a blast! :D

Hope someone can point me in the right direction and a big thank you to the ubuntu team, you've done an awsome job!

Cheers!

---

### Post by RaZer0r on 2007-08-18
you can add users using folowing code

```

sudo adduser <username>

```

It will prompt you with further questions (like pass etc, you can leave those fields blank.

---

### Post by Jabb3r on 2007-08-18
Hi, thanks for your suggestion, I have tried it previously, but this is the kind of thing thats happening, hope you understand

jabb3r@Pluto:~$ sudo adduser sandbox
Password:
adduser: The group `sandbox' already exists.
jabb3r@Pluto:~$ passwd sandbox
passwd: unknown user sandbox
jabb3r@Pluto:~$ su sandbox
Unknown id: sandbox
jabb3r@Pluto:~$ 


Thanks!

[Edit]
It never asks me for a passwd after I execute the sudo command btw, just pauses for a second and then goes back to prompt

---

### Post by Jabb3r on 2007-08-18
Bumpag, I knew I shouldda titled the post better

---

### Post by schorsch on 2007-08-18
Per default when using the adduser command ubuntu creates a new group with the same name as the user and uses this as the primary group of the user. So if the group sandbox already exits you get mentioned error message. To add an user to an already existing group you have to use:
```
 sudo adduser --gid XYZ sandbox
```
The value for "XYZ" (the gid or Group ID) do you get, when you search for the group name in the file /etc/group:
```
grep sandbox /etc/group
```
This will result in the follwing output:
```
sandbox:x:XYZ:
```

---

### Post by Jabb3r on 2007-08-18
Thank you muchly, that did the trick1 I'm still working out what I done wrong, but thanks alot, thats cleared up the only prob I've been havin so far. :)

---

### Post by GuitarRocker2562 on 2007-08-18
By the way, you may want to check out wubi (google it) it will be faster than vmware but without changing your hard drive setup.

---

