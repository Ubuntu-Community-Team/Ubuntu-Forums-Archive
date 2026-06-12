---
title: "Color terminal output?"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by Mets on 2008-03-28
I'm running Ubuntu as a server (i.e. without an x-session) and I want to get a little color on my terminal output.  Right now I have a black background and all the text is white, which is kinda hard to read when you have lots of files.

I know there is a way to do some basic colorizations, but I can't remember.  I'll I'd like to do is make folders print out in blue, files in white, binaries in green - something to that effect, nothing drastic.  Can anybody tell me how to do this?  I'm using bash.  Thanks.

---

### Post by ahsile on 2008-03-28
Add to your .bashrc file in the home directory
```

alias ls='ls --color=auto'

```

To reload settings without logging in, type:

```
. .bashrc
```

---

### Post by Mets on 2008-03-28
Thanks, that was what I was looking for!

Is there any way to make it load automatically everytime I login though?

---

### Post by ahsile on 2008-03-31
Sorry for the slow response, but been busy on the weekend... You may have already noticed that this should work automatically when you log in. The .bashrc file is read every time you log into a bash shell and sets up all of your aliases for you! Wouldn't have given you a solution that made you do extra work all the time. :)

---

