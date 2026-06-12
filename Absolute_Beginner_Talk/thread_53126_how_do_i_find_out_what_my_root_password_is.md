---
title: "how do i find out what my root password is?"
date: 2005-07-30
forum: Absolute Beginner Talk
---

### Post by porsher_puddles on 2005-07-30
i don't remeber ever setting one, i just have my login password. i am trying to open qparted which i just installed but it keeps asking me for the root password and it won't take no for an answer.
anyone know whats the go here

---

### Post by pataphysician on 2005-07-30
i think you just use your password.

---

### Post by Sam on 2005-07-30
Because it's YOUR password !!

Informations [here](https://wiki.ubuntu.com/RootSudo).

---

### Post by porsher_puddles on 2005-07-30
when i use my login password it says wrong password

---

### Post by KrisDwyer on 2005-07-30
[QUOTE=porsher_puddles]i don't remeber ever setting one, i just have my login password. i am trying to open qparted which i just installed but it keeps asking me for the root password and it won't take no for an answer.
anyone know whats the go here[/QUOTE]
 sorry to be rude man, but it sounds like u have a case of 'wheres my any key' syndrome...

---

### Post by nootdog on 2005-07-30
[QUOTE=porsher_puddles]i don't remeber ever setting one, i just have my login password. i am trying to open qparted which i just installed but it keeps asking me for the root password and it won't take no for an answer.
anyone know whats the go here[/QUOTE]

I had a similar problem.  When I was logged into the system and tried to change to "Root" my password didn't work.  Then I thought "did I ever set a root password"?  So then I went into my Root Terminal, used the same password to get in (which was weird too me) and I was in my root terminal.  The same password that didn't work when I wanted to su into Root ... worked to get in Root Terminal.
So as I'm in the Root Terminal I change the root password and then I'm able to change to super user in regular terminals.


Hope this makes sense.

---

### Post by porsher_puddles on 2005-07-31
hi again
look i tried opening my root terminal typed in my password and it works fine.
when i try qparted it asks me for my root password i type it and it says this
failed to run /usr/sbin/qparted as user root: child terminated with 1 status or sometimes it says root password incorrect.
whats going on?

---

### Post by Wi-Fi on 2005-07-31
Ubuntu doesn't tell you or ask you to set a root password when you install, but you can change it by "sudo passwd root".

---

### Post by TravisNewman on 2005-07-31
Did nobody read Sam's link?

---

### Post by porsher_puddles on 2005-08-01
ty for that wi-fi i reset my password and its fine now

---

