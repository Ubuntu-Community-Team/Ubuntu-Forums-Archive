---
title: "Non-US settings"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by Anders J on 2008-02-23
I just installed a new printer (HP) and it worked like a charm. But this now brings up an orl problem again. A lot of Gnome programs as well as Gimp defaults printer settings to Letter, which makes the network printer to stop processing waiting for Letter paper (which is never going to happen).

This is probably some inability from me, but I am convinced there is somewhere a "global" setting that controls default paper format, date and time formats etc. 

I have convinced Thunderbird to display date/time as yyyymmdd hhmmss (pretending to be Danish) as well as Open Office is properly set to A4.

---

### Post by mali2297 on 2008-02-23
In the terminal. check
```

cat /etc/papersize

```
This should say **a4**. If not, correct it with
```

echo a4 | sudo tee /etc/papersize >/dev/null

```

EDIT: Also check
```

locale

```

---

### Post by Anders J on 2008-02-23
Thanks!

Paper size A4

locale produces:

```
LANG=en_DK.UTF-8
LC_CTYPE="en_DK.UTF-8"
LC_NUMERIC="en_DK.UTF-8"
LC_TIME=en_DK.UTF-8
LC_COLLATE="en_DK.UTF-8"
LC_MONETARY="en_DK.UTF-8"
LC_MESSAGES="en_DK.UTF-8"
LC_PAPER="en_DK.UTF-8"
LC_NAME="en_DK.UTF-8"
LC_ADDRESS="en_DK.UTF-8"
LC_TELEPHONE="en_DK.UTF-8"
LC_MEASUREMENT="en_DK.UTF-8"
LC_IDENTIFICATION="en_DK.UTF-8"
LC_ALL=

```

I guess that is as it should and it should then not behave as it does, right?

---

### Post by mali2297 on 2008-02-24
> **Anders J said:**
> 
I guess that is as it should and it should then not behave as it does, right?


So you've got English language but Danish locale set (..and live in Stockholm)?

Check out this web page:
[http://myy.helia.fi/~karte/english_in_finland_on_ubuntu.html](http://myy.helia.fi/~karte/english_in_finland_on_ubuntu.html)
(It concerns English/Finnish but your problem should be analogous.)

---

### Post by Anders J on 2008-02-24
Tack! 

I would not consider running a Swedish desktop since support activity as global. I have alsp experience from a Swedish ubunui installation and the translations were not always very good.

It is also not in all cases a good idea to have the "," as the decima delimiter, since most documentation I prepare is in English anyway so this will be a problem regardless of which delimiter is used.

I will have a close look at the link You submitted.

---

