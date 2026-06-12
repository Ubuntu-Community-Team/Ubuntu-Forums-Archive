---
title: "Problem Running Photoshop 7"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by ragadanga63 on 2006-11-30
Installed Photoshop 7 with wine successfully.  However, when i tried running it, an error message was displayed:

fixme:actctx:QueryActCtxW 80000010 0x116283c (nil) 1 0x33fdc4 8 (nil)
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  145 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  31
  Current serial number in output stream:  31


Can anyone help please?  Thanks.  I'm a noob aching to say bye bye to Window$.

---

### Post by alican timur on 2006-11-30
you may want to try using GIMP.
[http://www.gimp.org/]("http://www.gimp.org/")

---

### Post by ragadanga63 on 2006-11-30
thanks alican timur.  I already have GIMP installed but it just can't do the things that i MUST do with Photoshop.  that's why i have to run the gauntlet of running it with wine on Ubuntu.

---

### Post by Kittie Rose on 2006-12-01
I have the same error with Paint Shop Pro 7 and Pixia. I doubt you'll get it fixed unfortunately.

And yes, GIMP is nowhere near the same. The interface is very cluttered and awkward. 

The best way to make Linux more popular is for WINE to have better support.

---

### Post by alican timur on 2006-12-03
> **Kittie Rose said:**
> I have the same error with Paint Shop Pro 7 and Pixia. I doubt you'll get it fixed unfortunately.

And yes, GIMP is nowhere near the same. The interface is very cluttered and awkward. 

The best way to make Linux more popular is for WINE to have better support.
or make better software for linux.

---

### Post by Shay Stephens on 2006-12-03
Gimp is making progress, and I look forward to version 2.4 which may give us some 16 bit editing (yay).  But as mentioned also, it is no substitute for some things such as batch automation, correction layers (non-destructive editing), etc.

I have Photoshop 7 running very successfully with crossover office, I have yet to get it to run reliably enough in wine.  If you must have PS7 running now, then crossover office is the answer.  Pony up the cash, you will not only get the functionality you need from PS7, you will also be supporting wine development.  A win/win :-)

Some projects to try out and keep an eye on:
Krita
Pixel image editor
cinepaint (glasgow)
gimp 2.4 or greater

Also, if you are wanting to do any raw processing, bibble is tops.  Paired with Photoshop 7, you have a complete solution.  ufraw is making some good progress, and by the time gimp 2.4 comes out, there might be a viable solution there.

---

### Post by sardion on 2006-12-03
what versions of wine and xorg are you using?

is this dapper or edgy?

i have photoshop 7 working fine thru wine.

do you have other things installed on top of wine?

try creating a fresh .wine folder if you can and see if that helps

---

### Post by sardion on 2006-12-03
oh, and to the rest of the people on this thread (i.e. not the asker)... the gimp is *not* a replacement for photoshop.  i wish the linux crowd would accept that.

---

### Post by Shay Stephens on 2006-12-03
> **sardion said:**
> ... the gimp is *not* a replacement for photoshop.  i wish the linux crowd would accept that.

It's not a replacement yet...but I don't think anyone should just accept that ;) 

And if you follow the development of gimp, it is making inroads to the areas of weakness that keep it from replacing photoshop.  With more and more people who join the linux ranks that are also advanced users of photoshop, they put pressure on the direction gimp and other projects take in future development.  That development takes time, but we are starting to see action.

But yes, I agree, the knee jerk recommendation of gimp as the cure all solution for photoshop is really misguided, but it comes from a lack of experience, not anything malicious.  I try to illustrate that by giving a few examples of functionality that photoshop has that gimp does not.  That helps people see that it's not just an interface thing, or a lack of experience in knowing where features are, etc. it is a real functionality argument being made.

Once people "get it" then their eyes are opened.  Get enough people to that point, and maybe the acceleration of development can increase :-)

---

