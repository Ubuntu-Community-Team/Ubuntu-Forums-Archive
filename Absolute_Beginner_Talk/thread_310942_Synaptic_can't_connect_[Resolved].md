---
title: "Synaptic can't connect [Resolved]"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by Popbot on 2006-12-02
Hey all, I'm completely new to this and so I cannot for the life of me figure out how to get synaptic to get updates. When I run it from the GUI or when I just run apt-get update I get this error:

```
E: Malformed Line 2 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)
E: unable to lock the list directory ###This only comes up if I try to update through the gui

```

I can connect to the internet just fine, so I don't know why it won't retrieve anything. It says something about going to repositories, but when I check in on that it looks the same as when I could get updates.

I have no idea what to do. 

](*,)

*edit*

Fixed, in case anyone wants to know I just moved the file edgy-universe.list to my home directory. Something was funky with it, but now it's not doing any more damage.

---

