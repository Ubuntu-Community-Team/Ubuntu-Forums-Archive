---
title: "safe remove"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by dwisianto on 2007-11-08
I am wondering how to write a bash script for "safely remove" a file/directory to a pre-selected junk directory
instead of actually removing those files.

---

### Post by Dr Small on 2007-11-08
```

#!/bin/bash
mv -R /path/to/directory/ /path/to/junk/

```

---

### Post by Harpoon on 2007-11-08
With respect to the function of "(re)moving files to a junk directory" I would point out that this is precisely what "deletin" files using the .Trash folder does.  Trashing the file moves it to the .Trash directory, and from there you can use it, copy it, and ultimately actually delete it permanently.

---

### Post by dwisianto on 2007-11-10
yeah, I am just wondering if there is any shell command to actually do the process
to "(re)moving" the file to .Trash or the junk directory.

thank you for the response.

---

### Post by finer recliner on 2007-11-10
as stated by dr. small:

```

mv -R filename ~/.Trash

```

this will move the file to your Trash.

there is no built-in command that will make this any easier. 'rm' will permenatley delete a file (so you dont want to use it in this scenario). 'mv -R' will recursively move a file/directory to the new location you specify (your trash folder in this case)

enjoy

---

### Post by dwisianto on 2007-11-10
at first, I thought someone out there have some sort of tricks I am not aware of.
I guess there is not any.
thanks for the response.

---

