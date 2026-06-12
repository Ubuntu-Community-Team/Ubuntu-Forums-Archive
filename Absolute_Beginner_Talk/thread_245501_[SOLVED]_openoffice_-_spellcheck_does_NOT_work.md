---
title: "[SOLVED] openoffice - spellcheck does NOT work"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by altonbr on 2006-08-27
Hey guys, ever since I upgraded to 6.06, I've been having a multitude of problems. If you do a search by author and use my name, you'll see what I mean.

Recently I was writing a quick 'to-do' list in OpenOffice Writer when I noticed it wasn't picking up my spelling errors.

I checked Synaptic Package Manager and everything appeared to be in order.. I check Tools > Options > Language Settings in OOo and everything was fine there as well, saying I had American and British English (no Canadian though :( ) installed, just as Synaptic stated. Has anyone ran into this yet? I have a big feeling I've been constantly doing something wrong, but my other sense of how well I know Linux and operating systems in general says it's not me.

I've included a screenshot.

Any help or even anicdotal evidence is much appreciated :)

**BTW:** Look at the background to see all my spelling mistakes... there is no red, jagged line crossing through, and the spellcheck dialog says nothing can be found.

---

### Post by aysiu on 2006-08-27
Does [this thread](http://kubuntuforums.net/forums/index.php?topic=8272.msg33249#msg33249) help to shed any light on the issue? Or is it something else?

---

### Post by altonbr on 2006-08-27
Apparently, all that was needed was to reboot... I thought that was a Windows trick?

---

### Post by aysiu on 2006-08-27
> **altonbr said:**
> Apparently, all that was needed was to reboot... I thought that was a Windows trick?
That's weird...

---

### Post by altonbr on 2006-08-30
Just as an update, it's doing it to me again. I'll restart and then do spell check when I'm done, but talk about an annoyance.

---

### Post by Blur-king on 2006-08-31
Hi did you follow asiu thread. for spellcheck to work you have to enable the dictionary. You need to do this by going to --File---> Wizards----> install new dictionaries in openoffice.

---

### Post by altonbr on 2006-08-31
Yeah, the thing is, it works SOMETIMES.. and other times it's non-existant.. I'll run DicOOo-1.6.1 and update my dictionaries to see if that helps. Thanks.

---

### Post by Blur-king on 2006-09-01
Ok noted, I notice that for the spellcheck thesaurus to work I have to set my default language for my document to English (UK). In OO under tools--->options ---->language settings----> language---->Default  language  for document.----- make sure you set  it to  your language ie do not leave it at None. hope this works for you.

---

### Post by altonbr on 2006-09-02
Yup, thanks aysiu and Blur-king, resetting the defaults to a specific dictiobnary helps... along with going through the dictionary update wizard

```
File > New Wizards > Install new dictionaries...
```

---

### Post by OakRand on 2006-09-09
I was having the same problem. Only some variations of the English dictionary can be configured with spellcheck: the UK and USA versions. The default language has to be specified as one of these. If you have old documents where the default was Canada or elsewhere, the spellcheck will not kick in unless you change the language when that document is open. To do so, select all, go to Format and select Character, then under the Font tab change the language. You should see the ABCcheckmark next to the UK and USA languages.

Provided the default is set properly, then any new documents will been spellcheckable, but with every old document I think you have to change the language by hand. A bit of a pain.

---

