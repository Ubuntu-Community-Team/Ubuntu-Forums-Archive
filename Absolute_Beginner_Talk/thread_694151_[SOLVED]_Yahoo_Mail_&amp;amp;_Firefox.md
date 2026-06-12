---
title: "[SOLVED] Yahoo Mail &amp;amp; Firefox"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by anchor1te on 2008-02-11
Running Gutsy and all of a sudden, when I try to log in to Yahoo Mail, it locks everything up.  Can't move anywhere so I can't check monitor or conky.  Was wondering if anyone else has seen this.  Haven't done anything new to my setup before this started happening.

Thanks much!

---

### Post by sports fan Matt on 2008-02-11
What version of Firefox? Does this happen in other browsers like Opera?  Are you fully patched & updated?

---

### Post by anchor1te on 2008-02-11
Firefox 2.0.0.12.  Also happens in Kazehakase.  Gutsy is all up to date.  Not sure if it's something to do with Yahoo Mails new extra steps they have started doing.

---

### Post by sports fan Matt on 2008-02-11
could be..i use yahoo mail but not the new version...

I had read earlier last summer they were implenting a new mail system..

---

### Post by LookTJ on 2008-02-11
Hmm, the new version seems to work fine for me.

---

### Post by nikoPSK on 2008-02-11
> **anchor1te said:**
> Running Gutsy and all of a sudden, when I try to log in to Yahoo Mail, it locks everything up.  Can't move anywhere so I can't check monitor or conky.  Was wondering if anyone else has seen this.  Haven't done anything new to my setup before this started happening.

Thanks much!

please run the command ```
firefox
``` in the terminal, give the output when it hangs.

---

### Post by LookTJ on 2008-02-11
> **anchor1te said:**
> Running Gutsy and all of a sudden, when I try to log in to Yahoo Mail, **it locks everything up.  Can't move anywhere so I can't check monitor or conky.  **Was wondering if anyone else has seen this.  Haven't done anything new to my setup before this started happening.

Thanks much!

> **nikoPSK said:**
> please run the command ```
firefox
``` in the terminal, give the output when it hangs.One problem, how does one post an output if it **locks** **everything** up?

---

### Post by anchor1te on 2008-02-11
From memory before I had to turn it off:

Error Unimplemented SWF8

Error Unimplemented Fileattributes Gnash won't care

Error Unimplemented Gnash

Error Unimplemented sharedobject_getlocal

---

### Post by LookTJ on 2008-02-11
You could try to create a new profile, if it fails again

```
firefox -P
``` and see if the problem persist.

---

### Post by LookTJ on 2008-02-11
> **anchor1te said:**
> From memory before I had to turn it off:

Error Unimplemented SWF8

Error Unimplemented Fileattributes Gnash won't care

Error Unimplemented Gnash

Error Unimplemented sharedobject_getlocal
Flash problem? Why Gnash and not Adobe?

---

### Post by nikoPSK on 2008-02-11
It;s gnash do this:
```

sudo apt-get install flashplugin-nonfree
```

---

### Post by anchor1te on 2008-02-12
Taylor and nikoPSK, tried both of your steps with the same result

As to why Gnash, I think I selected it when I had a pop-up to install in firefox.  Going to try and uninstall the Mozilla plugin to see if that resolves it.

---

### Post by nikoPSK on 2008-02-12
> **anchor1te said:**
> Taylor and nikoPSK, tried both of your steps with the same result
 
As to why Gnash, I think I selected it when I had a pop-up to install in firefox. Going to try and uninstall the Mozilla plugin to see if that resolves it.
 
no please try removing gnash and leaving just the flash nonfree.

---

### Post by anchor1te on 2008-02-12
Victory!!  No more Gnash, no more problem.  Thank you muchly!!

---

### Post by nikoPSK on 2008-02-12
> **anchor1te said:**
> Victory!!  No more Gnash, no more problem.  Thank you muchly!!

--> [IMG]http://ubuntuforums.org/images/uf/buttons/post_thanks.gif[/IMG]

Anyways, please mark this thread as solved by going to thread tools at the right top of the page. :)

---

