---
title: "Squid and Gnupg"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by ieuph7 on 2006-10-03
Hi there.  I'm a brand new ubuntu user and want to install Squid and gnupg to use.  I've used the synaptic package manager to get them, but I'm now completely lost.  Can anyone walk me through what to do next?

---

### Post by podunk on 2006-10-03
Are you trying to find the executables?

What I do is 

```
 sudo updatedb 
```

then I type

```
 locate file_name_whatever | less 
```

This will return every instance of the file name, which is why I use the pipe less ( | less) command, you can use the arrow keys to go up and down the list. Press the letter "q" when done to get back to the command prompt.

I then use Nautilus to find whatever, I right click it and chose “Open” and if the program starts I know the right path.

I right click my desktop and chose “Create Launcher” and drag the file over to the “command” line and give it a name.

---

