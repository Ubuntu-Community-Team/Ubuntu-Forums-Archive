---
title: "[SOLVED] I need a thesaurus!"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by kleo skywalker on 2008-01-29
None of the existing threads on this are later than early 2006, so I'm not sure if those instructions still hold true.
I can't get the thesaurus in OpenOffice Word Processor to work - it's incredibly annoying, not mention lame and inefficient. I mean, how can a supposedly full-featured ready-to-go word processor not have the thesaurus enabled by default? (Please excuse the rant.)
I would've just used AbiWord or Google Docs but neither seems to have  a thesaurus yet.
Could someone please tell me how to get the thesaurus in Open Office working? (It's greyed out under Tools, and if I try to install the dictionaries everything freezes.)
Thanks.

---

### Post by tdrusk on 2008-01-29
Make sure you have
```
sudo apt-get install openoffice.org-thesaurus-en-us
```

EDIT: I have it working. Do what I said, then open openoffice and highlight the word. Go to tools>language>thesuarus

BUENO!

---

### Post by kleo skywalker on 2008-01-29
> **tdrusk said:**
> Make sure you have
```
sudo apt-get install openoffice.org-thesaurus-en-us
```
and
go to openoffice, help>openoffice.org help and search for thesaurus. See if anything there works for you.

That package is already installed, and I haven't found anything useful on OpenOffice.org so far.

---

### Post by tdrusk on 2008-01-29
> **kleo skywalker said:**
> That package is already installed, and I haven't found anything useful on OpenOffice.org so far.
I edited my previous post. Read it and try that.

---

### Post by kleo skywalker on 2008-01-29
> **tdrusk said:**
> open openoffice and highlight the word. Go to tools>language>thesuarus

LOL, how do you think I knew that the thesaurus was greyed out?! 
Anyway, I found something really odd - the thesaurus is working for .doc documents but not .odt ones. What is that about?

---

### Post by tdrusk on 2008-01-29
> **kleo skywalker said:**
> LOL, how do you think I knew that the thesaurus was greyed out?! 
Anyway, I found something really odd - the thesaurus is working for .doc documents but not .odt ones. What is that about?

Odd. It worked right off the start for me. 

School time. I will check back later.

btw what version of ubuntu are you running?

---

### Post by philinux on 2008-01-29
Just tried this feature by opening the word processor which gives a blank document. Typed a few words highlighted one and it works in this situation.

---

### Post by kleo skywalker on 2008-01-29
tdrusk, I'm using Gutsy.

philinux, that's what I tried first - I opened a new document and couldn't get the thesaurus working.

---

### Post by philinux on 2008-01-29
Thats odd. My set up, as far as OO is concerned, is as installed from gutsy live cd.

---

### Post by kleo skywalker on 2008-01-29
> **philinux said:**
> Thats odd. My set up, as far as OO is concerned, is as installed from gutsy live cd.

So is mine, except for a failed attempt to install dictionaries from within OpenOffice (I was following instructions from an ancient thread).
This is bizarre though, for OpenOffice to have the thesaurus working on .doc files and not .odt ones.

---

### Post by philinux on 2008-01-29
I'd be tempted to uninstall completely and remove the .config file in your home/user directory and then reinstall. 2 mins of a job.

---

### Post by tdrusk on 2008-01-29
go to synaptic and completely remove openoffice and everything associated with it. Then reinstall.

---

### Post by kleo skywalker on 2008-01-31
philinux, tdrusk - when you say reinstall OpenOffice, does that mean remove the whole OpenOffice suite or just OpenOffice Writer?

---

### Post by lswest on 2008-01-31
have you installed the dictionaries using the dictionary wizard under file-->wizards-->install new dictionaries?  Try that first, it's the only thing i've done in OO and my thesaurus works fine.  And by "ancient instructions" what exactly did you do? install the dictionary files manually?

---

### Post by kleo skywalker on 2008-01-31
> **lswest said:**
> file-->wizards-->install new dictionaries?

That's what I did, it just froze everything.
The thesaurus package is installed (I checked in Synaptic) but the problem seems to be specific to file type - the thesaurus works with .doc files but not .odt files.

---

### Post by philinux on 2008-01-31
> **kleo skywalker said:**
> philinux, tdrusk - when you say reinstall OpenOffice, does that mean remove the whole OpenOffice suite or just OpenOffice Writer?

If you need to do this then in synaptic it's openoffice.org. This is the complete package. Mark for complete removal then reinstall. I would delete the .openoffice.org2 config file from your /home/user folder before reinstalling.

---

### Post by kleo skywalker on 2008-01-31
> **philinux said:**
> If you need to do this then in synaptic it's openoffice.org. This is the complete package. Mark for complete removal then reinstall. I would delete the .openoffice.org2 config file from your /home/user folder before reinstalling.

Oh ok. I completely removed OpenOffice Writer and reinstalled it, this removed the openoffice.org package but did not install it again (actually, it removed 3 other packages too but didn't reinstall any.) Anyway, that made no difference to my thesaurus problem.
So now I'm going to remove the openoffice.org package and the reinstall it. I don't know what config file you're referring to - there's a .openoffice.org2 folder in my home folder, which in turn has a folder called config but there's no file by that name. ??

---

### Post by philinux on 2008-01-31
Just delete the .openoffice.org2 folder. Before you reinstall.

---

### Post by kleo skywalker on 2008-01-31
> **philinux said:**
> Just delete the .openoffice.org2 folder. Before you reinstall.

Did that. Problem persists. Thankful for your help, but very annoyed with OpenOffice.

---

### Post by philinux on 2008-01-31
Just double check that after your re-install that the thesaurus is installed in synaptic.

---

### Post by kleo skywalker on 2008-01-31
> **philinux said:**
> Just double check that after your re-install that the thesaurus is installed in synaptic.

It is installed (that package was unaffected by what I did; and like I said before, I can use the thesaurus when I'm working with .doc files but not with .odt files).

---

### Post by kleo skywalker on 2008-01-31
Oh no wait! I was mistaken - it doesn't seem to have to do with the file format after all. I tried saving a new file I was working on as .doc, but the thesaurus doesn't work with that either.
It seems that the thesaurus doesn't work with the files that I have created using OpenOffice Writer, but works with older files - the ones I created using Microsoft Word.
This is extremely annoying. I'm only asking for a word processor that gives me a functional thesaurus, not for it to take me to Mars!
Could someone please help me out on this? I have to do quite a bit of work, so could someone either tell me how to fix OpenOffice Writer or recommend another word processor with a working thesaurus? It could be an online one too (pity Google Docs doesn't have a thesaurus).
Thanks.

---

### Post by Hagar Delest on 2008-01-31
See that thread and check what's the language of the paragraph style: [[Tutorial] Spell check and Language configuration](http://user.services.openoffice.org/en/forum/viewtopic.php?f=7&t=67).

---

### Post by kleo skywalker on 2008-02-01
> **Hagar de l'Est said:**
> See that thread and check what's the language of the paragraph style: [[Tutorial] Spell check and Language configuration](http://user.services.openoffice.org/en/forum/viewtopic.php?f=7&t=67).

I looked at that link and I'm not sure what you mean by > language of the paragraph style
Could you please clarify?


Any other ideas? (I'm very annoyed, this shouldn't be so obtuse and difficult. I'm losing time because of this.)

---

### Post by zabien1970 on 2008-02-01
Was just looking at that thread and in 'spell check not working, why?' theres a section describing language and paragraph style, and if its set up wrong it changes your files, it also talks about how it handles windows files and after you save them it changes the format which sounds similar to what you're describing.

---

### Post by kleo skywalker on 2008-02-01
zabien1970, you're right.
I did what it said, and now I can use the thesaurus in new documents.
For older documents though, I still have to manually change the language settings for each file to be able to use the thesaurus. Is there a way to apply them to all documents?

---

### Post by Hagar Delest on 2008-02-01
No, except if they're based on the same template, then modify the default paragraph style in the template.

Else, you need to change the default paragraph style for each document. Note that you can record a macro to do that.

---

