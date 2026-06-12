---
title: "What did I Install?"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by think13 on 2006-10-05
I recently installed a package from source.  Well, I can't find the name of the command in the terminal to run the program!
Some ideas I had to get the command:
1) Somehow page up in the terminal, the install was too long, I couldn't see the top of it.  
2) Read some sort of system log and find the name.
3) Find the executable file in the filesystem

Which one of these will work best for me?  Or is there something else I can do?

---

### Post by podunk on 2006-10-05
To start with – in the directory where you uncompressed the source files there may well be a README or “Install” text file.

You could do this
```
sudo updatedb
```

This takes a few seconds.

Then
```
 locate <filename> | less  
```

This will return every mention of the file. I use pipe less ( | less} because some programs like games have tons of files. You can use your arrow keys to move up and down the list. When done press “Q” to exit less.

Usually there will be some directions in the /usr/share/doc folder on your app.

Hope this helps!

---

### Post by slightcrazed on 2006-10-05
You can try 2 things:

which *program*

or:

locate *program* | grep bin

Both do just about the same thing, but the 2nd will work even if the program installed to a directory outside your path. The 2nd does assume that the executable is in a directory called 'bin', but this is a pretty good assumption. 

slight

---

