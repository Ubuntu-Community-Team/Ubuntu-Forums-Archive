---
title: "Editors that support windows line breaks?"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by Zeroangel on 2006-03-18
Hey all.

I'm working on a project that requires me to edit and exchange text files with windows users. However, every time I make an edit to a file using gedit, it converts the line breaks to unix line breaks which windows text editors do not understand.

Can anyone tell me how I can enable windows line breaks in gedit, or does anyone know of an app that I can use that will write Windows line breaks?

Thanks in advance,

---

### Post by jpkotta on 2006-03-18
Any decent editor should be able to do that.  I would go so far as to say any editor that didn't handle both Unix and DOS linebreaks is not decent.  Gedit probably has a way to do it, but I'm not sure because I don't use it.  Emacs will automatically save in whatever format the file was originally in, and there is a function to convert a file as well.  Nedit has a Save As option that lets you set the format.

The easiest way is to use this script and use whatever editor you like.  It is untested but should work.

---

### Post by steve.horsley on 2006-03-18
In gedit, you can search and replace-all "\r\n" with "\n" to remove the CR and convert from DOS to Unix format. Then when exporting back, you can replace all "\n" with "\r\n". It doesn't look any different in gedit on the screen, but in the saved file it does.

P.S. Wordpad doesn't mind showing files with Unix line-endings.

---

