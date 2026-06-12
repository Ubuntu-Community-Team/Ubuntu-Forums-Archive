---
title: "wine doesn't work."
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by Caligula on 2006-04-16
I've downloaded IE5 and tried to install it using wine, but at the first screen6, whike setup is intializing, an error message comes up and says that setup can't continue when I press "help" it says that it may be because the internet connection is broken and that I should try to close all applications and try again, it didn't work. 

When I'm trying to install IE6, at the same stage it pops an error message that says  that setup couldn't connect to the internet, to download the rest...

What else can I try?
thanks

---

### Post by Caligula on 2006-04-16
*screen, while
**continue, when

---

### Post by hentaidan on 2006-04-16
I would recommend trying ies4linux @ [http://www.tatanka.com.br/ies4linux/]("http://www.tatanka.com.br/ies4linux/"). Lets you install IE 5/5.5/6 with a bash script.

Worked fine for me.

---

### Post by Caligula on 2006-04-16
It doesn't work for me, the executable just won't execute...

---

### Post by croak77 on 2006-04-16
Do you have wine and cabextract installed?

---

### Post by Caligula on 2006-04-17
yes, everything is installed...

---

### Post by mostwanted on 2006-04-17
[QUOTE=Caligula]It doesn't work for me, the executable just won't execute...[/QUOTE]

Scripts aren't executable by default on most mounted file systems. This will make it executable:
```

sudo chmod +x ies4linux
```

---

### Post by Caligula on 2006-04-17
I've done it, clicked on it again, didn't start, didn't do anything...

---

### Post by mostwanted on 2006-04-17
[QUOTE=Caligula]I've done it, clicked on it again, didn't start, didn't do anything...[/QUOTE]

It's not a pretty GUI, it's command line script that requires you to interact from the terminal (select what versions of IE to install etc.). Open it in a terminal,

---

### Post by Caligula on 2006-04-17
wow! thanks for that, mate...
Why is it always happening to me that the solution is so simple and I miss it?

anyway, it's downloading now, lets hope it'll work...

---

### Post by mostwanted on 2006-04-17
[QUOTE=Caligula]wow! thanks for that, mate...
Why is it always happening to me that the solution is so simple and I miss it?

anyway, it's downloading now, lets hope it'll work...[/QUOTE]

Yeah, it's just the cultural differences between Linux and Windows :)

Normally when you have trouble running a script, you try opening it in the terminal; this will display the error output which is necessary for determining why the script doesn't work. Even more often, the scripts are meant to be run from the terminal, like in your case :)

It should work just fine.

---

### Post by Caligula on 2006-04-17
oy!
is there any way to add encodings to it?
I can't see hebrew sites...

---

### Post by mostwanted on 2006-04-17
Hm, in the view menu you can set temporary encodings, I know that much. Haven't used IE in a while.

---

### Post by Caligula on 2006-04-17
yeah, normally you can, but not here...
When I go to the "encoding" thing, it open a new menu, where the encodings are supposed to be, but nothing is the...

---

### Post by mostwanted on 2006-04-17
[QUOTE=Caligula]yeah, normally you can, but not here...
When I go to the "encoding" thing, it open a new menu, where the encodings are supposed to be, but nothing is the...[/QUOTE]

Hm... as far as I can remember it takes a while to load that menu when running IE in WINE. Dunno why.

---

