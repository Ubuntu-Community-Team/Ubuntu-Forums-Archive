---
title: "I can't find ClamAv and Firestarter"
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by nala on 2006-03-10
I installed ClamAv and Firestarter through Synaptic, but I can't seem to find them. The starter guide says that they should be under applications > system tools, but they aren't there. Apologies for the newbishness. I had this same problem when I installed g++.

---

### Post by Brunellus on 2006-03-10
you may have to kill and restart gnome-panel.

Or, failing that, add them yourself using the menu editor.

---

### Post by Perfect Storm on 2006-03-10
try killall gnome-panel, then you'll (hopeful) see firestarter. ClamAV you have to run in command as I recall it.

---

### Post by nala on 2006-03-10
I'm still brand-new to Linux, so I'm sorry if I'm a bit slow on this. I want to make sure that I'm following what you're telling me. I'm supposed to type killall gnome-panel in the terminal? Is that all I have to do? I don't know how to use the menu editor, and I don't know how to run clamav in the terminal.

Are there any good newb guides to Linux that I can read online/buy at a bookstore? n.n;;;

---

### Post by Perfect Storm on 2006-03-10
ah, sorry..yes write **killall gnome-panel** in the terminal, this will reload/restart the panel. To edit the application tab write: **smeg** in the terminal.

---

### Post by 11hjpphty76lkjj on 2006-03-10
For a beginner wouldn't just ctrl-alt-backspace be easier to restart gnome?

Aaron

---

### Post by Brunellus on 2006-03-10
[QUOTE=kalosaurusrex]For a beginner wouldn't just ctrl-alt-backspace be easier to restart gnome?

Aaron[/QUOTE]
that would kill the whole xsession and everything in it.  NOT nice if you have open apps with unsaved data.

---

### Post by Perfect Storm on 2006-03-10
Depends what he want to do in my opinion. It's only the panel who needs to get restarted and why not learn it from the start ;)



Someone mention about a book here: [http://ubuntuforums.org/showthread.php?t=91938](http://ubuntuforums.org/showthread.php?t=91938) for newbies. I havn't read the book but you might take a look at it.

---

### Post by 11hjpphty76lkjj on 2006-03-10
Good point!  I stand corrected.  and learned. hehe

---

### Post by nala on 2006-03-10
Thanks everyone!:KS

---

### Post by NoNo_231 on 2006-03-12
ClamAV is loaded in the background and checks the e-mail attachements. However if you want a frontend you could install also clamtk (from the synaptic). To start this I think that you also have to start it from the terminal. But you could go to apllications menu editor and make a new entry wherever you wan. You will write to the command line clamtk and you can loaded from the menu.

---

