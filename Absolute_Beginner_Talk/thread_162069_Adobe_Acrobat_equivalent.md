---
title: "Adobe Acrobat equivalent"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by nsmith on 2006-04-18
I recently downloaded a bunch of Adobe Acrobat forms.  The forms have interactive fields but I cannot fill in the fields on my ubuntu system.  Do I need another program to do this? If so, what program and how do I install it?

---

### Post by 5-HT on 2006-04-18
I've read that kword can edit pdfs.

If you want to go the fun way :D: import the document into the GIMP and insert the text you want .
To get back to .pdf, I tend to import the .jpg the GIMP creates into oppenoffice and export to .pdf from there (it's cumbersome, but it works).

---

### Post by unbuntu on 2006-04-18
[QUOTE=nsmith]I recently downloaded a bunch of Adobe Acrobat forms.  The forms have interactive fields but I cannot fill in the fields on my ubuntu system.  Do I need another program to do this? If so, what program and how do I install it?[/QUOTE]

Acrobat reader has a Linux version.  You can find and download it from their site [www.acrobat.com](www.acrobat.com)

I don't know about form-filling on non-Acrobat PDF readers.  Evince is the default for ubuntu.  xpdf is also an alternative, but again, not sure about form-filling.  Best bet might be using Acrobat reader for Linux.

---

### Post by 5-HT on 2006-04-18
[quote=unbuntu]Acrobat reader has a Linux version.  You can find and download it from their site [www.acrobat.com]("http://www.acrobat.com")

I don't know about form-filling on non-Acrobat PDF readers.  Evince is the default for ubuntu.  xpdf is also an alternative, but again, not sure about form-filling.  Best bet might be using Acrobat reader for Linux.[/quote] 
I don't think Acroread for Linux can edit pdfs (would love to know how to get it to work if it does though!).

---

### Post by fmo on 2006-04-18
[QUOTE=5-HT]I don't think Acroread for Linux can edit pdfs (would love to know how to get it to work if it does though!).[/QUOTE]

It's not considered as editing, it's just one of the features of the reader, you can fill forms but you can't modify the form.

---

### Post by nsmith on 2006-04-18
> I don't know about form-filling on non-Acrobat PDF readers. Evince is the default for ubuntu. xpdf is also an alternative, but again, not sure about form-filling. Best bet might be using Acrobat reader for Linux.


I dont want to sound stupid but I do not see xpdf or Evince.  My PDF documents current open with document viewer.  Is this xpdf or Evince?

---

### Post by 5-HT on 2006-04-18
[quote=fmo]It's not considered as editing, it's just one of the features of the reader, you can fill forms but you can't modify the form.[/quote]

Thanks for the input. 
Guess the forms I've needed to fill out weren't originally created properly for filling out. :(

---

### Post by unbuntu on 2006-04-18
[QUOTE=nsmith]I dont want to sound stupid but I do not see xpdf or Evince.  My PDF documents current open with document viewer.  Is this xpdf or Evince?[/QUOTE]

What DE are you using?  Don't know about KDE, but on GNOME, double-clicking a PDF will launch evince, as it's the default pdf viewer.  If you're not sure, you can always check Help->About, to see which app you're using.

---

### Post by 5-HT on 2006-04-18
[quote=nsmith]I dont want to sound stupid but I do not see xpdf or Evince.  My PDF documents current open with document viewer.  Is this xpdf or Evince?[/quote] 
Should be Evince.

*EDIT: too late

---

### Post by niviche on 2006-04-18
[QUOTE=unbuntu]Acrobat reader has a Linux version.  You can find and download it from their site [www.acrobat.com](www.acrobat.com)[/QUOTE]

I might be wrong, but I believe that Acrobat Reader is in the repositories. Don't ask me which one, though. :)

Also, the best OS PDF viewer I have seen so far is Kghostview. It's faster and better than Kpdf or Xpdf, IMHO.

---

### Post by nsmith on 2006-04-21
> I might be wrong, but I believe that Acrobat Reader is in the repositories. Don't ask me which one, though.

Acrobat Reader can be found in the multiverse repositories.  I downloaded and installed it but I still cannot fill out forms.  This is bizarre to me because the windows version allows me to fill out forms.

I am still looking for a pdf viewer for ubuntu that allows this.

---

### Post by Kimm on 2006-04-21
I'm sure Acrobat Reader for Windows will work in wine if you try that, but I havnt tested it.

---

### Post by jeremy on 2006-04-21
I use acroread (linux version) to fill in (as opposed to edit) and print my tax forms, it works perfectly. Xpdf and Kpdf do not work.

---

### Post by nsmith on 2006-04-21
> I use acroread (linux version) to fill in (as opposed to edit) and print my tax forms, it works perfectly. Xpdf and Kpdf do not work.

I a have downloaded acroread (linux version) but I still can not fill in forms.  Is there a trick I do not know about?

---

### Post by nick58b on 2006-04-27
Make sure you also get "acroread-plugins" along with "acroread" from synaptic. I wasn't able to fill in forms until I installed that extra package. Now if only I could save a filled-in form and still be able to edit it later on...

---

### Post by gingermark on 2006-04-27
Check out flpsed - one for the future maybe (it's alpha software) but looks very promising at any rate. Allows you to "write on" pdfs, so great for filling out forms. As I say, it's still in the early stages though.

---

