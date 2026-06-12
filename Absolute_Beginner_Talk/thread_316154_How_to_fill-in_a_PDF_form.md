---
title: "How to fill-in a PDF form?"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2006-12-10
So, as you can tell from the title I have a pdf form that I would like to fill in.

I read through the forum, some mentioned Abiword, some mentioned pdftk, others mentioned kword.

I tried Abiword, but when I try to import the pdf form it just sits there saying 'importing document' and nothing else happens.

Kword imports the form fine, but messes up and removes the formatting leaving the forum useless and unusable.

I have not figured out how to use pdftk, it doesn't not appear to have a GUI and seems to be usable only through the terminal.

So dear Ubuntu users, have you ever needed to fill out a pdf form and if yes how did you do it without messing the form up?

Thanks!

---

### Post by meng on 2006-12-10
What about Adobe Acrobat Reader?

---

### Post by wombat20 on 2006-12-10
I don't think you can edit existing PDFs - you can Export an OpenOffice.org document as a PDF, but PDFs are meant to be read-only.  You are probably expected to print it out and fill it in with a pen, assuming it's some kind of application form.

I think to edit existing PDFs you need Adobe Distiller or some other Adobe tool you have to pay for.

If you really want to do it electronically, you could try the following:
1. Open the PDF for viewing, with evince for example.
2. Expand it so you can see the whole form.
3. Take a screenshot using the GIMP
4. Add your text to the screenshot
5. Save the edited screenshot as a JPG or similar.

Not ideal, but probably the best you can do.

---

### Post by PartisanEntity on 2006-12-10
Actually it is one of those PDF forms that you can fill in electronically.

It works in Windows XP using Adobe Reader, but I would like to get it to work in Dapper too.

I have come across the Gimp method you mentioned, is this the only way?

---

### Post by meng on 2006-12-10
For me, it works in Dapper using Adobe Acrobat Reader.

---

### Post by PartisanEntity on 2006-12-10
What plugins do you have installed for Adobe Reader?

---

### Post by meng on 2006-12-10
I didn't install any plugins manually, I simply went with a simple acroread and mozilla-acroread install. Looking at the several plugins that are installed with Acrobat, the one which seems most relevant is called Forms (unsurpisingly).
Quote: The Acrobat Forms plug-in allows users to work with electronic forms using Acrobat.

---

### Post by Malta paul on 2006-12-10
If its any help, you can down-load and install Acrobat reader in Ubuntu using  Automatix, Good luck :)

---

### Post by PartisanEntity on 2006-12-10
@ Malta Paul: Thanks, that is how I originally installed Acrobat Reader.

I have just installed acroread-plugins from the repository, and now I can fill-in the PDF form using Acrobat Reader!

---

