---
title: "emacs and termcap..."
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by Greggle on 2007-06-17
I wanted to compile emacs from the source just to see how it all works, compiling that is.

Anyway, ./configure/make/install worked fine. However, once I tried to run emacs I received the error: 'cannot open the termcap database file.'

I did some searching and it would appear that termcap has been replaced by terminfo. I don't even know what termcap is, so the change to 'terminfo' is equally meaningless.

I tried to install termcap-compat per a recommendation I found elsewhere, but it did not work; it didn't exist anymore... I guess...

'How can I get emacs running,' I wonder quietly to myself?

P.S. I searched both Google and these-here forums, but the NUMEROUS suggested solutions have not availed me.

-Thanks

---

### Post by weel on 2007-06-17
Can you tell us what version of emacs you are trying to compile and where you got it? Also, can you tell us what operating system and version you are using? Lastly, can you tell us the contents of the TERM environment variable in the terminal that you are trying to run emacs in? (Just do echo $TERM to find out.)

Also, the output from the ./configure program might be useful. You can capture it using 

./configure 2>&1 > configure-output.txt

The learning curve for this kind of stuff can be a bit steep, but please do continue on and feel free to ask questions. At some point it will all start to make sense.

---

### Post by igray78756 on 2007-06-28
I found a solution to this problem:

First run:

```
$ sudo apt-get install libncurses5-dev
```

Then re-compile emacs:

```
$ ./configure
$ make
$ sudo make install
```

That should let you run emacs in a terminal again.

---

