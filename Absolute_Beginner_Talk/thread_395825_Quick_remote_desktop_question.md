---
title: "Quick remote desktop question"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by Error47 on 2007-03-28
I gave someone online permissions to view my desktop. I was chatting with him for help, and I came up with the remote desktop idea. I allowed him to connect, he can see my desktop. How do I know when he can see or not see my desktop? How do I terminate the session when I don't want him to see or control my pc anymore?

---

### Post by hfranco on 2007-03-28
You can have Ubuntu request permission from you first to connect remotely.

I think the best way to fix this is to change your password if you gave him your account info.  If you created a user for that remote desktop session then just delete that user.

---

### Post by Error47 on 2007-03-28
There is no account info, all he needs is the IP. I can change the password yeah, but I don't know if it would take effect. I need alot of help using some stuff in linux and the remote desktop helps alot. I just need to know how I can terminate the session if I need to. I only gave him access to view my desktop while I did the work. How can I know if he can see it or if he disconnects? What if I gave him access to control my desktop, how can I resume control just incase he tries something I don't like.

---

### Post by hfranco on 2007-03-28
Ok I understand now.  You can type who-u in a terminal and kill the user right there.

so:

hfranco@ubuntu:/home/hfranco# who -u
hfranco    pts/1        2007-03-28 21:41   .          2408 (192.168.0.100)
hfranco@ubuntu:/home/hfranco# kill 2408

---

### Post by halitech on 2007-03-28
go into System - prefs - remote desktop and uncheck where it says Allow others to view your desktop and that should make sure he can't

---

### Post by Error47 on 2007-03-28
I installed VNC on my other computer and saw how it works. What happens if I have access for this person to control my computer, they have access to the terminal and everything. They could easily format the drive or do something, no?

---

### Post by halitech on 2007-03-28
> **Error47 said:**
> I installed VNC on my other computer and saw how it works. What happens if I have access for this person to control my computer, they have access to the terminal and everything. They could easily format the drive or do something, no?

if you gave them access to control the system then yes, they could do pretty much anything you could do at the computer. best thing would be to disable the remote access.

---

### Post by Error47 on 2007-03-31
Can it be hacked? If I have it enabled, but change the password, is it easy to still get in? I don't know if the password would do much, can somebody brute force it or something?

---

### Post by halitech on 2007-03-31
if you are that concerned about it, best thing to do is turn it off. Even as good as linux is, the only truely secure box is the one thats in a closet with no power hooked up to it.

---

