---
title: "basic wine issues"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by Craigy on 2006-10-29
hi there.

apologies if this belongs in gaming, but i am an absolute beginner having just installed ubuntu 6.10 and beryl. wow. eye-candy that is functional.

anyhow my first question(s) is to do with wine (specifically with counter stike source)

1) running wine --help is states you can use "arguments" at the end of the command. is there somewhere that lists these arguments? 

2) trying to get the best performance from counter stike source, the only thing i have found is to use "WINEDEBUG="fixme-all" wine Steam" (from [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games)). this runs fine from the terminal, but if i amend the menu entry to this command it errors with "cannot find the command "WINEDEBUG="fixme-all"". is there a way to get this extra command in the menu item?

3) if i run counter strike source fullscreen it hijacks the entire desktop resolution and "shifts" the entire screen downwards (e.g. bottom half of screen missing and top half of screen black)

many thanks craig

---

### Post by willy1234x1 on 2006-10-29
I wouldn't know how to help you with that I'd just say cedega is a good investment for gaming

---

### Post by CatKiller on 2006-10-29
> **Craigy said:**
> 1) running wine --help is states you can use "arguments" at the end of the command. is there somewhere that lists these arguments?

Those arguments are, I believe, arguments for the program you are trying to run with Wine. So no, there's no central store of all arguments. Check the documentation of whatever it is you're trying to run.

**man wine** will tell you some stuff about the options for when you run Wine, though.

> 2) trying to get the best performance from counter stike source, the only thing i have found is to use "WINEDEBUG="fixme-all" wine Steam" (from [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games)). this runs fine from the terminal, but if i amend the menu entry to this command it errors with "cannot find the command "WINEDEBUG="fixme-all"". is there a way to get this extra command in the menu item?

From **man wine**:
>        wine makes the environment variables of the shell from  which  wine  is
       started  accessible  to  the  windows/dos processes started. So use the
       appropriate syntax for your shell to enter  environment  variables  you
       need.

I don't know what the appropriate syntax is for your shell, although it's probably **bash**.
> 3) if i run counter strike source fullscreen it hijacks the entire desktop resolution and "shifts" the entire screen downwards (e.g. bottom half of screen missing and top half of screen black)

You could try turning off Beryl. Or running the game at a different resolution. Other than that, I don't know what to suggest, other than browsing through the Gaming & Leisure forum in case someone there has fixed a similar issue.

Good luck, and welcome to the community.

---

