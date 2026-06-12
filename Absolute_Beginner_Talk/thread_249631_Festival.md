---
title: "Festival"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by tjb891 on 2006-09-02
Can anyone explain to me how to use festival? For example how to read this website or text I highlight on a website so I don't get eyestrain?

---

### Post by Burke on 2006-09-03
Try: 

```

sudo apt-get install lynx

lynx -dump [insert_url_here] | text2wave -scale 1.5 -F 8000 -o festival_tmp.wav && play festival_tmp.wav && rm festival_tmp.wav

```

If you want, you can make a script to do this for you:

Make a new file called speak_page or whatever you want. 

Paste in:
```

#!/bin/bash
lynx -dump "$1" | text2wave -scale 1.5 -F 8000 -o festival_tmp.wav && play festival_tmp.wav && rm festival_tmp.wav

```

then run: 
```

sudo mv speak_page /usr/bin
sudo chmod a+x /usr/bin/speak_page

```

now you can go:
```

speak_page "http://digg.com"

```
...and it will read the page to you.




As you can see, it's not quite as user-friendly as the Microsoft equivalent ;)

---

