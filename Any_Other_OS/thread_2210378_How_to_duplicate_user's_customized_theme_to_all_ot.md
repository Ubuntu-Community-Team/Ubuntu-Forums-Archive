---
title: "How to duplicate user's customized theme to all other users?"
date: 2014-03-10
forum: Any Other OS
---

### Post by sravan2 on 2014-03-10
Hello everyone,

1) I'm trying to create my own customized operating system using linux kernel. In this process, I made my own desktop look for a user and now I am planing to distribute all other       users too. But i am unable to figure out, How to do it? 

2) How to convert my customized OS to iso?

Can anyone Please help me! 

Thank you

---

### Post by buzzingrobot on 2014-03-10
1) You don't mention the GUI you are using, but the usual place for themes visible to all users is /usr/share/themes.

You might be interested in a look around [http://www.freedesktop.org/wiki/](http://www.freedesktop.org/wiki/).

---

### Post by Martinjo84 on 2014-03-10
Copy your configs to /etc/skel

[http://www.remastersys.com/forums/index.php?topic=2639.0](http://www.remastersys.com/forums/index.php?topic=2639.0)

---

### Post by sravan2 on 2014-03-10
I forgot to mention, my GUI. I'm using openbox. Thank you buzzingrobot and Martinjo84, those article are really helpful but i would like to get more information about problem 1. Thank you

---

### Post by vasa1 on 2014-03-11
Are you using Openbox with or without a desktop environment (DE)? If you have a DE, things will be decided by the DE.

But if you're using Openbox alone, as I do, things will be quite different. I have described what I did to get things the way I want in this thread: [http://ubuntuforums.org/showthread.php?t=2173126](http://ubuntuforums.org/showthread.php?t=2173126)

I know this doesn't answer point 1 as you wish but maybe you can get some pointers. All the best.

---

