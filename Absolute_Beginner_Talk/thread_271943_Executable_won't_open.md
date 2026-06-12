---
title: "Executable won't open"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by soopafly on 2006-10-05
Hello all,
Brand new to the Linux world and slowing learning.

I've downloaded [AdvanceMame]("http://advancemame.sourceforge.net/readme.html") and compiled the source using

```

./configure
make
make install

```

This resulted in an executable file (which is the purple looking diamond, correct?)  When I double click this file, nothing happens.  Am I doing something wrong here?

---

### Post by skymt on 2006-10-05
> **soopafly said:**
> Hello all,
Brand new to the Linux world and slowing learning.

I've downloaded [AdvanceMame]("http://advancemame.sourceforge.net/readme.html") and compiled the source using

```

./configure
make
make install

```

This resulted in an executable file (which is the purple looking diamond, correct?)  When I double click this file, nothing happens.  Am I doing something wrong here?

AdvanceMame doesn't have a GUI. If you had run it from a terminal, it would have given you an error message.

Try running it from a terminal, like this:```
advancemame /path/to/rom.zip
```Or, you can try a graphical frontend, like AdvanceMenu, from the same team.

---

### Post by soopafly on 2006-10-05
I see now.  I did download and compile AdvanceMenu, but had to run out the door because I was late for work.  How to I launch AdvanceMenu?

Thanks for your help!!;)

BTW I'm just reading about AdvanceCD and it looks like something that I want to try as well.

---

### Post by Patrick-Ruff on 2006-10-05
the thing about linux is a lot of stuff requires the command line, you compiled it...but where are such files? theres a good possibility that compiling left an executable, perhaps .sh, so in terminal it would be something like ```

sh /compiledfile.sh 
```

it really varies, you'll learn as you go along.

---

### Post by skymt on 2006-10-05
> **soopafly said:**
> I see now.  I did download and compile AdvanceMenu, but had to run out the door because I was late for work.  How to I launch AdvanceMenu?

Thanks for your help!!;)

BTW I'm just reading about AdvanceCD and it looks like something that I want to try as well.

Sorry, I can't help you with AdvanceMENU. I tried it once, got annoyed, and switched back to running AdvMAME from the command line. Your best bet is to read the documentation. If you have questions, ask them in the Games forum here, or at the [AdvanceMENU forum](http://sourceforge.net/forum/forum.php?forum_id=313512).

---

