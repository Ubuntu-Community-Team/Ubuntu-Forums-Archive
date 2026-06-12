---
title: "convert html to pdf"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by sundol on 2007-07-13
How to convert a web page to a pdf file while keeping links alive?

I tried pdf printer but it kills all links.

Thank you in advance.:KS

---

### Post by lisati on 2007-07-13
I haven't tried it with a document with embedded links, but Open Office Wordprocessor has an "export to PDF" option.

---

### Post by kevinlyfellow on 2007-07-13
you can use the (command line) program html2ps to convert it to postscript, and then, ps2pdf to convert it to html.

```
html2ps something.html something.ps
ps2pdf something.ps something.pdf
```

Of course you will need to install html2ps and maybe ps2pdf (I think it's default), but they are in the repositories
```
sudo apt-get install html2ps
```

---

### Post by jordanmthomas on 2007-07-13
won't that lose the hyperlinks as well?

---

### Post by kevinlyfellow on 2007-07-13
> **jordanmthomas said:**
> won't that lose the hyperlinks as well?

Yes, I believe it would.

---

### Post by jordanmthomas on 2007-07-13
Well, to be honest I just use any kde program when I need to print to pdf.  (lazy man in me I suppose)
I did find a program called htmldoc that will do it and preserve hyperlinks, but it looks to be a pain to use (unless you use the command line version).  Maybe you could look into it.

---

### Post by fchivu on 2007-09-03
You can try the [html to pdf converter for .net ]("http://www.dotnet-reporting.com") from [http://www.dotnet-reporting.com](http://www.dotnet-reporting.com) or from [http://www.winnovative-software.com](http://www.winnovative-software.com). It has a lot of features. It should preserve the links too.

---

### Post by jordanmthomas on 2007-09-03
Does that run with mono or does it have to have .net?

...or are you just suggesting he use the online demo?

---

