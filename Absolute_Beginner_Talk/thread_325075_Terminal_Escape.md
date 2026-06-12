---
title: "Terminal Escape?"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by alx_amvs on 2006-12-25
I am kind of a new user to Linux in general please bear with me if I am just sounding completely stupid and ignorant here but i can't seem to find an answer after seaching the FAQs and the forums. If I have missed the answer please accept my apologies.

I have just installed Ubuntu 5.10 on one of my computers. The problem is that when i tried it with the live cd it was already booted into the shell. I am currently stuck in the terminal/command prompt and I have no idea what i am doing here. I assume there is a way to get into the shell from here aside from just using the live cd. Is what do i need to do to get there if you please? 

Once again I am sorry for sounding totally ignorant, but in truth that is what i am when it comes to Linux which is why i am asking.

---

### Post by MkfIbK7a on 2006-12-25
type 
startx   or alternativly
Xinit

---

### Post by alx_amvs on 2006-12-25
That is doing nothing on this computer. Its telling me command not found on both of those, from the directory i start off in (home/alex) nor from home or root. Am I doing something wrong?

---

### Post by cilynx on 2006-12-25
Sounds to me like you did a server install or in some other way told it not to install the desktop graphical system.  If you have network access or access to your installation media, try 
```

sudo apt-get install ubuntu-desktop

```

---

### Post by MkfIbK7a on 2006-12-25
can you do recovery mode (press escape wile loading grub)?

---

### Post by alx_amvs on 2006-12-25
Well I am going to try re-installing it. Perhaps that will help. Thanks for all your help.

---

### Post by MkfIbK7a on 2006-12-25
No Problem thats what we are here for :D

---

### Post by kinson on 2006-12-25
> **alx_amvs said:**
> Well I am going to try re-installing it. Perhaps that will help. Thanks for all your help.

Just a suggestion, but if you're gonna try re-installing, you might wanna try re-installing with 6.06. I tried installing with 5.10 back then, and didn't enjoy it too much, but installation is much easier(smoother :p ) with 6.06 :)

Cheers,
Kinson

---

