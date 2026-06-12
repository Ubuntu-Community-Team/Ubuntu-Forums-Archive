---
title: "Cannot install console-setup - problem with locales?"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by mundus on 2007-04-04
Ok, so I decided to update from Dapper to Edgy, and things started to go wrong from the beginning. Anyway, no things are in quite a good shape, I just cannot start X.. :) 

To my understanding the problem is that I don't have ubuntu-minimal installed. When trying to install ubuntu-minimal script /var/lib/dpkg/info/console-setup.config is run. (correct me if I'm wrong.) And this is where the problem starts.

The console-setup.config fails on line 936 - unexpected EOF while looking matching '"'

Script's lines 935-937 are:
```

if which locale > /dev/null; then
  eval 'locale'
fi

```

I'm not quite sure, but as the error claims that character " was not found I guess there is something wrong with my locals. They look like this:

```

LANG=C
LANGUAGE=fi_FI:fi:en_GB:en
LC_CTYPE="fi_FI@euro","
LC_NUMERIC="fi_FI@euro","
LC_TIME="fi_FI@euro","
LC_COLLATE="fi_FI@euro","
LC_MONETARY="fi_FI@euro","
LC_MESSAGES="fi_FI@euro","
LC_PAPER="fi_FI@euro","
LC_NAME="fi_FI@euro","
LC_ADDRESS="fi_FI@euro","
LC_TELEPHONE="fi_FI@euro","
LC_MEASUREMENT="fi_FI@euro","
LC_IDENTIFICATION="fi_FI@euro","
LC_ALL=fi_FI@euro",

```

The last ", bit wonders me, I guess that breaks the script. I just havent figured out how to fix that problem. I reinstalled the locales, but that didn't help. Neither did removing console-setup and reinstalling it.

Any ideas? Thanks!

---

### Post by Feba on 2007-04-04
> LC_ALL=fi_FI@euro"

I don't know much about coding, but it looks like that needs to be 

> LC_ALL="fi_FI@euro"

It says " not found, and there's no " there despire it being in the other ones.

Try editing it in gedit or nano

---

### Post by mundus on 2007-04-04
Hey, thanks! I missed that. I'll try editing /etc/environment. 

Thanks, I hope it helps.

---

### Post by mundus on 2007-04-06
Thanks, I used export LC_ALL="fi_FI@euro" to fix the problem.

---

