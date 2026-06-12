---
title: "Modifying Linsta GTK theme"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by ferpadro on 2007-10-14
Hi everyone! Yesterday i installed Gutsy rc1 on my computer, and so far so good. It seems like the boot time has been improved a little, and the new clearlook window border is amazing. Unfortunately, like previous versions, gutsy also came with the same gray, flat, boring panels, and i wanted them to be black, like the one Vista has. So i searched debian-art.org and found LinSta ([http://www.debian-art.org/content/show.php/LiNsta+%28LiNsta+is+Not+Vista+%3B-%29?content=42697](http://www.debian-art.org/content/show.php/LiNsta+%28LiNsta+is+Not+Vista+%3B-%29?content=42697))

Downloaded, installed it and finally got my black panel the way i wanted to. But also a few things changed its colour:

[http://img149.imageshack.us/img149/6104/pantallazozr7.jpg](http://img149.imageshack.us/img149/6104/pantallazozr7.jpg)

As you see, now the Title Bar is grey and i really prefer the soft blue of clearlooks. Also the menu bar changed to a weird turquoise degrade which is, imho, very disgusting.

So the bottom of the line is: is it possible to have the clearlooks theme but with the LinSta panel instead of the grey one?

Thanks in advance

---

### Post by Lord Illidan on 2007-10-14
Open the archive of the theme and look around for a png which looks like your panel. Then you can take it and use that instead.

EDIT, it is in /LiNsta-GTK2/gtk-2.0/Panel/

There's a nice list of pngs, pick and chose.

---

### Post by ferpadro on 2007-10-14
Excellent, it worked the way i wanted.  :popcorn:

Now i have the last issue, any clue on how to change colour of the panel text from black to white?

---

### Post by Lord Illidan on 2007-10-15
Create a file called .gtkrc-2.0 in your home directory, and paste these lines in it.

```
style "my_color"
{
fg[NORMAL] = "#FFFFFF"
}
widget "*Panel*Clock*" style "my_color"
widget "*Panel*MenuBar*" style "my_color"
widget "*Panel*Task*" style "my_color"

```

---

