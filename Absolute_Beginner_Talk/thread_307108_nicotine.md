---
title: "nicotine"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by paripamano on 2006-11-26
Hello there!

Can anybody help me to get nicotine work?

i installe dit in sínaptic, but doesnt even start. then i tried to download a new version from its source page, but still not doing anything.

any suggestions?

thanks

this is what i get, when i try to run the newest version from command window:

./nicotine
Nicotine supports "psyco", an inline optimizer for python
code, you can get it at [http://sourceforge.net/projects/psyco/](http://sourceforge.net/projects/psyco/)
Traceback (most recent call last):
  File "./nicotine", line 151, in ?
    result = checkenv()
  File "./nicotine", line 98, in checkenv
    print _("""Nicotine supports a country code blocker but that
  File "/usr/lib/python2.4/gettext.py", line 568, in gettext
    return dgettext(_current_domain, message)
  File "/usr/lib/python2.4/gettext.py", line 532, in dgettext
    codeset=_localecodesets.get(domain))
  File "/usr/lib/python2.4/gettext.py", line 480, in translation
    t = _translations.setdefault(key, class_(open(mofile, 'rb')))
  File "/usr/lib/python2.4/gettext.py", line 177, in __init__
    self._parse(fp)
  File "/usr/lib/python2.4/gettext.py", line 301, in _parse
    plural = v[1].split('plural=')[1]
IndexError: list index out of range

---

### Post by paripamano on 2006-11-26
please, 

is there anybody who can help???

---

### Post by junglepeanut on 2006-11-26
OK, I will try. Let me see what happens when I get it.

---

### Post by junglepeanut on 2006-11-26
Try getting it from synaptic again, I just did 

sudo aptitude install nicotine 

and it worked fine.

Let me know when you have it running please then I will uninstall mine.

---

### Post by paripamano on 2006-11-26
Sorry , I've tried, but nothing happened.

---

### Post by junglepeanut on 2006-11-26
What did you do? How did you try to install? Did you try doing it my way from a terminal? How did you try to start it? 

I need information, not it doesn't work.
Sorry but I am about to pass out and getting cranky.

---

### Post by junglepeanut on 2006-11-26
Please try installing via the terminal, so you can easily paste any errors it gives. If for some weird reason it wont work I will look into the newer version, but the apt one should be working, if it is not we need to fix that more than fix nicotine.

hmmm What version of nicotine are you getting in synaptic? Mine is 1.2.6

---

### Post by junglepeanut on 2006-11-26
I am off to bed I will check this in the morning.

---

### Post by paripamano on 2006-11-26
sorry, i had to walk the dog.

the version in synaptic is an older one, so i installed the 1.2.6

but still nothing, then i uninstalled the synaptic version and tried the 1.2.6 that way from the terminal. now it works.

thnks

---

### Post by junglepeanut on 2006-11-26
excellent, I dont know how I stayed awake but I wanted to know this was resolved. 

Goodluck with the rest of linux.

---

