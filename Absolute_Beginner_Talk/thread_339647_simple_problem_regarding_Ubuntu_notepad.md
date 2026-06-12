---
title: "simple problem regarding Ubuntu notepad"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by Joseph Pentecost on 2007-01-16
Pardon the simplicity of this question.  I am a newbie.  My question regarding basic text files goes like this:

When I save a 'text' file using Ubuntu's packaged notepad (I forgot what it was called) and opened it using Windows' Notepad, the text inside come out as unformatted (meaning all line breaks and spaces are removed thereby turning it into one very long line of text).

Is there a way, when I save a text file (using Ubuntu's packaged notepad) it would come out the same when opened with Windows' Notepad?  How should I do it?  If not possible, what simple 'notepad' would be good for this?

Thanks for your help!

---

### Post by ajmorris on 2007-01-16
when using gedit..... when saving change the encoding of the document to "western (windows)"

That should do the trick.

---

### Post by Joseph Pentecost on 2007-01-16
Thanks for your most prompt response ajmorris!

Unfortunately, I will also work with chinese characters and need them to be saved as such.  I also currently use the default format (UTF-8).

---

### Post by ajmorris on 2007-01-16
There are many other windows encoding options. Is it possible for you to choose one of the chinese windows ones? Or do you require UTF encoding for what you need in windows?

---

### Post by Wim Sturkenboom on 2007-01-16
Reason:
In dos/windows the end-of-line is formed by a carriage-return/linefeed. In the unix world, it's a linefeed only.


If ajmorris' solution does not eork:
1)
Quite sure that there is a unix2dos command to convert (no ubuntu at hand).
2)
Use a decent editor in Windows (I use PFE but there are others) to open text files. They allow you to convert between the two formats.

[edit]
two posts while I typed this message
[/edit]

---

### Post by Joseph Pentecost on 2007-01-16
That's a problem too.  I'm not really familiar with what format to use.  I'm still looking for a format wherein I could save in simplified Chinese as well as in English and come out right when opened in Windows' Notepad.  Currently UTF 8 is the only format I know that is capable of inputting simplied Chinese (not that I know much mind you).  I'm just throwing darts blindfolded at formats that I could use.

---

