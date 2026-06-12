---
title: "Learnig ubuntu"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by joseps on 2008-02-03
I am new to linux or ubuntu. I downloaded it and install it to learn how to use it. It is running and I am interested in running boinc projects. Unfortunately, when I downloaded to install it, I get this message:  "Could not open the file /temp/boinc_5.10-28-i686-pc-linux-gnu.sh. gedit has not been able to detect the character coding. Please check that you are not trying to open a binary file"
Both character coding 1) Current Locale (UTF-8)   and  Western (iso-8859-15)  fail. 
I am at a loss. I do not know whether to continue trying to learn Ubuntu. 
Currently I am running Microsoft OS IN my 5 computers I run Boinc projects daily 14/7.
I  do not know if any one is willing to give me some advise. But I need help. Frustrated, Thanks a lot for this post to your forum. joseps :(

---

### Post by spiderbatdad on 2008-02-04
This was actually a mispost intended for another thread. I only returned here when I  noticed this thread indicated I had posted here. I wondered why I would have posted here. I see it was a mistake.

---

### Post by jordanmthomas on 2008-02-04
[COLOR="Silver"]> **spiderbatdad said:**
> removed old quote since it's irrelevant

HUH?  How is this related to the OP's problem?[/COLOR]

Anyway, here's your problem.
Odds are, the file has not been made executable.  Move the file onto your desktop (just to make this easier, as you said it was in /temp, and not /tmp)
Then, open a terminal.
```
cd ~/Desktop
chmod +x boinc_5.10-28-i686-pc-linux-gnu.sh
sudo ./boinc_5.10-28-i686-pc-linux-gnu.sh

```
You don't need to use sudo there if the program can be installed without root access being needed, but it likely needs it.

Opening the file in gedit (a text editor) won't run the file.

---

### Post by spiderbatdad on 2008-02-04
previous was a mispost intended for another thread.

---

