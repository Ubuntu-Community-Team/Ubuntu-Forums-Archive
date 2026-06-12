---
title: "In Browser Media Player (like quicktime)"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by tartarian on 2006-10-15
In windows, quicktime will play videos in the browser. I was wondering whether this was possible in Firefox, Kubuntu? Thankyou!

---

### Post by mejy on 2006-10-15
> **tartarian said:**
> In windows, quicktime will play videos in the browser. I was wondering whether this was possible in Firefox, Kubuntu? Thankyou!

If you have not done so already, install the Win32 codecs:

```
wget -c http://packages.freecontrib.org/ubuntu/plf/pool/dapper/non-free/w32codecs_20060611-1plf1_i386.deb
sudo dpkg -i w32codecs_20060611-1plf1_i386.deb
```

Then, installing mozilla-mplayer and it's dependancies should do the trick:

```

sudo apt-get install mozilla-mplayer
```

---

### Post by motang on 2006-10-16
> **tartarian said:**
> In windows, quicktime will play videos in the browser. I was wondering whether this was possible in Firefox, Kubuntu? Thankyou!

This [link]("http://www.ehomeupgrade.com/entry/2663/how-to_get_full") will help you out.

---

