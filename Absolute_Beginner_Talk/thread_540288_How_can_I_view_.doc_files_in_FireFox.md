---
title: "How can I view .doc files in FireFox?"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by northerndude81 on 2007-09-01
Pretty much what the title says, I just want to look at an MS Word (.doc) document in FireFox.  Is there a way to do it?

(The reason I want to use FireFox is that the document I want to view is in Japanese, and I have a dictionary add-on in FireFox that will make reading the 30 or so pages much easier for me.  Also, OpenOffice doesn't format the Japanese text as well as FireFox does.)

The document is saved to my desktop.  I can look at the directory (/home/pbr/Desktop) in FireFox but when I click on the document I want it says "Open with...?" and the default is OpenOffice, then it says "Other," but when I click other it wants me to manually look through the computer to find another application to open the .doc with.  And I don't know how to find FireFox that way.  Kind of a lame explanation of the problem but hopefully someone will understand me.  Thanks.

---

### Post by Steveway on 2007-09-01
Google Docs should be able to open it.

---

### Post by northerndude81 on 2007-09-01
That's an interesting service (I'd never heard of it before) but I'd rather just look at the file directly on my machine rather than have to pass it through Google.  Is there a way?  Back in Windows I would have just done Right Click->Open With->FireFox.  Simple enough but I can't figure it out in Ubuntu.

---

### Post by northerndude81 on 2007-09-01
I mean even in Ubuntu I can get to Right Click->Open With->FireFox Web Browser, but then it asks me to "Choose Helper Application" and I don't know how to find FireFox under that menu.  Help??

---

### Post by kerry_s on 2007-09-01
**sudo apt-get install mozplugger abiword**

---

### Post by Hendrixski on 2007-09-01
> **Steveway said:**
> Google Docs should be able to open it.

Google docs is probably the best way.  Go to docs.google.com and log in with your google account (or get a new one) then upload the .doc and view it there.

You can also save the .doc as HTML :-)  Firefox can view .html files.

You shouldn't use MS Office... here's why [http://ubuntuforums.org/showthread.php?t=540016](http://ubuntuforums.org/showthread.php?t=540016)

---

### Post by Majorix on 2007-09-01
Can't you just download the file and view it with OOo? Or is there a problem holding you back from doing so?
EDIT: Sorry I missed the Japanese part :)

---

### Post by Steveway on 2007-09-01
> sudo apt-get install mozplugger abiword
A Plugin to use Abiword in Firefox? That is pretty cool, I love Abiword it reminds me to Word97 with the difference that Abiword is a good compatible Open-source program.

---

### Post by kerry_s on 2007-09-01
> **Majorix said:**
> Can't you just download the file and view it with OOo? Or is there a problem holding you back from doing so?
EDIT: Sorry I missed the Japanese part :)

oh oh, i missed that to.
have you tried installing the Japanese language pack for open office?
**sudo apt-get install openoffice.org-I10n-ja**

edit:
**sudo apt-get install mozplugger abiword abiword-plugins**

I added abiword-plugins, it has babelfish plugin that can translate.

---

### Post by Lord C on 2007-10-22
> **kerry_s said:**
> **sudo apt-get install mozplugger abiword**

I have done this, yet when I try to run view a .doc file in firefox, it just opens in open office word processor.

AbiWord is installed, as is mozplugger. Mozplugger works nicely with pdf files in firefox.

Any advice anyone? It would be nice to view word files in firefox.

---

### Post by sybille on 2007-11-28
This works for me:
[http://ubuntuforums.org/showthread.php?t=94384](http://ubuntuforums.org/showthread.php?t=94384)

---

### Post by mikewhatever on 2007-11-28
You can convert a .doc file to .html with [http://www.zamzar.com/](http://www.zamzar.com/)

---

