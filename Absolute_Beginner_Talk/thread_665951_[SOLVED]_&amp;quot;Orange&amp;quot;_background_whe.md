---
title: "[SOLVED] &amp;quot;Orange&amp;quot; background when logging in [Video] [Pictures]"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by alecwh on 2008-01-12
Alright, this is a small annoyance I have been experiencing while using Ubuntu. This is pretty small, but it's always like "ah, that's terrible. I gotta fix that" whenever I login, and I then forget about it. Luckily, this time I remembered to write this up.

Whenever I login to ubuntu (Gnome + Face Browser login window), seconds after, I'm presented with an orange background for a few seconds. It might seem small, but it sorta ruins the atmosphere I'm trying to create with my desktop. I know it's sort of hard to see what I'm talking about, so I have taken a video (mpeg, avi) and some pictures. Pictures of the orange screen:

[IMG]http://img339.imageshack.us/img339/695/screenshot1fe2.png[/IMG]

[IMG]http://img110.imageshack.us/img110/8648/screenshot2ci4.png[/IMG]

A few seconds after that, I get this:

[IMG]http://img110.imageshack.us/img110/5597/screenshot3qo7.png[/IMG]

How can I get rid of that orange background, or change it to a different color?

Video:
Took to long to upload, and I got the answer before it finished. =)

Thanks in advance.

---

### Post by Arthur Archnix on 2008-01-12
```
gksudo gedit /etc/gdm/PreSession/Default
```

Then change at the bottom backcolor = "x" from "#dab082"
```
# Default value  
      if [ "x$BACKCOLOR" = "x" ]; then  
          BACKCOLOR="x"  
      fi
```

At that point it should take on the background colour that you specify in  >system>administration >login window preferences.

---

### Post by alecwh on 2008-01-12
That worked perfectly! Thanks a lot, that makes everything a lot better. It actually retains the background image, instead of just a color.

---

### Post by Can+~ on 2008-01-12
Mark it as solved.

And, there's also the non-command approach.

> Administration > Login Window > [tab]Local > Background color

---

### Post by alecwh on 2008-01-12
I don't know why, but it just added &quot;'s to the title. Maybe a moderator could fix this?

---

### Post by Arthur Archnix on 2008-01-12
> **Can+~ said:**
> Mark it as solved.

And, there's also the non-command approach.

Good to point out. The solution above is only for those affected by[ bug #132833]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/132833")

---

