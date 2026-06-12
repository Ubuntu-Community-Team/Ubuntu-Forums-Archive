---
title: "Tab in BASH - confusing results"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by thomasf on 2007-10-23
Hi!

I've come across puzzling behavior of TAB key in Bash.
Look at this:

> tomek@tomek-desktop:~$ ping[space][TAB] 

Results:
> tomek@tomek-desktop:~$ ping |1|

I get the same results with other network-related command -  traceroute, but I guess it's only a coincidence. Of course I'm aware of the fact that TAB is used in command completion.
Can someone explain it to me? 

Regards,
Thomas

---

### Post by Daishiman on 2007-10-23
It seems to me like it's showing matches from the .ssh/known_hosts file, which keeps a cryptographic fungerprint of hosts that you've accessed through SSH.

---

### Post by ice60 on 2007-10-23
it could be something to do with the program called tab completion (i think that's the name), it does intelligent tab completions.

---

### Post by js_fr on 2007-10-23
In my case - typing ```
ping[space][tab]
``` does a file name completion ...

---

### Post by thomasf on 2007-10-23
Thx for quick reply!

You're right - I should have checked /etc/bash_completion!
How this feature can be used?

---

### Post by ice60 on 2007-10-23
> **thomasf said:**
> Thx for quick reply!

You're right - I should have checked /etc/bash_completion!
How this feature can be used?
i don't know much about it, but i just tried ping[space][TAB] and nothing happens, i'm not using ubuntu and don't have bash completion installed, so it looks like it must be that. it sounds like a usful program from the things i've read about it.

---

### Post by js_fr on 2007-10-23
> **ice60 said:**
> i don't know much about it, but i just tried ping[space][TAB] and nothing happens, i'm not using ubuntu and don't have bash completion installed, so it looks like it must be that. it sounds like a usful program from the things i've read about it.
Completion is built into bash so you don't have to install it :)
If you type ping[space][TAB] and nothing happens this means that you have more than one (or none) completion possibility. Try ping[space][TAB][TAB], this should give you the content of your current directory (same output as "ls").  If you have e.g. one file that starts with "t" and you type ping[space]t[TAB] this should complete the filename.

---

### Post by ice60 on 2007-10-23
> **js_fr said:**
> Completion is built into bash so you don't have to install it :)
If you type ping[space][TAB] and nothing happens this means that you have more than one (or none) completion possibility. Try ping[space][TAB][TAB], this should give you the content of your current directory (same output as "ls").  If you have e.g. one file that starts with "t" and you type ping[space]t[TAB] this should complete the filename.
i promise you there's a program called tab completion and it's not a builtin program like using the TAB button.

the builtin TAB isn't the same thing. the program tab completion is intelligent, so if you run this 
tar xvfz [TAB]
it will only look for programs ending in .gz, using the builtin TAB will look for all programs in the current directory

if you find the name of the tab completion program run this command
type "name of the tab complete program"
and it won't say builtin, it will point to somewhere on the computer.

> Try ping[space][TAB][TAB]
nothing happens when i do that, that's why i think it's the program tab completion that's doing the tab completions because i don't have it installed :)

like i said though, i've never used the program tab completion and don't know much about it, if you really know what you're talking about i'll take your word for it.

---

### Post by ice60 on 2007-10-23
this could be what i'm talking about, i'm not sure :confused:
[http://freshmeat.net/projects/bashcompletion/](http://freshmeat.net/projects/bashcompletion/)

---

### Post by nick_h on 2007-10-23
If you look in the bash help using,
```
yelp man:bash
```
there are two sections to read, one called "Completing" and the other called "Programmable Completion".

The intelligent one you are describing is defined in the file /etc/bash_completion and is run from one of the bashrc scripts.

---

