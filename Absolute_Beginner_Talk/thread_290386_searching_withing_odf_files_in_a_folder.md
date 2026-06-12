---
title: "searching withing odf files in a folder"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by KhaaL on 2006-11-01
Hey all

I'm trying to organize my notes for my exam this friday, and I need to search all odf files in a folder for words starting with insats* - anyone who can tell me how i can accomplish this?

thanks

---

### Post by swamytk on 2006-11-01
odf files are not binary, so you can search with grep.

$ grep -rl insat <your-odf-files-folder>

---

### Post by KhaaL on 2006-11-01
are you sure? i just tried that command and came up with nothing...

---

### Post by steve.horsley on 2006-11-01
> **swamytk said:**
> odf files are not binary, so you can search with grep.

$ grep -rl insat <your-odf-files-folder>

On the contrary - they are gzipped collections of XML files. Because of the gzipping, grep will not be able to read them. I can't think of a good way to search them.

---

### Post by swamytk on 2006-11-01
> **steve.horsley said:**
> On the contrary - they are gzipped collections of XML files. 

fine, I agree. But ODFs need not to be zipped.. they can be in XML format.

Khaal, did you try opening the file in text editor like gedit, so that we can come to know whether it is text (XML) or zipped?

---

### Post by KhaaL on 2006-11-01
I did try to see the input with less, and the output didn't look like ASCII... all of my stored odf files are saved in the same format so I guess they're all compressed...

---

