---
title: "Converting Between Text Encodings"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by NotPhil on 2007-04-15
Does anyone know of a utility that will allow me to convert text files from one encoding to another? 

I've got a lot of plain-text files that GEdit won't open (complaining that it can't recognize the encoding) and that Cream will open, but will display incorrectly (with gray ^M characters instead of line breaks, and no scrolling in the window).

Come to think of it, can anyone tell me what the "standard" encoding for plain text is, nowadays? I know some of these files are MacRoman ASCII, some are Windows ASCII, while others are ISO text files. Is UTF the thing now?

---

### Post by NotPhil on 2007-04-16
Has no one else had this problem?

---

### Post by babis85 on 2007-08-26
Hi, somehow late though...
^M is the for displaying the character '\r' that windows puts before '\n' in order to break a line. To convert to unix format, that is lines ending with '\n', just type dos2unix filename.

As for the encoding, you have to know the encoding of the current file. For example, if it is of iso-8859-1 you can convert it to utf-8 using the command:
iconv -f iso-8859-7 -t utf-8 input_file > output_file

In case that sth goes wrong, you have specified wrong encoding for parameter -f.
The prevailing character encoding is UTF-8 and all have to adhere to that.

---

### Post by NotPhil on 2007-08-27
Thanks Babis. I'll give it a try.

---

