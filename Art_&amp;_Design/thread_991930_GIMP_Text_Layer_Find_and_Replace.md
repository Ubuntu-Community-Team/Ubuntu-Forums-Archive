---
title: "GIMP Text Layer Find and Replace"
date: 2008-11-24
forum: Art &amp; Design
---

### Post by rtsnhatl on 2008-11-24
I have several images with many text layers where in the layers I have put "X's" that I want to search out and replace with numbers.  (for example replace ATS-XA-2 with ATS 1A-2 or ATS 2A-2 )  Is there a quick way to either load all the text strings from a single text file or do a global search and replace of the XCF file.  I can do scripting and CLI, just not sure where to start.  Thanks in advance for any suggestions.

---

### Post by cr33dog on 2008-11-30
Well, I did not really think that this would work, but it did:

I created a file called test.xcf with one text layer containing the word "test".

Then I used this command:
```
cat test.xcf | sed 's/test/TEST/g' > test2.xcf
```

And "test" was replaced with "TEST".  Whether or not this method will
work for more complex documents I do not know.  It seems possible to write a plug-in also...

Chris

---

### Post by cr33dog on 2008-11-30
Well, I wrote a quick plug-in also ;)

[http://registry.gimp.org/node/12212](http://registry.gimp.org/node/12212)

Chris

---

### Post by Samhain13 on 2008-12-01
Hello cr33dog, I just gave your plug-in a try. I get this error:

```
Traceback (most recent call last):
  File "/usr/lib/gimp/2.0/python/gimpfu.py", line 662, in response
    dialog.res = run_script(params)
  File "/usr/lib/gimp/2.0/python/gimpfu.py", line 347, in run_script
    return apply(function, params)
  File "/home/arielle-cruz/.gimp-2.4/plug-ins/find_and_replace-0.1.py", line 19, in find_and_replace
    if pdb.gimp_drawable_is_text_layer(layer): #only act on text layer
error: procedure not found
```

I'm using version 2.4.5, in Ubuntu 8.04.

---

### Post by cr33dog on 2008-12-01
Hi Samhain13,

I think that the procedure gimp_drawable_is_text_layer() must have been added in GIMP 2.6.  I found this guide to installing GIMP 2.6 on Hardy and it looks safe to me:
[http://tombuntu.com/index.php/2008/10/13/install-gimp-26-in-ubuntu-804/](http://tombuntu.com/index.php/2008/10/13/install-gimp-26-in-ubuntu-804/)

Just be sure to reinstall 'ubuntu-desktop' if you ever decide to upgrade to 8.10.  (8.10 includes GIMP 2.6.1)

Chris

---

### Post by rtsnhatl on 2008-12-31
Thanks, just getting back to this after being pulled away on something else...also needed to learn python seems like a great language picked it up real quick.

---

### Post by rtsnhatl on 2008-12-31
Chris,

Many thanks that worked beautifully, and did exactly what I was looking to do.  When I originally made this post I really knew nothing about GIMP or Python, now that I have learned it I can use it extensively.

Bob:D

---

