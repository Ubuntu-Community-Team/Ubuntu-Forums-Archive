---
title: "efax-gtk and CUPS"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by luvinit on 2006-12-04
I would like to set up direct to efax-gtk fax printing from Writer. There is a generic readme, but it isn't helpful to me, unfortunately. Does anybody with some expertise know how to decipher this into a straightforward guide for an Ubuntu newcomer? 

The efax-gtk readme is here

[http://efax-gtk.sourceforge.net/README](http://efax-gtk.sourceforge.net/README)

checkout "using with a word processor" about half way down. I would appreciate  some help and am sure it would make a good FAQ for the Ubuntu forum.

Ok, just to update, i inputted the following command 

/usr/sbin/lpadmin -p FaxPrinter -E -v socket://localhost:9900

from the root and it all just worked perfectly, so I guess I don't need any help. However, I don't have a clue what it means when it says "bringing up the fax administration page for CUPS in a web browser" in the readme before it gets to the  above command, which is what set my brain into overload, because it is very small. :-) So, anyone trying to do this, just go straight to the command line type the above and ignore the other stuff to save confusion.

---

### Post by lhtown on 2006-12-08
Thanks,

You just saved me an hour or so of work. It worked for me too!

As a side note, does anyone know how to print to postscript or some format that efax can read so that I can save a file and then fax the file?

---

### Post by luvinit on 2006-12-09
If you select "print" in open office writer there is an option to print to file, which will save as a postscript .ps file. In Abiword, if you choose print, there is an option for "generic postscript". I think there is a similar option in many applications.

---

### Post by lhtown on 2006-12-09
I couldn't find the option to print to file until I installed the package pstoedit. 

Now the print to file option shows up fine in OpenOffice. I don't use Abiword, so I haven't tried it.


Thanks for your help, luvinit.

---

