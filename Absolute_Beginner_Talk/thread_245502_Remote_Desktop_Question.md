---
title: "Remote Desktop Question"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by jbmalone on 2006-08-27
All right you guys.  It has been a while since I have posted up a question because thanks to your help, I've been able to figure out a lot of stuff on my own, but now I am at a crossroads with stuff I have never worked with before.

Here's my situation:

I am at school and want to download some stuff through torrents (linux distros, etc.) so, I want to be able to remote desktop into my computer back at home, download the torrent and then ftp it to myself at school.  Anyways, I have OS X at school and either XP or FC5 or Dapper at home (which ever is easiest for this process).  My main question, is what do I need to set this up?  I have used FTP before, but never set up my own server.  Can you guys help me out?

Thanks,
Jacob

---

### Post by aysiu on 2006-08-27
OS X can use Chicken of the VNC to remote desktop into Windows and/or Linux. For Windows, I'd advise TightVNC. Ubuntu has Vino, which can be set up by going to System > Preferences > Remote Desktop.

Keep in mind that VNC may not be the most secure. If you have the patience to go through the HowTos, you might want to look into SSH and FreeNX.

---

### Post by jbmalone on 2006-08-28
Can the HowTos on SSH and FreeNX be found here on the board?  Or would it best to Google them?

---

### Post by aysiu on 2006-08-28
> **jbmalone said:**
> Can the HowTos on SSH and FreeNX be found here on the board?  Or would it best to Google them?
A little of both.

[Here's an example](http://www.google.com/search?num=100&hl=en&lr=lang_en&safe=off&q=site%3Aubuntuforums.org+freenx+ssh+howto&btnG=Search).

---

### Post by jbmalone on 2006-08-28
Ha, thanks man for your help.  Just to ask, what is the security like on the Chicken and TightVNC programs?

---

### Post by aysiu on 2006-08-28
> **jbmalone said:**
> Ha, thanks man for your help.  Just to ask, what is the security like on the Chicken and TightVNC programs?
I think it's pretty lousy from what I've heard from more knowledgeable users.

---

### Post by jbmalone on 2006-08-28
I read a lot of the links around the site and from some of the program sites that you sent me, and I think that I am just going to use FreeNX.  I can load the Free Personal Server on my linux box and then run the OS X client from school, and I should be ok.  

Thanks a lot for your help man.

---

