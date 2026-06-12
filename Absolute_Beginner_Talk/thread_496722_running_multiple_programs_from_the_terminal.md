---
title: "running multiple programs from the terminal"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by maverick23r on 2007-07-09
This is a really stupid question but is it possible to run programs from the terminal (konsole) and still be able to use the same shell? Basically I don't want to have a separate shell for every program that I open and I'm wondering if there is a way around that. Thanks.

---

### Post by Malibu Illusion on 2007-07-09
Put this after a command:

```
&
```

So, for example:

```
firefox &
```

---

### Post by maverick23r on 2007-07-09
Boss, I feel slightly less dumb now, thanks!

---

### Post by Pragmatist on 2007-07-09
Often you can run programs in the background using the "&":
```
program &
```

You can also use job control by typing CTRL Z and then typing bg to put it in the background.  You can do the same with fg to put it back in the foreground.  Read the bash man page for more information:
```
man bash
```

You can search man pages by using the /  Once inside the man page type this:
```
/background
```
Then keep hitting ENTER to see more and more instances of the word background in the man page.

---

### Post by UnixAnt on 2007-07-09
Also, don't overlook the usefulness of the 'screen' command.

As far as I can remember, if you use bash (I don't) you have to add something like the following to your .bashrc

alias screen='TERM=screen screen'

Screen enables you to run multiple pseudo consoles within a console.  Its really, really useful.

---

### Post by Pragmatist on 2007-07-09
> **UnixAnt said:**
> Also, don't overlook the usefulness of the 'screen' command.

As far as I can remember, if you use bash (I don't) you have to add something like the following to your .bashrc

alias screen='TERM=screen screen'

Screen enables you to run multiple pseudo consoles within a console.  Its really, really useful.
Very interesting!  I was able, however, to use this screen command without setting any alias.  You can use the man page to find out more, or there is an excellent book called "Unix Power Tools" which has some excellent explanations about the screen command.  Thanks UnixAnt!

---

### Post by UnixAnt on 2007-07-10
> **Pragmatist said:**
> I was able, however, to use this screen command without setting any alias.  You can use the man page to find out more, or there is an excellent book called "Unix Power Tools" which has some excellent explanations about the screen command.  Thanks UnixAnt!

Ahh, that's good to know.  I use ksh and haven't used bash as my main shell for a couple of years now.

Whilst I don't use screen every single day, it is definitely one of my more popular cli tools.  Its incredibly powerful.

Anyway.  Glad to be of help :D

---

