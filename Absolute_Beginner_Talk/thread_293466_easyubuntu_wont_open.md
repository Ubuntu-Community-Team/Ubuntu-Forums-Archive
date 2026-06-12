---
title: "easyubuntu wont open"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by bobanshirl on 2006-11-05
I have Easyubuntu installed which was working a couple of weeks ago.I recently did some updating and package removal ie language packages and open office.Now when I double click on easyubuntu it asks for my password I get the spinning disc but thats it.I tried in a terminal by typing easyubuntu but it tells me I appear to be running gnome using gksudo.Can anyone help me on this.The reason I removed the language packages etc is I only have dialup and when I get told there are 194 updates for download well it goes on all day,so I removed what I thought I didnt need.

---

### Post by heinouskyle on 2006-11-29
Try sudo /usr/lib/easyubuntu/wrapper.sh

You'll probably get some warnings about no authentication and GTK, but software will still install OK.

---

