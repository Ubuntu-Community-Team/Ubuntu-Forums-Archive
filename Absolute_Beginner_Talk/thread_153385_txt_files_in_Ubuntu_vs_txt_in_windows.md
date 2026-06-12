---
title: "txt files in Ubuntu vs txt in windows"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by halitech on 2006-03-31
Ok, I guess from the thread title, most have probably guessed what I'm wondering. I have Ubuntu 5.1 installed on this box and my girlfriend has windows 2000. I have some things that we work on together that I use texteditor to save info in and it works great for me. My concern is that when I send the file to her,saved as a .txt when she opens it, where the breaks should be, she has a bunch of box shaped "things" and everything runs together. Is there a way around this or should I use another program instead of texteditor?

thanks

---

### Post by rfruth on 2006-03-31
a 7 bit text file has no breaks in it, rich text does though ... both of you could use Open Office to create and send .DOC files or use ajaxwrite [http://www.ajaxwrite.com/]("http://www.ajaxwrite.com/") (no IE support in ajaxwrite yet though) :)

---

### Post by trent dillman on 2006-03-31
Try using either

a) metapad for Windows

or 

b) after saving on linux, make a DOS friendly copy to transfer:

```

cat youroldfile.txt | sed 's/$/\r/' > yournewfile.txt

```

EDIT: forgot the pipe :-)

---

### Post by halitech on 2006-03-31
thanks, was thinking about using OO to create the files. It's usually more one way with me creating them and sending them to her so as long as she can open it in wordpad or word then thats what matters. 

ajaxwrite looks interesting, I've bookmarked it for later investigation :)


edit: well dang, not hard to tell this forum has nothing to do with M$, friendly help within minutes of posting a question and no smart alec responses either, loving this place more and more every day :)

(and no, NOT in THAT way so no worries ~LOL~)

---

