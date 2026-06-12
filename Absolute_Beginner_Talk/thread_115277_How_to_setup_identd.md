---
title: "How to setup identd"
date: 2006-01-10
forum: Absolute Beginner Talk
---

### Post by Prozzy on 2006-01-10
Hey...

I need to setup some identd server thing.

I've tried to search a few things but cant really see how to do it.

I would like to setup something where im able to set the identd reply myself.

ive installed pidentd but i cant figure out how to set a userdefined reply.

- Greets Prozzy

---

### Post by Prozzy on 2006-01-10
Okay... i did some more reading and have found that its probably oidentd i need.

Ive installed oidentd, the port 113 is forwarded in my router.

This is my /etc/oidentd.conf

```
default {
	default {
             	deny spoof
		deny spoof_all
                deny spoof_privport
		allow random
		allow random_numeric
		allow numeric
		deny hide
	}
}

user rasmus {
    default {
        allow spoof
        allow spoof_all
        allow random
        allow hide
        allow numeric
        }
}

```

and i made a ~/.oidentd.conf that got this info

```

global {
reply "myidentd"
}

```

i edited the /etc/oidentd_masq.conf, added the line
```
 192.168.0.100 identd UNIX 
```

But it still seems like it doesnt work :(

Any idea what i did wrong?

---

