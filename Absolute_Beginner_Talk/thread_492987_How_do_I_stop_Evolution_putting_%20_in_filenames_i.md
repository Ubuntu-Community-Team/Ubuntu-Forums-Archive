---
title: "How do I stop Evolution putting %20 in filenames instead of a space?"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by Alex Spencer on 2007-07-05
How do I stop Evolution putting %20 in filenames instead of a space?
Thanks,
Alex.

---

### Post by Cypher on 2007-07-05
Linux doesn't like spaces in filenames much. You're better of avoiding it if you can. Are you trying to save attachments or something??

---

### Post by Alex Spencer on 2007-07-05
Hey cypher,

Yeah that's what I'm trying to do, save an attachment. I just don't like the look of it, what are the problems with spaces...I though 7 bit filenames were long gone?

Alex

---

### Post by Cypher on 2007-07-05
Linux doesn't put a limit on the filename size but just doesn't like spaces. If you find a file with spaces, you will have to access it by putting the filename is all quotes or doing things like "My\ Document\ Name\ With\ Spaces" and so on..

It is preferred to use _ (underscores) instead of spaces.

---

### Post by Wim Sturkenboom on 2007-07-05
I prefer to use underscores as well, but it's not true that linux does not like it. It's better to state that the results will be (e.g.) 'unexpected' when using filenames with spaces.

By the way, Windows has the same problems (no familiarity with other OSes).

PS I've just send myself an email with an attachment using evolution and it preserved the space when I received and saved it.

---

### Post by bulldog060 on 2007-07-05
1) Underscores are better, they are clean and do not have to be escaped :)
2) Linux/Unix (Good OSes) do have problems with spaces no matter how PC you want to refer to it because they will try to evaluate every arg passed to it so spaces will have to be escaped.
3) Windows doesn't care about spaces ( at least for the past decade or so )
4) Have you tried just clicking on the attachment and going to `Save As...'? or are some of these attachments coming from web links? %20 is a URL encoded space so most times when you see them it is related to something web based.

---

### Post by use a name on 2007-07-05
You can use "" around the filename in quite some cases. I don't know about Evolution though.

EDIT: sorry, was already said...

---

### Post by Wim Sturkenboom on 2007-07-05
> **bulldog060 said:**
> 3) Windows doesn't care about spaces ( at least for the past decade or so )
Oh :-? Please explain to me why I have to specify *path_to_executable **"%1"*** when setting an association for e.g. textfiles if I want to be able to open them in my favorite editor using a double click on the file?

---

