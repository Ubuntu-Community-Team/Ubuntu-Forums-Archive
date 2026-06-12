---
title: "Batch file in Linux.."
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by sayakb on 2008-02-11
Is there some way to create something like a batch file in Linux (containing sequence of terminal commands)..

What I actually want to execute is:

metacity --replace
wxvlc %F
compiz --replace

The 3rd line wont be executed until I exit VLC player.

---

### Post by hyper_ch on 2008-02-11
there is, called shell scripts:

script.sh
```

#!/bin/bash
metacity --replace
wxvlc %F
compiz --replace

```

Then make the file executable:

```

sudo chmod 0755 script.sh

```

And now you can run it:

```

sh script.sh

```

for more, see

[http://www.linuxcommand.org](http://www.linuxcommand.org)

---

### Post by marshall.robert on 2008-02-11
im not a script guru, but i have done similar.

you open a text editor (gedit)

put those lines into it, save it as whatever you like

open a terminal and type:

chmod a+x /path/to/file

then you should be able to double click it and it should run, but you may need to run it in the teminal.

---

### Post by sayakb on 2008-02-11
> **hyper_ch said:**
> there is, called shell scripts:

script.sh
```

#!/bin/bash
metacity --replace
wxvlc %F
compiz --replace

```

Then make the file executable:

```

sudo chmod 0755 script.sh

```

And now you can run it:

```

sh script.sh

```

for more, see

[http://www.linuxcommand.org](http://www.linuxcommand.org)

The terminal waits at metacity --replace until I send some key interrupt. Is there some way I can make the default window manager replace, then run vlc and again compiz..??

---

### Post by sayakb on 2008-02-11
> **marshall.robert said:**
> im not a script guru, but i have done similar.

you open a text editor (gedit)

put those lines into it, save it as whatever you like

open a terminal and type:

chmod a+x /path/to/file

then you should be able to double click it and it should run, but you may need to run it in the teminal.

This executes only the 1st command and exits. :(

---

### Post by hyper_ch on 2008-02-11
you could try:

```

metacity --replace &

```
and then add the other ocmmands you want.

---

### Post by aashay on 2008-02-11
Why would you want to do that? Videos dont show properly under compiz? There are threads addressing the issue. Maybe you would like to look into that.

---

### Post by sayakb on 2008-02-11
> **aashay said:**
> Why would you want to do that? Videos dont show properly under compiz? There are threads addressing the issue. Maybe you would like to look into that.

Well, I don't like the X11 video mode. Some low-resolution vids become pixelated if scaled to large previews or fullscreen. I like OpenGL. Also, I do this with NetBeans, that doesnt work with compiz-fusion (or I don't know how to make it work :D).

---

### Post by sayakb on 2008-02-11
> **hyper_ch said:**
> you could try:

```

metacity --replace &

```
and then add the other ocmmands you want.

Thank you so much. That works perfectly. :)

---

