---
title: "[SOLVED] what does this command do?"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-12-01
i was flicking throught the interweb reading about tune2fs and hdparm.

the website wasnt a real site by a company, it was one some person created.

anyway, reading through, lots of what seemed normaly command and then i noticed a weird command that we was told to enter in the terminal, no letterst. im a bit curious


```
 :(){ :|:& };: 
```

what does it do?

---

### Post by Dr Small on 2007-12-01
It's the fork bomb. DO NOT RUN IT.
Please read more in the Announcement!!!

[http://ubuntuforums.org/announcement.php?f=73](http://ubuntuforums.org/announcement.php?f=73)

---

### Post by skymera on 2007-12-01
ahhhhhh
amazing how a siple line can do so much 

i wasnt planning on running, looked odd.

anyway thanks :)

---

### Post by imtheguru on 2007-12-04
Don't fear code. Understand it.



```
:(){ :|:& };:
```

From [[http://www.euglug.org/pipermail/euglug/2005-August/004338.html]](http://www.euglug.org/pipermail/euglug/2005-August/004338.html])

    It creates a function called ":" that accepts no arguments-- that's
    the ":(){ ... }" part of the utterance.

    The code in the function calls the recursively calls the function
    and pipes the output to another invocation of the function-- that's
    the ":|:" part. The "&" puts the call into the background-- that way
    the child process don't die if the parent exits or is killed. Note
    that by invoking the function twice, you get exponential growth in
    the number of processes (nasty!).

    The trailing ";" after the curly brace finishes the function definition
    and the last ":" is the first invocation of the function that sets off
    the bomb.

    Most unpleasant...



Just replace ":" with some word, it will be easier to understand:

kill(){kill|kill&};kill

    kill()
    {
    kill | kill &
    };
    kill

---

### Post by skymera on 2007-12-04
now i understand, its bad :)

---

