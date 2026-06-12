---
title: "it asks for a password that isn't there"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by benner on 2006-11-24
i have 2 machines running through a router.  1 is ubuntu 1 is windows.  they see eachother and the windows machine can read from the ubuntu (can't write and I don't know why because i have folder sharing 'read only' unchecked) but the real problem that i can't get is that the ubuntu machine asks for a password to access the windows box.  i don't have any password set up on windows.  
i was having trouble going the other way until i found a very helpful post that told me to set up a password for samba (smbpasswd -a 'username') and after reading a million indecipherable posts, i got it sorted and can go one way.  but the ubuntu machine still can't get into the windows one.  can anyone help?

---

### Post by compwiz18 on 2006-11-24
I have the same problem with Windows.

---

### Post by kd_pease on 2006-11-24
When you first set up Windows it probably asked you for a password - that's probably the one you need. 

Alternatively if you look under either "User Accounts" or "Security" (I forget exactly what it's called) in the Windows control panel you should be able to set/change the password for the current user. Once you've done that, try using that password to connect.

---

### Post by louieb on 2006-11-24
I have the same thing 2 PCs one XP one Ubuntu connected to a router.

If I remember right what I did when asked for my windows uesr name and password  was give it my user name and leave the password  blank. That worked for me. (file and printer shareing).

---

