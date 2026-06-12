---
title: "installing opera"
date: 2006-02-06
forum: Absolute Beginner Talk
---

### Post by Bubba Ho-Tep on 2006-02-06
I'm having dramas installing Opera - 

I actually had it intstalled but was trying to stick shortcuts in in my menus etc as detailed here [https://wiki.ubuntu.com/OperaBrowser](https://wiki.ubuntu.com/OperaBrowser)

wouldn't bloody work. (which is kinda funny cos it worked fine on my home machine)

Ok I thought I would be a clever bugger and add it to my sources.list as detailed in the link above.

Only thing is when I do "sudo apt-get update" I get a malformed line error on the 
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free line 

So I browsed to [http://deb.opera.com/opera/](http://deb.opera.com/opera/) 

and looked for other URLs to use, coming up with:

deb [http://deb.opera.com/opera/dists/stable/non-free/binary-i386/](http://deb.opera.com/opera/dists/stable/non-free/binary-i386/)

Which also gives malformed line error 

Also  
deb [http://deb.opera.com/opera/dists/stable/non-free/binary-i386/](http://deb.opera.com/opera/dists/stable/non-free/binary-i386/)
opera-static_8.51-20051114.1-qt_en_i386.deb

does the same


Anyone have any ideas?

BHT

---

### Post by Madpilot on 2006-02-06
Just downloading the Breezy .deb from Opera's website doesn't work for you?

The lastest Opera (8.51) runs beautifully on Breezy here. I've never bothered modifying my sources.list.

---

### Post by Perfect Storm on 2006-02-06
Try this one:

## Opera web browser
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

---

### Post by Bubba Ho-Tep on 2006-02-07
that URL worked thanks AI! It didn't link opera to my menus etc but I can live with that for now.

On a side note - the deb file has never worked for me (on computers at home and at work) I had to use the tar.gz file and untar. 

Oh well.

---

