---
title: "How do I create a script to automatically run terminal lines?"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by Feba on 2007-04-05
I thought all you had to do was create a file with ".sh" and put the terminal lines inside it, but that didn't work. 

Tried googling it, but google doesn't play well with ".thing", so looking up ".sh" would be a nightmare. 

Just need a simple solution or guide, thanks.

---

### Post by RaZer0r on 2007-04-05
did you make the file executable? If not: do
```

chmod +x filename.sh

```
you can run the file than with:
./filename.sh if you are in the directory where the file is (or double klik it), or you can add it to the /usr/local/bin directory which allows you to open it up anywhere you currently are.
the file should be something like this:

#!/bin/bash
"terminalcommand"

---

### Post by Feba on 2007-04-05
worked, thanks!

---

