---
title: "[SOLVED] I lost my user and groups tool"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by layst on 2008-02-12
Hey,
I was editing my user privileges, and i disabled all my privileges in my main account. Now there is no User & Groups tool under my administration tab, therefor i cant re-enable all my privileges.  half of my admin tools are all gone aswell. Can anyone please help me. i need to update but it wont let me do anything.

---

### Post by nemilar on 2008-02-12
Can you still sudo?  If so, use

```
gksudo gnome-control-center
```

Which should give you a complete control center window.  I don't know the name of the users and groups controls command, but you can access it through the control center easily.

If you can't sudo...do you have a root password set?  If so, you can

```
su
gnome-control-center
```

If you can't get superuser at all, you'll have either boot into single-user mode, or use a LiveCD to fix things.

---

### Post by nikoPSK on 2008-02-12
> **nemilar said:**
> Can you still sudo?  If so, use

```
gksudo gnome-control-center
```Which should give you a complete control center window.  I don't know the name of the users and groups controls command, but you can access it through the control center easily.

If you can't sudo...do you have a root password set?  If so, you can

```
su
gnome-control-center
```If you can't get superuser at all, you'll have either boot into single-user mode, or use a LiveCD to fix things.

as stated try sudo and use your root pw.

---

### Post by layst on 2008-02-12
My friend. problem solved. Cheers heaps.

---

### Post by nikoPSK on 2008-02-12
> **layst said:**
> My friend. problem solved. Cheers heaps.

Please:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Best,
nikoPSK

---

