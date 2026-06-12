---
title: "Word count of a pdf document"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by 1002285 on 2007-10-03
Is there an application that can give me a word count of a pdf document?
I do have Windows, too, but I can't seem to find a way to get the word count for free in Windows either.

---

### Post by Terl on 2007-10-03
Check this:  [wc command]("http://www.oreillynet.com/linux/cmd/cmd.csp?path=w/wc")

---

### Post by jordanmthomas on 2007-10-03
How would you use wc to get the count of words in a pdf since there's a bunch of binary junk in it?

---

### Post by Terl on 2007-10-03
> **jordanmthomas said:**
> How would you use wc to get the count of words in a pdf since there's a bunch of binary junk in it?


Good call, sorry.

I did find this (windows though):  [http://www.globalrendering.com/download.html]("http://www.globalrendering.com/download.html")  It is free

---

### Post by jordanmthomas on 2007-10-03
Good find.  

I just tested it and it works in Wine.

---

### Post by laur on 2007-10-03
Hey
You can also do it in a easy way without any installation of software. Just type:
pdftotext YOUR_PDF.pdf YOUR_PDF.txt
wc YOUR_PDF.txt -w
in the terminal.
Isn't that easy?

/Laur

---

### Post by jordanmthomas on 2007-10-03
That is much easier, actually, and gives the same number the program suggested above did on my test file.

---

### Post by mali2297 on 2007-10-03
You can shorten it to one line:
```

pdftotext YOUR_PDF.pdf - | wc -w

```

---

### Post by 1002285 on 2007-10-04
> **laur said:**
> Hey
You can also do it in a easy way without any installation of software. Just type:
pdftotext YOUR_PDF.pdf YOUR_PDF.txt
wc YOUR_PDF.txt -w
in the terminal.
Isn't that easy?

/Laur


This gave me 25665, but I actually needed character count - this could have been the number of words.
I tried the same thing without -w and got
970 25665 211776. Is the last number character count? Does it count spaces? Do you think this way is entirely reliable?

I guess I will also have to try the Windows app that was suggested here, bevause that actually seems to be made for the exact thing I need - to give a translator the character count.

---

### Post by 1002285 on 2007-10-04
> **mali2297 said:**
> You can shorten it to one line:
```

pdftotext YOUR_PDF.pdf - | wc -w

```
Strangely, this gave me 0.

---

### Post by 1002285 on 2007-10-04
> **Terl said:**
> Good call, sorry.

I did find this (windows though):  [http://www.globalrendering.com/download.html]("http://www.globalrendering.com/download.html")  It is free

The answer given by this application was 26811, while wc MY PDF-txt said 25665.
AnyCount did not work. So I guess it is not easy to do.

What I need is a character count and I need to know the result including spaces, and I need to do it with a file that has a lot of pictures and tables. So the best way seems to be to ask for the source file. I just wanted to find out whether this can be done with pdf-s reliably, but so far I am not convinced.

Thanks to everybody, though.

---

