---
title: "what happened to my aliases?"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by JohnJSal on 2006-08-08
Following the directions of a site I found, I set up a few terminal aliases like this:

alias sau='sudo aptitude update'

But now they are all gone! There was no mention of saving these to a file, so I didn't know I needed to do that, if that's the case. How can I be sure I retain my aliases after a reset or after I close and reopen the shell?

Thanks.

---

### Post by Third Thoughts on 2006-08-08
you'll want to write them to a file. First open up gedit and write down all the aliases in the format 
```

alias <custom command>=<normal commands>

```
Each alias goes on a seperate line

Save this file in your home directory as .bash_aliases.
Then open up your .bashrc file in your home directory. There should be a commented out section that looks a little like this.
```

#Define your own aliases here ...
#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

```

Uncomment everything execpt the first line. If you don't have this section, add it. That should make your aliases permanent

~Andrew S.

---

### Post by JohnJSal on 2006-08-09
Thanks!

---

