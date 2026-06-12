---
title: "Save Webpage as PDF?"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by Hexx on 2006-07-16
I'm looking for some software that will allow me to save webpages as PDFs. I realize that there are Firefox extensions that do this, but AFAIK they all require Java to be installed.

Are there any other methods?

---

### Post by crystal on 2006-07-16
Wouldnt it be easier to install Java then?

---

### Post by noynac on 2006-07-16
This will do what you want:

[http://ubuntuforums.org/showthread.php?t=188860](http://ubuntuforums.org/showthread.php?t=188860)

---

### Post by Hexx on 2006-07-17
Well I installed CUPS-PDF and attempted to print to file a PDF from Firefox, but when Evince opens it, it says "unhandled MIME type."

Do I need to use a different PDF viewer? Or did I do something wrong?

---

### Post by noynac on 2006-07-17
I did a reinstall of linux a while back and did not have the PDF printer installed. I just installed it as described in the thread and printed a test page and this web page to the PDF driver. Both opened and looked fine in evince. I don't know why it would make a difference, but did you set the PDF printer as the default? Perhaps you should delete the PDF printer and give it a second try. I would also try to open the actual PDF file in a different PDF reader (such as Acrobat).

---

### Post by Hexx on 2006-07-17
> **noynac said:**
> I did a reinstall of linux a while back and did not have the PDF printer installed. I just installed it as described in the thread and printed a test page and this web page to the PDF driver. Both opened and looked fine in evince. I don't know why it would make a difference, but did you set the PDF printer as the default? Perhaps you should delete the PDF printer and give it a second try. I would also try to open the actual PDF file in a different PDF reader (such as Acrobat).

Actually it seems I haven't configured it correctly after all. The instructions in that thread are specific to Ubuntu, and I'm using Xubuntu.

Does anyone know how to get CUPS-PDF working correctly under Xubuntu?

---

### Post by moshuptrail on 2006-07-29
I'm using Ubuntu (6.06) and I'm having the following problem when I try to install the cups-pdf package.  Being new and all, I'm a bit perplexed. Help?

$ sudo apt-get install cups-pdf
Reading package lists... Done
Building dependency tree... Done
Package cups-pdf is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package cups-pdf has no installation candidate

---

