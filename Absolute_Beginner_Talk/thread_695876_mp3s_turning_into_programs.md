---
title: "mp3s turning into programs"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by speedjunkie on 2008-02-13
hey all I am a new ubuntu user that has migrated from the not-so-wonderful world of windows.  I moved all of my mp3s and video files from my windows partition onto the linux partition (dual boot vista and ubuntu fyi).  The files at first played fine up until i started moving them around into different folders and the turned themselves into programs.  I have also noticed that when this happens i cant open another folder, it just says "cant display the contents of x folder".  if i was to restart the computer it fixes the problem, but it happens again after a while.  I have had this problem before when i was using two seperate computers, one with linux and one with vista and using samba to connect the two, and i tried to view a linux format partition on the windows machine.  Does anyone know whats going on?

---

### Post by OffAxis on 2008-02-13
I don't know about turning themselves into programs, but if you're having problems with access it might be a permissions problem.

next time it happens try running an 
```
ls -l
```

to see how the ownership looks. Ubuntu will change permissions to the user who brings the file over from the windows side, and if you use a 'sudo' to move things it may assign ownership to root.
and if you're using windows to manipulate the file after the fact then all bets are off.

you can use 
```
sudo chown username:groupname filename
```

to modify the ownership.

---

