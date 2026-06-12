---
title: "Look, I just want to know how to make GUIS with C++ on linux.."
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2006-10-06
I just need to know where to look..

I want to program c++ on a low level and create guis with forms and buttons etc..
I am profficient with c++.

What are my different options..

Windows has windows api, where you can just program low level and call up forms from scratch.. OR windows has MFC, which wraps c++ objects around these api calls..


HOW is this done in linux... What is the low level way.. What are some good wrapping classes?  GTk? GTKmm?

Thanks everyone.

---

### Post by DSn0wMan on 2006-10-06
I just use mono for GUI stuff. It uses C# and GTK+. I am sure that there are some C++ API's for GTK+.

---

### Post by CatKiller on 2006-10-06
You could try asking in the Programming Talk forum. Or just browsing there for a while. I don't think that Absolute Beginner is necessarily the right skillset for the people that you'd like to read your post.

EDIT: Guess I'm wrong. Good luck, anyway.

---

### Post by pgatrick on 2006-10-07
I guess if you use gnome gtk is a good one to start with, or you can just do x programming. [http://tronche.com/gui/x/xlib/](http://tronche.com/gui/x/xlib/)
Hope that helps, I don't know too much about it.

---

### Post by systemintheglitch on 2006-10-07
Hmmm.. looks like gtkmm uses automatic memory allocation.. Thats not gonna work for me.. Looks like ill make my own gtk wrapper that is more lightweight.

---

### Post by maaronB on 2006-10-07
I don't know how lightweight it is but you could look at wxWindows.

---

### Post by pgroover on 2006-10-07
I personally prefer Qt, especially if you're not creating anything commercial.  It's very extendable and easy to understand.

---

### Post by 3rdalbum on 2006-10-07
wxWindows is now called wxWidgets.

Are you interested in writing a C++ backend and then using a program to generate the C++ code for the GUI? If so, you could look at Glade and wxGlade (the former does GTK). That could be a good learning excercise too if you want to really program the interfaces all by yourself.

---

