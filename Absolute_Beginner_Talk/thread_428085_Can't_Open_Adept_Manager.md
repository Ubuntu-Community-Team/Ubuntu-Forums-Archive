---
title: "Can't Open Adept Manager"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by ubuntu27 on 2007-04-30
Hello guys!
I am new to **K**ubuntu. I want to open Adept but Can't it says cant have conversation with su. 

Look at the screenshot.

Any ideas how to fix this?

---

### Post by mikeyphi on 2007-04-30
I don't use Kubuntu but my understanding is that you should access Adept Manager through the K menu and the system folder?

---

### Post by theredcross on 2007-04-30
```
sudo adept_manager
```
in the konsole, see if that works any better. Or just try
```
sudo apt-get update
```
At least it'll update, and let us know if its an apt problem, which it doesn't seem to be.

---

### Post by ubuntu27 on 2007-04-30
Thanks guys. Problem solved. I restarted the computer completely, and the problem was gone :)

---

