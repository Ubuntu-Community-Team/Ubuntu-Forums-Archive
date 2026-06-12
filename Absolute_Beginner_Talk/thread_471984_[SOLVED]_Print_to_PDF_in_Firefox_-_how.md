---
title: "[SOLVED] Print to PDF in Firefox - how?"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by qprfact on 2007-06-12
In Windows, I can use Distiller or Cute PDF to create PDFs of web pages.

On my printing options in Ubuntu, there is a print to file, but that produces an output that I can't open in Windows - how do I go about achieving this?

Thanks!

---

### Post by starcraft.man on 2007-06-12
[cups-pdf]("http://ubuntuforums.org/showthread.php?t=393596&highlight=cups-pdf")

Follow the second post's instructions, it works.

---

### Post by happysmileman on 2007-06-12
I think Firefox 3 should have that feature built in, but that's just IIRC

---

### Post by qprfact on 2007-06-12
That seems to have done it! As others have said, it prints to Home/PDF

Thanks!

---

### Post by kevdog on 2007-06-12
Just another recommendation -- KPrinter.  It provides a gui similar to windows so the interface is very familiar.  Its KDE, but if your using ubuntu with gnome, I think you can still install it.

---

### Post by mutley69 on 2008-06-17
kprinter --stdin WAS the better option - until the builders of firefox took the "unhappy" descision of letting it out of firefox3.

The cups-pdf produces some pdf output - but sometimes it's only the first page. The pdf output of kprinter is a lot more stable.

So i just hope that this NASTY bug gets out of firefox - or i'll have to switch to something else - opera?

Yep Opera has a nice printer program dialog - and that dialog does whatever i want.

It's sad that firefox-devels took such an approach. It's just a feature that i can't live without! 

I'd rather like them to support KDE better ... (i won't say what i think about gnome - there's enough war in the world!) :(

---

### Post by cobradevil on 2008-07-08
well not entireley true about firefox 3 leaving it out!!

Gtk has different backends for printing and one of them is lpr.

Now since the hardy heron release the default gtk has enabled file and cups as the backends.

you can change this by editing gtkrc:
```

sudo vi /etc/gtk-2.0/gtkrc

```
And add the following line
```
gtk-print-backends=file,lpr,cups 
```

i use this for a pdf script i created which replaced the printer!

---

