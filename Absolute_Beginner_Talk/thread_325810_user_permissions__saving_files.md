---
title: "user permissions / saving files"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by thaKing on 2006-12-26
i'm new to ubuntu (and linux for that matter) and i have a question regarding user persmissions...what is root, is it the main admin? and should it have any permissions for its group? i'm logged in on my machine as thaKing (do i need to setup permissions for myself)....i have gone to /etc/firefox/profile/chrome/ to modify the userChrome.css file...however, it won't allow me to save it stating i don't have the proper permissions...as i am the only one who will be using this, how do i go about properly setting up my user acct so that i can save/modify files?

---

### Post by taurus on 2006-12-26
Basically, you can only write and modify stuff in your own $HOME directory, /home/thaKing.  Therefore, if you want to modify something outside of that, you need to use the sudo command...

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/firefox/profile/chrome/userChrome.css
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by steve.horsley on 2006-12-26
Read the link that Taurus gave you. But as a quick guide, yes, root is the administrator. You don't assign those rights to yourself, but use the sudo (SuperUserDo) command to run processes with root's privilege. A very useful (and suitably dangerous) command is **gksudo nautilus** which gives you a file manager window with full privilege. Use it with care. I set a coloured background on mine to remind me it's root's manager.

---

