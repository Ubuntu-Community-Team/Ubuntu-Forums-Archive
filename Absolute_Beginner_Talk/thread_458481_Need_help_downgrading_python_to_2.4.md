---
title: "Need help downgrading python to 2.4"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by drewu on 2007-05-29
Hello all!

I have python 2.5 and python 2.4 on my ubuntu box but am unable to play with Soya3D. After asking their forums I was told to downgrade python to 2.4. How would I do this without removing a bunch of packages like synaptic prompts?

Thanks for the help!

---

### Post by greybirds on 2007-05-29
How are you starting the python scripts? You may not need to remove anything at all.

---

### Post by drewu on 2007-05-29
I am running the scripst as such:
python py_script_to_be_run.py

---

### Post by zekopeko on 2007-05-29
ok this is just a guess but python is probably a symlink to /usr/bin/python2.5 or something similar. 
couldn't you try 

```
python2.4 script_to_run.py?
```

---

### Post by drewu on 2007-05-29
Yes, that does work.
Would there be any other way to downgrade python? I would rather just use python 2.4 exclusively.

---

### Post by greybirds on 2007-05-30
I'm not sure Gnome would like that. I think it uses python extensively, and might rely on 2.5-specific features. Then again, if you remove 2.5 take note of what gets uninstalled with it; you can always reinstall it later if you find life in Gnome's turned hellish. Be prepared to install it in text-mode, though.

Another option to try is to leave 2.5 installed but set /usr/bin/python to point to /usr/bin/python2.4 instead of /usr/bin/python2.5. I would hope that the developers would code in version dependencies into their python scripts, in which case you'd never see any difference. But if you did, you can always link the python command back to 2.5.  The "ln" command (that's a lowercase L) will create the links for you. 

You could also set up a custom link to /usr/bin/python2.4 like "/usr/bin/py" or "/usr/bin/Python". Then you could run your soya scripts with "py filename.py" Again, the ln command would do that. 

Can't think of any more off the top of my head. Hope this helps.

---

### Post by drewu on 2007-06-01
Very helpful!
I didn't even think of ln.

Thanks for the ideas guys.

---

