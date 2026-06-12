---
title: "lost my color coding of filenames in my bash shell"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by madeupname on 2007-07-19
Does anyone know what could possibly have happened to my Bash shell?  In a related thread I complained about my profile.local no longer being read and/or used so my environment variables were not being set.  Well now I see that my color coding for files and directories has also disappeared.

Does anyone have any idea what may have happened or how I may revert back to a previous state?

Other than receiving two updates over the net and not even paying much attention to what they were I haven't intentionally done any changes in configuration and yet my whole system all of a sudden has quirks?

Any ideas?

Egads sometimes I think Ubuntu has a mind of its own.

Bill

---

### Post by iver2435 on 2007-07-19
You could alias ls like this:

```
alias ls='ls --color=auto'
```

and that would get you color when you use the ls command....

Here is a clipping out of my .bashrc file:

```

# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
fi
 
```

so, in theory, if you have this in your .bashrc file, you should be golden.....but given what you said about your .profile file not being recognized, you could have bigger issues...

if you type  "source .bashrc", what happens?

---

### Post by asmoore82 on 2007-07-19
if the color coding magically disappeared someone or something may have tampered with the
"profile" defaults stored in '/etc'

---

