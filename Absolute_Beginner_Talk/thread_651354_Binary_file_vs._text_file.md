---
title: "Binary file vs. text file"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by kkjaergaard on 2007-12-27
I tried to open a binary file (any program) using gedit, but gedit was not able to open the file. gedit warned me about whether I was trying to open a binary file.

Why is that? Why can't gedit open a program (like any text editor can i Windows)? Is there any difference between text files and binary files not mentioned in [http://en.wikipedia.org/wiki/Binary_file](http://en.wikipedia.org/wiki/Binary_file) ?

---

### Post by LowSky on 2007-12-27
from that link> 
If a binary file is opened in a text editor, each group of eight bits will typically be translated as a single character, and you will see a (probably unintelligible) display of textual characters. If the file were opened in some other application, that application will have its own use for each byte: maybe the application will treat each byte as a number and output a stream of numbers between 0 and 255 — or maybe interpret the numbers in the bytes as colors and display the corresponding picture. If the file is itself treated as an executable and run, then the computer will attempt to interpret the file as a series of instructions in its machine language.

Binary isn't text so why could a text editor open it?

use a hex editor like ghex

---

### Post by Muni Beduhin on 2007-12-27
Binary files are like .exe files in Windows. You can't open .exe files in Notepad, or any other normal text editor, for that matter. Are you sure you want to edit the binary code? Do you not want to download the source, edit that, and then recompile the application?

---

### Post by kkjaergaard on 2007-12-28
> **Muni Beduhin said:**
> Binary files are like .exe files in Windows. You can't open .exe files in Notepad, or any other normal text editor, for that matter.

That is actually not true. It is possible to open a .exe file in Notepad, but the result is rather messy since the program presents the file's content as if it was actually text (and the program decodes it using some encoding).

> **Muni Beduhin said:**
> Are you sure you want to edit the binary code? Do you not want to download the source, edit that, and then recompile the application?

No, I do not want do edit the binary code, I just tried for fun - since it can be done in Windows (and I have had quite much fun doing so \\:D/), why should it then not be possible in Linux?

What I really meant is: Is there any file attribute or anything that characterizes a binary file or text file? Just file extension or MIME type? How does gedit decide not to open binary files?

Anyway, editing binary code is not that relevant in the open source environment as it is in Windows :-$

---

### Post by Taboo Mirage on 2007-12-28
Linux doesn't use extensions at all.  It is determined by the contents of the file.

I have no idea why you'd want to see a binary file in a text editor.  That'd be practically useless and unreadable.  If you're desperate though, just use less or similar:

```
less /usr/bin/apt-get
```

Have fun.

---

### Post by kkjaergaard on 2007-12-28
> **Taboo Mirage said:**
> Linux doesn't use extensions at all.  It is determined by the contents of the file.

How? Can you tell more about this or do you have a link or something?

> **Taboo Mirage said:**
> I have no idea why you'd want to see a binary file in a text editor.

Well, I don't really want to see a binary file in a text editor. I just tried and wondered why it was not possible.

---

### Post by SunnyRabbiera on 2007-12-28
well then again there is the little thing that annoys me about gnome, it seems like it wants to treat txt files like binaries.... you have to edit nautilus

---

### Post by The Cog on 2007-12-28
> **kkjaergaard said:**
> 
No, I do not want do edit the binary code, I just tried for fun - since it can be done in Windows (and I have had quite much fun doing so \\:D/), why should it then not be possible in Linux?

There are two reasons.
Firstly, gedit has registered that it opens text files, and nautilus knows its a binary file. That's why you have to explicitly say you want to open it in gedit. You can tell nautilus that gedit opens binary files, but its not the default.
Secondly, gedit looked at the file and said "I can't cope with this". That is no different to MS Word refusing to open an mp3 file. It's not Linux as such, it's an application complaining about a file format it doesn't know about.

---

### Post by nick_h on 2007-12-30
> **kkjaergaard said:**
> How? Can you tell more about this or do you have a link or something?

It uses magic numbers - [wiki link](http://en.wikipedia.org/wiki/Magic_number_(programming))

You might also find something in the manual page for the file command.
```
man file
```

---

### Post by LaRoza on 2007-12-30
To read a binary file, use a hex editor. gHex is good.

The difference is in the encoding. If you were to open a binary file in a text editor, then save it (without editing) you would corrupt it. The reasons why aren't really important, if you want to know, ask.

The hex editor will not do this, and will display it in hex (by default) good for examing binary files and archives.

---

