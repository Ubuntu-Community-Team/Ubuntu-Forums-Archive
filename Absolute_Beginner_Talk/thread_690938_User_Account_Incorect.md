---
title: "User Account Incorect"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by hobohitman on 2008-02-08
I just finished installing 7.10 Server Edition and I am dual booting with Vista 64 bit. When I attmept to log in I get my problem. 

In the "User Name" field I can enter my user name fine, but after I hit enter and I get to the "Password" field, I cant type anything unless I hit enter again, and when I enter my password it tells me that it is incorrect. I installed twice to make sure that I didnt mistype something along the line, and everything checked out fine.

Any suggestions?

And one more quick question. This is my first time using Linux/Ubuntu, and I am doing it because I want to set up a web hosting server for my school that people can test web pages on. Would it be best to use the server edition or the Desktop edition?


SOLVED

---

### Post by amingv on 2008-02-08
I am not sure if I understood well what you mean, but when you type in your password it won't show up.

Just put your username and then type in your password (even if it doesn't look like you're typing anything) and press enter. It should login with no problems.

---

### Post by hobohitman on 2008-02-08
I was struggling best how to word what I meant, but you described exactly what happened. It appeared like nothing was happenening, so after I pressed enter again and type my password showed up, but not as ******, as the actual password. Thanks, Ill give that a try.

---

### Post by aysiu on 2008-02-08
> **amingv said:**
> I am not sure if I understood well what you mean, but when you type in your password it won't show up.

Just put your username and then type in your password (even if it doesn't look like you're typing anything) and press enter. It should login with no problems.
More details here:
[http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal)

---

### Post by jrd on 2008-02-08
> And one more quick question. This is my first time using Linux/Ubuntu, and I am doing it because I want to set up a web hosting server for my school that people can test web pages on. Would it be best to use the server edition or the Desktop edition?

If you are new to Linux then I would suggest using the desktop instead of the server. This way you can set everything up with a gui then turn the gui off once you have it configured.

Just post back here if you need any help setting everything up...or pm me, I'll be glad to help

---

### Post by amingv on 2008-02-08
> **jrd said:**
> If you are new to Linux then I would suggest using the desktop instead of the server. This way you can set everything up with a gui then turn the gui off once you have it configured.

Just post back here if you need any help setting everything up...or pm me, I'll be glad to help

<opinion>
I personally suggest to stick to the server edition and install a DE, and then when you get the hang of it, remove it and go back to CLI. This is because the server edition's kernel is optimized for server tasks (or at least that I've heard). Webmin is also a good choice.
</opinion>

---

### Post by jrd on 2008-02-08
Very good point.

---

### Post by hobohitman on 2008-02-08
I dont mean to sound like a failure, but is DE desktop edition?

---

### Post by hyper_ch on 2008-02-08
no, DE is a desktop environment.

---

### Post by hobohitman on 2008-02-08
How do I get a DE for Server edition then if you dont mine me asking?

---

### Post by hyper_ch on 2008-02-08
For Gnome: 
```

sudo aptitude install ubuntu-desktop

```

For KDE:
```

sudo aptitude install kubuntu-desktop

```

For Xfce: (I prefer that one here)
```

sudo aptitude install xubuntu-desktop

```

---

