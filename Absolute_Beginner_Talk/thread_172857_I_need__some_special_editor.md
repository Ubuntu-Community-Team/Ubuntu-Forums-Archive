---
title: "I need  some special editor"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by Isoss on 2006-05-09
I am looking for an editor that enables me to delete or modify a certain word, letter, or sentance from all over a text! for example, I need to to change every "Very Important Person" into this word "VIP" ... so if the text contains 10 sentences of "Very Important Person", I need to change that using one option at once! so I don't have to search for them all and take time changing.

Is there such an editor in linux?

Hope somebody knows.

---

### Post by Jagot on 2006-05-09
Yeah, it's search-and-replace.  I believe Kate can do it.

---

### Post by Ferri on 2006-05-09
OpenOffice writer does it without problems (use ctrl+f).

---

### Post by mostwanted on 2006-05-09
Gedit, Kate, OpenOffice, etc.

_Any_ editor will do that!

---

### Post by Kvark on 2006-05-09
In Gedit which is Ubuntu's default text editor:
1. Press Ctrl+R.
2. Fill in the "search for" and "replace with".
3. Click the "replace all" button.

PS. "Is there such an editor in linux?" No matter what kind of text editor you need I bet there is such an editor for Linux. A lot of geeks who write program code all day and thus need all kinds of advanced or even weird text editor functions use Linux, and they know how to program editors with all the special functions they want. Take a look at emacs for example, it's not just a text editor anymore it's almost an OS of it's own.

---

### Post by xtacocorex on 2006-05-09
You could always command line it up and use sed...
I still have trouble sometimes using it [sed] because it seems so foreign. 

I know that Kate will do it since I use it frequently.

---

### Post by ComplexNumber on 2006-05-09
if anything, i think it would more difficult to come up with a list of editors that *don't* do search and replace.

---

### Post by harisund on 2006-05-09
yeah it would be very hard to come up with an editor that can't do that, even on Windows. 

The best of course, if the text file is ASCII formatted
```
sed -i -e 's/Very Important Person/VIP/g' name_of_file
```

---

### Post by Isoss on 2006-05-09
Thanks guys. I just found it in some editor right after I posted ... Thanks anyway ... I should've searched more.

---

