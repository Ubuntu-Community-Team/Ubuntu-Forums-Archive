---
title: "How to get terminal to stop pinging."
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by OmnificienT on 2007-06-09
I pinged one of my friends on Hamachi, but now I'd like it to stop. How do I stop the ping command?

---

### Post by diatribe on 2007-06-09
press ctrl+c

---

### Post by Catsworth on 2007-06-09
Hold down Ctrl+C

---

### Post by jonward0690 on 2007-06-09
It should stop when you close the terminal.

---

### Post by Outrunner on 2007-06-09
Well, I think you have to close the terminal. The next time you ping someone use
```

sudo ping -c # address
```

where # is the number of pings as in

```
sudo ping -c 3 bbc.co.uk
```

---

### Post by Catsworth on 2007-06-09
You don't need the sudo command, ping works just fine without it.

---

### Post by Outrunner on 2007-06-09
> **Catsworth said:**
> You don't need the sudo command, ping works just fine without it.

Well, looks like you're right! I swear the last time I tried without sudo it didn't work. I guess I was wrong.

---

### Post by original_jamingrit on 2007-06-09
If you you don't want to close the terminal for some reason, typing in 
```
ps u
```
and then 
```
kill (appropriate process number here)
```
should do the trick.

---

### Post by OmnificienT on 2007-06-09
Ah, thank you.

---

### Post by darkfame on 2007-06-09
If you don't want to bother finding the pid to the ping process or have several ping processing running you want to kill.. simply type: killall ping

---

