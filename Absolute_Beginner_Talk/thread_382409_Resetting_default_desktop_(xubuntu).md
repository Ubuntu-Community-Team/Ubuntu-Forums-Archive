---
title: "Resetting default desktop (xubuntu)"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by CanadaGradeEh on 2007-03-12
I messed my desktop up beyond newbie functionality, so would like to set the desktop settings to default. Id like to know how I could go about this; I was hoping I could enter a command in either the terminal or alt-f2 prompt that would bring up some option to set it to defaults since I know I can access those :P

That, or giving a new user some root privileges -- I created a new in the terminal to gain back my default desktop, which I fortunately have now on said account, but I cant access Users and Groups (restricted).

---

### Post by CanadaGradeEh on 2007-03-12
PS - sorry about the lack of question marks and other punctuation, but I have the wrong keyboard set... yea, I should go change it. Heh.

Help, please!

---

### Post by siciliancasanova on 2007-03-12
EDIT:  Gave you the wrong code, this is the code I meant to give you:

```
sudo aptitude remove xubuntu-desktop
sudo aptitude update
sudo aptitude install xubuntu-desktop
```

---

### Post by CanadaGradeEh on 2007-03-12
Thanks a lot, but it didnt help :( By the way, Im in the account right now.

Basically, what I was doing was fooling around with desktop toolbar or panel settings. I was creating and adjusting them, and I went to delete a few I created but instead of deleting them then automatically going to the one preceding what was just deleted, it went straight back to panel one. Without thinking I just deleted a bunch before I realized I deleted the default panels. Im not too sure how to set them up properly again, and was hoping -- as Ive said -- that I could simply find a default restore option. It would be a lot nicer then going through and manually setting the whole thing up again. If that is what I must do, though, then I think I will just let a re-install happen over-night since it would be faster :P

---

### Post by CanadaGradeEh on 2007-03-12
Last call for help! Im sorry for double-posting, but Id like to not have to re-install again since Ive done it a few times already getting used to partitioning and boot management with Linux (GRUB I guess, since I havent used Lilo yet).

---

