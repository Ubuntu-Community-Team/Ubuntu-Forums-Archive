---
title: "Network"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by linux-beginner on 2006-12-02
Hello,

There are some computers using internet by a hub and a router. I want to set up a network between these computers with a shared folder. My computer is the only computer with linux and the other computers have Windows.
I've installed samba and tried to find the other computers by "Network Servers" option in "Places" menu but I couldn't find other computers.
Could you guide me how I can do that?

Thanks,

---

### Post by Portable_Jim on 2006-12-02
Have you installes samba 

To check (in gnome) go to System --> Administration --> Synaptic Package Manager --> (put in the password as prompted (it will tell you which one)) --> 'Search' --> Type in "samba" --> Search. If the box on the left hand side of the word samba is green, then it is installed. 
If it is an outline, then samba is not installed. If this is so, click on it (and the word 'mark' if a dialog box comes up), then click apply twice (once to bring up a popup window, then the apply, inside the window.)

---

### Post by linux-beginner on 2006-12-02
I've installed both of these pakages "samba" and "smbfs".

---

### Post by Portable_Jim on 2006-12-02
Now see this:
[http://ubuntuguide.org/wiki/Dapper#Samba_Server](http://ubuntuguide.org/wiki/Dapper#Samba_Server)
authough only one part of the tutoral talks about networking, the rest it good as well.

---

### Post by infoseeker on 2006-12-02
At the terminal prompt, enter```
smbtree
```, enter your password, and the windows shares should be listed, together with workgroups.

---

### Post by Scorpuk on 2006-12-02
If none of the above have helped then you might want to try this too:


Activate the guest account on the windows XP machine you want access too.


I had the same problem where my linux box just would not see the shares I had open on my XP box until I did the above.

;)

---

