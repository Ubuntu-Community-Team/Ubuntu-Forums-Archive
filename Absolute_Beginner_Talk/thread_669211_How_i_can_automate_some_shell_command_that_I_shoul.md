---
title: "How i can automate some shell command that I should enter every time?"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-01-16
Hi
Thank you for reading my post
I need to do following things everytime i need to use some specefic application:

1-in my own user, open a terminal and enter
```

xhost +local:user2

```

2-open another terminal and 

```

su user2

```

and then in the same terminal which execute the above command

```

export DISPLAY=:0
/bin/bash

```

Everytime I restart the linux i must do this, I will be happy to learn how i can automate this.


thank you.

---

### Post by nem75 on 2008-01-16
Create a script containing:

```
#!/bin/sh

xhost +local:user2
sudo -u user2 export DISPLAY=:0
sudo -u user2 /bin/bash
```

Haven't tested it, but the basic idea should work.

---

### Post by legolas_w on 2008-01-16
I want to put it into the startup script, I think sudo will need password in order to execute, wont it?

Thanks

---

### Post by bodhi.zazen on 2008-01-16
what are you trying to do exactly ?

If you are using sudo you can configure it by running ```
sudo visudo
``` and adding

> env_keep+="DISPLAY HOME XAUTHORIZATION"

to the "defaults" line

---

