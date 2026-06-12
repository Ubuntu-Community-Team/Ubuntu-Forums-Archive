---
title: "Sudo File Browser"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by kingpoiuy on 2007-03-28
I just tried to add "sudo" to the beginning of the command for my "file browser" in the menu editer.  It said it was starting and then it just disappeared.  I was hoping to use this to change permissions to folders so I don't have to use the terminal. 

Not that I don't like the beloved terminal but I like to setup linux computers for windows users to try out.  And why not have a way to do some of these things in GUI anyway?  

So anyone know why it would die on me like this?

Thanx!

---

### Post by Catsworth on 2007-03-28
There's a nautilus script that allows you to right-click on a folder and select an 'open root nautilus here' type of option.  You are then asked for your password and, if you enter it correctly, you get a nautilus file explorer window but with root priviledges.

Can't remember where I found it though, a quick search of the forums should reveal it I would have thought.

---

### Post by Catsworth on 2007-03-28
Alternatively, try *gksudo* instead of *sudo*, it may work better.

---

### Post by Degeim on 2007-03-28
If I understand you right, you added "sudo" to the beginning of the command in **the menu editor**.

If that's so, try adding "gksu" instead of "sudo". This will give you a graphical login box, and will work from the menu. "Sudo" is for the terminals, as far as I know.

Degeim

---

### Post by kingpoiuy on 2007-03-28
Awesome yes it worked.  I also found out that sudo will work if i click the run in terminal box.

Thanx

---

### Post by aysiu on 2007-03-28
You should use *gksudo*, though.

More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

