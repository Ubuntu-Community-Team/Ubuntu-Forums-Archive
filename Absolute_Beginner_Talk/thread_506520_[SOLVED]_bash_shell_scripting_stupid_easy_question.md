---
title: "[SOLVED] bash shell scripting stupid easy question that'll take u seconds to answer"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by Contrarian on 2007-07-21
I want to write a one liner bash script so that I can change directory (the path is rather long, and i'd rather type ./gotodir instead when i login).

I enter in the script the one line;

  cd /really/long/dir/path/here

but it's failing.  Is this the correct syntax or should i do something else?  I've tried with just 'cd /usr' and that fails also, so I'm guessing it's a syntax error.  I'm logged in with god-like permissions so it wouldn't be that.

---

### Post by aktiwers on 2007-07-21
Did you try putting the path in quotes like this:
cd "/really/long/dir/path/here/"

---

### Post by scxtt on 2007-07-21
you need more than just the "cd to such and such directory" ...
```

#!/bin/bash

cd /this/is/a/really/really/long/path/even/longer/than/it/should/be

```and make sure your script is executable ...

this won't technically work how you want anyway - use an alias ...

alias GoHere='cd /this/is/a/really/really/long/path/even/longer/than/it/should/be'

---

### Post by Contrarian on 2007-07-21
> **scxtt said:**
> 

this won't technically work how you want anyway - use an alias ...

alias GoHere='cd /this/is/a/really/really/long/path/even/longer/than/it/should/be'

Hmm... I can just throw that in my .bashrc file can't I...

... Yup, works like a charm

Thank you!!

---

