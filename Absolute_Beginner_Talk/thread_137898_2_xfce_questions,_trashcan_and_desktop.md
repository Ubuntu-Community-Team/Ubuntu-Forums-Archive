---
title: "2 xfce questions, trashcan and desktop"
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by grimdaze on 2006-02-28
i just installed xubuntu a couple days ago but i can't seem to figure out these two things:
i must be totally blind but where is the trashcan in xfce?
and
how do i get the desktop drawn instead of having to go to the folder? can i do it without using another window or desktop manager?

---

### Post by Pragmatist on 2006-02-28
This should answer your trash can question: [http://www.xfce.org/documentation/docs-4.0/xffm.html#xffm-wastebaskets](http://www.xfce.org/documentation/docs-4.0/xffm.html#xffm-wastebaskets)

> how do i get the desktop drawn  What does that mean?

---

### Post by jbmalone on 2006-02-28
I don't think it has a trashcan.  I believe it just deletes it forever.

---

### Post by grimdaze on 2006-02-28
>  What does that mean?

where folders and files and stuff are shown, instead of just the wallpaper.
i have stuff on the desktop but can only view it through the filemanager, i can't just look "at" the desktop and use or even see them.

[http://img148.imageshack.us/img148/3769/snap16no.png](http://img148.imageshack.us/img148/3769/snap16no.png)
[http://img146.imageshack.us/img146/6707/snap29qz.png](http://img146.imageshack.us/img146/6707/snap29qz.png)

those should show you what i mean

> This should answer your trash can question: [http://www.xfce.org/documentation/do...m-wastebaskets](http://www.xfce.org/documentation/do...m-wastebaskets)

oh, ok. thanks. one problem solved.

---

### Post by Pragmatist on 2006-02-28
Here is an obvious question.  Is anything in your $HOME/Desktop directory?? ```
ls $HOME/Desktop
```

---

### Post by grimdaze on 2006-02-28
[QUOTE=Pragmatist]Here is an obvious question.  Is anything in your $HOME/Desktop directory?? ```
ls $HOME/Desktop
```[/QUOTE]

```

grimdaze@grimdaze:~$ ls $HOME/Desktop
c++  grim  pascal  roms  web
grimdaze@grimdaze:~$

```

i still have gnome and nautilus. if i launch nautilus, my gnome desktop gets drawn with my gnome icon theme and my gnome wallpaper but i was hoping there was a way to draw the desktop with xfwm or some other xfce component instead of using nautilus.

---

### Post by kaamos on 2006-03-01
I think that can be done with the xfce version in dapper. For breezy, you'd have to use some additional program to do that.

---

