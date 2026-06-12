---
title: "installing acrobat reader"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by G. Cotgreave on 2007-11-19
Hi people!!!!
I have just downloaded the adobe acrobat reader from adobe site but how do i install it?

---

### Post by rsambuca on 2007-11-19
Hi there.  Just so you know, there is a pdf reader already pre-installed with Ubuntu (it is called evince).  If you just click on a pdf, it will open it up.  

Anyways, if you want to install the bloated adobe acrobat reader, then it is probably easier to do this:```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```then```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```then ```
sudo apt-get install acroread
```

---

### Post by G. Cotgreave on 2007-11-19
Thnx a lot i allready had the mediubuntu repository so i just had to use the last line of code you gave me :) Thnx!!!!

---

### Post by rsambuca on 2007-11-19
> **G. Cotgreave said:**
> Thnx a lot i allready had the mediubuntu repository so i just had to use the last line of code you gave me :) Thnx!!!!

No problem!  Just out of curiosity, what is it that you need in the Adobe reader that isn't in the default Ubuntu pdf reader?

---

### Post by G. Cotgreave on 2007-11-19
Just out of curiosity :)

---

### Post by aysiu on 2007-11-19
I would install *acroread-plugins* as well. *acroread*, by itself, offers very little over Evince or Kpdf. *acroread* with *acroread-plugins*, however, lets you fill in PDF forms.

---

### Post by stchman on 2007-11-19
> **rsambuca said:**
> Hi there.  Just so you know, there is a pdf reader already pre-installed with Ubuntu (it is called evince).  If you just click on a pdf, it will open it up.  

Anyways, if you want to install the bloated adobe acrobat reader, then it is probably easier to do this:```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```then```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```then ```
sudo apt-get install acroread
```

The only thing about Evince is that PDFs don't print well.  They always print well in Acrobat.  I wish Foxit would make a PDF reader for Linux.

---

### Post by jrusso2 on 2007-11-19
> **stchman said:**
> The only thing about Evince is that PDFs don't print well.  They always print well in Acrobat.  I wish Foxit would make a PDF reader for Linux.

They do but they never finished it.  Doesn't seem to work in Ubuntu though.

[http://www.foxitsoftware.com/pdf/desklinux/](http://www.foxitsoftware.com/pdf/desklinux/)

---

### Post by mangurt on 2007-11-19
Hmm...ok, how does someone get the plug-ins for acroread?

Just wondering.  I have to do a lot of stuff with adobe, and filling in .pdf files would be great!

---

### Post by philinux on 2007-11-19
Just open synaptic and click search then type in acroread.

---

### Post by jmax on 2007-11-19
I just downloaded the acrobat reader for debian 
right clicked on the package and one of the options
it gave was "open with gbi package installer". 
Did that clicked install and there it is ... acrobat
reader installed without code [thank goodness]
I'm an ex windows user from the 3.11 days.

---

### Post by pyronicte on 2007-11-22
Hi, I'm prefer using acrobat reader before evince for the following reasons:

1. Evince don't let me to change the background color to grey. I'm an electronic reader, and the blank background isn't good to my eyes for long periods.
2. Evince owes you to change page by icon but acrobat lets the use of wheel mouse to change pages.
3. The zoom options in acrobat are better than evince.

One problem I have both evince or acrobat is related to printing pdf forms. In both cases when I click in print a form filled for me, the cups tray says hold, and hold forever. No page for the printer. Anyone knows why? How to repair this?

Bye!

---

### Post by oliverjia on 2007-11-25
after added the medibuntu source, open up a terminal, type in:

sudo apt-get install acroread mozilla-acroread acroread-plugins

that's it.

---

