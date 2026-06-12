---
title: "I cant get Frostwire to open"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by voodoonirvana on 2006-09-27
I just freshly installed frostwire because I was having troubles opening LimeWire as well! So I get frostwire installed and I type "frostwire" into the terminal and get this:

runFrost.sh: 44: Syntax error: "(" unexpected (expecting "}")


I did a "locate forstwire" and it didnt do anything.

Then I tried "whereis frostwire" and it told me it was in:

frostwire: /usr/bin/frostwire /usr/lib/frostwire /usr/bin/X11/frostwire

---

### Post by voodoonirvana on 2006-09-27
Some help please?

---

### Post by llamakc on 2006-09-27
sudo ln -sf /bin/sh /bin/bash

You're using Edgy, right? 

Edgy is using dash for /bin/sh which causes your problem.

---

### Post by voodoonirvana on 2006-09-27
> **llamakc said:**
> sudo ln -sf /bin/sh /bin/bash

You're using Edgy, right? 

Edgy is using dash for /bin/sh which causes your problem.

No, Im using dapper actually.

---

### Post by deadgobby on 2006-09-27
[http://ubuntuforums.org/showthread.php?t=165371](http://ubuntuforums.org/showthread.php?t=165371)

---

### Post by voodoonirvana on 2006-09-27
> **deadgobby said:**
> [http://ubuntuforums.org/showthread.php?t=165371](http://ubuntuforums.org/showthread.php?t=165371)

Did that, still wouldn't open. Then tried installing it with Automatix, and still got this.

sam@sam-laptop:~$ frostwire
runFrost.sh: 44: Syntax error: "(" unexpected (expecting "}")

---

### Post by BatteryCell on 2006-09-27
Well when I opened up runFrost.sh (/usr/lib/frostwire/runFrost.sh) This is my line 44:
```

potential_java_dirs=(`ls -d1 "$JAVADIR"/j* | sort | tac`)

```

Is that what your line 44 looks like?

---

### Post by buckethead27 on 2006-09-27
Just install Java from automatix and CTRL-ALT-DEL

---

### Post by voodoonirvana on 2006-09-27
> **BatteryCell said:**
> Well when I opened up runFrost.sh (/usr/lib/frostwire/runFrost.sh) This is my line 44:
```

potential_java_dirs=(`ls -d1 "$JAVADIR"/j* | sort | tac`)

```

Is that what your line 44 looks like?

  potential_java_dirs=(`ls -d1 "$JAVADIR"/j* | sort | tac`)

Yep, thats what it looks like.

---

### Post by brodock on 2006-09-30
change your /usr/bin/frostwire to:
```

#!/bin/bash
cd /usr/lib/frostwire
bash runFrost.sh

```

---

### Post by airblade on 2006-10-20
> **brodock said:**
> change your /usr/bin/frostwire to:
```

#!/bin/bash
cd /usr/lib/frostwire
bash runFrost.sh

```

I got frostwire working with this solution.
Using Edgy...

---

