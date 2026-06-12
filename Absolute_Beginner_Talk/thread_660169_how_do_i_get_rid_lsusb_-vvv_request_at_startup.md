---
title: "how do i get rid lsusb -vvv request at startup?"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by shuRe on 2008-01-06
Hi everyone,
Just to start by saying i have been complete microsoft geek all my life, tried recently to have a go at mac osx but failed, and remembered i tried ubuntu ages ago with no luck on a older computer, anyway cut to the chase, i am now trying to work my computer use round ubuntu, i find it brilliant, from its simplicity and cleanliness to its great user support for compatibility with issues such as being able to use microsoft office docs!

I have however got carried away with running commands in the terminal, mainly installing and updating, but along the line i must have done something to get this annoying popup window at startup. Basically a window will come up and request a password saying 'the application 'lsusb -vvv' lets you modify essential parts of your system'. 

Its not a major problem because i can enter my password and away it all goes, but i want to show my friends how good ubuntu is and dont want to put them off with slight complications like this.

Any help would be much appreciated, and i really have found this forum awesome for help with other issues i have had.

---

### Post by blueridgedog on 2008-01-06
Two places to look:

System -> Sessions -> start up programs tab

also

```
cat /etc/rc.local
```

---

