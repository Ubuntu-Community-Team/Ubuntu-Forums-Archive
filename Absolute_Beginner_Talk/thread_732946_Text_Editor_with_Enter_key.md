---
title: "Text Editor with Enter key"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by luckymancvp on 2008-03-23
I have just type a document in Ubuntu use Text Edittor.But When I open it in Windowns, all of in is showed in a line. I sure that I tyoe Enter key.

---

### Post by Dr Small on 2008-03-23
It does the same thing to me...
On windows, open the text document it Wordpad. Notepad seems to mess up the breaks.

Dr Small

---

### Post by ghost_ryder35 on 2008-03-23
> **Dr Small said:**
> It does the same thing to me...
On windows, open the text document it Wordpad. Notepad seems to mess up the breaks.

Dr Small
If I only knew this before, I have been manually going in and re entering the "enters" LOL

---

### Post by ByteJuggler on 2008-03-23
Ubuntu uses Unix style text files, where new lines are indicated witha single CarriageReturn character.  Windows uses, well, Windows style text files which uses both a CarriageReturn and LineFeed character.  

Personally, I would suggest you just get a better text editor on Windows, that can cope with both styles of text files, I very much like ["Notepad2"]("http://www.flos-freeware.ch/notepad2.html") for simple tasks.  (Ubuntu's text editor will also cope with both styles of files, but will save using Unix format obviously.)

---

### Post by scorp123 on 2008-03-23
> **luckymancvp said:**
> I have just type a document in Ubuntu use Text Edittor.But When I open it in Windowns, all of in is showed in a line. I sure that I tyoe Enter key. UNIX-style operating systems such as Linux use a different "line ending marker" than Microsoft OS'es.

What you need is either a better editor program on Windows that understands UNIX-style "line ending markers" or you'd have to convert your text file from UNIX/Linux format into DOS-format before you can use it on Windows.

There is a package that does exactly this:  **tofrodos**  .... So to install it you'd type this into a terminal: ```
sudo apt-get update
sudo apt-get install tofrodos
```

There are two programs in the package that you can use:
[LIST]
[*]unix2dos
[*]dos2unix
[/LIST]

So to convert a file e.g. from UNIX format to Microsoft/DOS format you'd use:
```
unix2dos mytextfile.txt
``` .. that's it. The file is converted and should now be displayed correctly on Microsoft operating systems.

A few tests (please note the difference before and after converting the file):
```
 > unix2dos test.txt 
 > file test.txt 
test.txt: ASCII English text, with CRLF line terminators
 > dos2unix test.txt 
 > file test.txt 
test.txt: ASCII English text
```

---

