---
title: "Searching pdf's"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by resistantgnome on 2007-07-13
I tried searching text inside pdf's using search-tool. I always get no results.Is search tool that bad or do I need to add some plugin to enhance it's capability?

---

### Post by kevinlyfellow on 2007-07-13
I don't seem to have an issue with it.  Of course you will need to have pdf that specifies text and not one that's just a picture of text (you can check by trying to highlight the text, if you can it should be searchable).  Are you using evince?  Can you provide on example pdf?

---

### Post by resistantgnome on 2007-07-13
I made few pdf's using openoffice. It by default gets open in evince. But somehow I can't search through them using search-tool.

---

### Post by kevinlyfellow on 2007-07-13
I just tried what you did, and it worked fine.  I'm wondering if this is a problem with OpenOffice or with Evince.  Can you search through other pdfs using evince?  If you can't find a pdf when you need it, here is a whole list of them (and I tested it through evince and it seemed to work [http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/pdf/](http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/pdf/)

---

### Post by James.Dedon on 2007-07-13
Google desktop searches through the text of PDFs created by open office.

---

### Post by stchman on 2007-07-13
> **resistantgnome said:**
> I tried searching text inside pdf's using search-tool. I always get no results.Is search tool that bad or do I need to add some plugin to enhance it's capability?

Install Adobe Acrobat.  It has far more functionality than Evince:

[http://www.stchman.com/install_adobe.html](http://www.stchman.com/install_adobe.html)

This applies to Feisty.  If you have Edgy then type:

sudo apt-get -y install acroread

from a terminal.

---

### Post by resistantgnome on 2007-07-16
I am not searching through EVINCE. I am searching through simple search-tool of ubuntu. It can search doc files with textual search but can not search pdf using textual search.
Is there any software in ubuntu like google desktop on windows?

---

### Post by mikewhatever on 2007-07-16
In my experience, nautilus search tool could not find neither files in folders, nor text in files. You can search inside pdfs by opening the file and hitting Ctrl+f. If you'd like to use Google desktop, it is available for linux.

---

### Post by resistantgnome on 2007-07-16
thanks...google desktop works sweet.

---

