---
title: "How Can I gunzip a file in /usr/share/doc?"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by wmichaelb on 2007-05-13
I have a long standing interest in outline processors, which led me to NoteCase. But I've had some problems figuring out how this thing works, and could find no help file. With a little sleuthing, I found that the help file was there, but was just zipped. However, if I try to unzip it, the system tells me that I don't have the permission to do that. So...how do I unzip /usr/share/doc/notecase/notecase/help.ncd.gz? I've tried both double-clicking on it, and gunzipping it via the command line.

Thanks!

---

### Post by Pobega on 2007-05-13
You can read it with a text editor still, just make sure to open it through sudo/gksudo. Usually I read docs using Vim, which I'm most comfortable with, but if you want to do it in a terminal you can always do:

sudo cat /usr/share/doc/notecase/notecase/help.ncd.gz | less

---

### Post by wmichaelb on 2007-05-14
Pobega: Thanks for your suggestion; I was able to read the notes file with the Ubuntu text editor, and figured out that I can access the tree commands by right-clicking on the left panel. Simple, but I had no clue. I still don't know how to unzip the package so that I can access the help file from the help tab in the application; but I'm working my way through Keir's Ubuntu book, and so hopefully will be more competent at the basics soon.

Thanks again for your time and help!

---

