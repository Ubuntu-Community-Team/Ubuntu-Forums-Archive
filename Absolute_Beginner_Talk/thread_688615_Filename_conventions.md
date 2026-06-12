---
title: "Filename conventions"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by Baasha on 2008-02-05
This will sound like a very dumb question, but I have searched all over the place for a list of Ubuntu and/or Linux filename rules.  The kind of thing I am looking for is what characters are allowed or  disallowed, etc.

Can anyone point me in the right direction?

---

### Post by Cypher on 2008-02-05
By experimentation you'll find that many of the keyboard characters can be used in filenames, it is usually desirable to replace spaces in filenames with underscore, otherwise you'll have to quote the filename to manipulate it.

There is no need to for an extension and the filename can be fairly large..

Beyond that..The [LSB]("http://www.linux-foundation.org/en/Specifications") is the Linux body that mandates many things about Linux. Poke around there to see if you can get a definitive answer.

---

### Post by stevescripts on 2008-02-05
> **Baasha said:**
> This will sound like a very dumb question, but I have searched all over the place for a list of Ubuntu and/or Linux filename rules.  The kind of thing I am looking for is what characters are allowed or  disallowed, etc.

Can anyone point me in the right direction?

Try this: [http://www.linfo.org/file_name.html](http://www.linfo.org/file_name.html)

In general, it is a good practice to avoid spaces in filenames/pathnames (unlike standard practices on windows systesms ...)

Hope this helps.

Steve

---

### Post by stoodleysnow on 2008-02-05
If you want to play it safe, keep it simple with lower case and numb3r5
:)

---

### Post by monte48lowes on 2008-02-05
"#" will not work in a filename. Since this is used to comment out lines...

Mike

---

### Post by jken146 on 2008-02-05
Most characters are allowed, and there are some things to bear in mind:

[LIST]
[*]Linux file names are case-sensitive.
[*]. at the start of a file name denotes a hidden file
[*]/ is used to differentiate between directory levels, so don't use / in your file names.
[*]\ is used to escape certain characters, like a space.
[*]Avoid spaces if you are going to do a lot of terminal based manipulation of files, as otherwise you will have to put them in quotes and/or use backslashes
[*]There are no MS-DOS style file extensions; a file name can end with anything you like and still be of the desired type.  Use the **file** command to find out what sort of file something is.
[*]Don't use a * as this is the wildcard symbol.
[*]In each directory there are 2 files by default.  They are called **.** and **..** and represent the present working directory and its parent directory respectively.
[*](not a rule) Tab completion is wonderful.
[/LIST]

There may be some more things you should know, but if there are I can't think of them.

---

### Post by Baasha on 2008-02-05
Thanks all,

I knew the info was hiding somewhere, but I just couldn't find it.

---

### Post by Cypher on 2008-02-05
Additionally, if you DO happen to use some of the reserved characters, Bash will most likely expand those characters and the result might be quite alarming. ;)

---

