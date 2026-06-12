---
title: "No sound after GDM"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by dermotti on 2006-04-17
When i boot up my system, GDM makes its little drumbeat sound. When i Login, i cant get any sound.

i'm using XFCE4

Ideas?

---

### Post by dermotti on 2006-04-17
Hmmm looks like possibly a permission issue, reading the forums. I belive the user need to be added to the audio group...

Using the "Userd and Groups" program i cant seem to figure out where to give the user audio permission....

---

### Post by xXx 0wn3d xXx on 2006-04-17
[QUOTE=dermotti]When i boot up my system, GDM makes its little drumbeat sound. When i Login, i cant get any sound.

i'm using XFCE4

Ideas?[/QUOTE]
Did you make sure that nothing is muted ? In terminal type: "sudo alsamixer" and make sure nothing is muted/turned down really low.

---

### Post by dermotti on 2006-04-17
Checked that earlier, nothing muted...

---

### Post by dermotti on 2006-04-17
Hm but sound works fine in Unreal tournament.....

---

### Post by xXx 0wn3d xXx on 2006-04-17
[QUOTE=dermotti]Hm but sound works fine in Unreal tournament.....[/QUOTE]
Thinking back to when I used XFCE on my new (and current) computer. I don't remember having sound either, even though I have it in Gnome. Maybe you could try and compile the latest release if it is not included in breezy/dapper if that's what your using.

---

### Post by dermotti on 2006-04-17
Yea its a fresh insall of dapper xubuntu....hmmmm....

---

