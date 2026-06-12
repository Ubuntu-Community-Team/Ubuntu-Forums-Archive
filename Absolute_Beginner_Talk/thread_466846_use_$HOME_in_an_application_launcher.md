---
title: "use $HOME in an application launcher?"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by justleen on 2007-06-07
Hey there,

I need to create a new application launcher for several users.. the launcher points towards a file in their home dir. 
I can edit each shortcut to point to /home/USER/ but that would be quite a bit of typing.. Is there any way i can use the $HOME variable in a launcher?

if i just try  $HOME/file,  it will try to literally find a file called $HOME.. which it kind find, obviously..

---

### Post by viciouslime on 2007-06-07
Use ~ :)

~/test = /home/<current user>/test

---

