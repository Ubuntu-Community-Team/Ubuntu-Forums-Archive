---
title: "Wine installation issue"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by Chaositect on 2008-03-21
I've copied and pasted the given CLI commands from the Wine HQ site, and although the install line appears for Wine on the Add/Remove application, I've checked the boxes next to the third party software lines that appeard, and I am still unable to check the box.  I click, and no check....   Please help to stir my newbsauce!

Doesn't seem to match any of the existing issue threads...  Thanks!

---

### Post by Tatty on 2008-03-21
Which CLI lines did you run?  There are several different ways of installing wine, depending on what version you want...

Can you post a link to the instructions you followed?

---

### Post by Chaositect on 2008-03-21
I followed instructions at [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) 
(not sure how to make that a link Re: Newbsauce in sig)

The command lines given for Gutsy (7.10) were as follows:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

then 

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list

Was that first line supposed to be broken by the | ?  Don't know much about it, but it seems the "sudo" usually goes at the beginning...

---

### Post by Tatty on 2008-03-21
Well if you want simplicity, wine is included in the default ubuntu repositories...

```
sudo apt-get install wine
```

Although i assume the ones in the repository you are trying to add will be kept slightly more up to date.

Are there any error messages given when you execure the code from the website?  Sorry i dont quite follow what is going wrong.

---

### Post by Chaositect on 2008-03-21
No errors at all...  The Wine item shows up in the add / remove programs list just as it should, but I am unable to place a checkmark in the box provided...  It just won't register.  I used the text you provided, and it appears to be installing, so I appreciate the help...  Just not sure what I am missing with the deb install...  Thanks!

---

