---
title: "Outlook to Evolution.."
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by Mazen on 2006-10-18
Is there any way to import my messages, contacts and calendar from MS Outlook to Evolution, i tried getting Contacts and Calendar in comma separated format but it's really messy!
thanks

---

### Post by meng on 2006-10-18
I hear the easiest way to do this is via Thunderbird! (MS Outlook -> Thunderbird Windows -> Thunderbird Linux -> Evolution) I have never tried this, I synced my PDA to Windows then Linux to achieve the same thing.

---

### Post by ReaderRat on 2006-10-18
Isn't there an import/export function in Outlook?

---

### Post by jimrz on 2006-10-18
> **ReaderRat said:**
> Isn't there an import/export function in Outlook?

yes but it exports to a .pst file and Evo cannot use these, but they can be imported to Tbird in windows then exported to a proper file type and subsequently imported to Evo. a bit convoluted, but it works

---

### Post by notarikon on 2006-10-19
Easy :)

Download libpst-0.5.4.tar.gz from [here]("http://www.five-ten-sg.com/libpst/packages/")

Extract
./configure
make
sudo make install

You now have a command line utility called readpst that can convert a pst to an mbox file :) It will also export a contact list as either vcards or a list of emails

Edit: One caveat, doesn't like Outlook 2003 files, sorry not so easy

Edit 2: It's in the repositories, under readpst (surprisingly). I've also just found that if you remove all NULLs from the pst first, it'll read in 2003 files (don't quote me on that).

---

### Post by Mazen on 2006-10-20
how do i remove the NULL?!!:???:

---

