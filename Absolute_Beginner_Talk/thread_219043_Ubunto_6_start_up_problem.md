---
title: "Ubunto 6 start up problem"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by PeterHubbard on 2006-07-19
I am really new to Ubuntu, I downloaded the live CD yesterday.  

My first install worked well but then I got a message saying that there were 187 updates, I then downloaded them and my machine rebooted itself whilst instaling them.

When I start the machine now it asks for my name and password byt then the cursor sits on a blank screen and nothing happens.

I did try to run the option to repair but and a lot of code was run but then it sits at a probpt with peter-desktop:@ and I have no idea what to d next, I knew I should have bought a bok or something.

Any help will be appreciated.

Best wishes

Peter

---

### Post by MrHorus on 2006-07-19
X is broken somehow.

Type in the username and password that was created when you installed the system - this will allow you to login.

Try typing 'startx' to see if X is indeed broken or just not starting by default.

If it doesn't work or it's knobbled somehow, try checking for residual updates by running apt again.

```
sudo apt-get update && apt-get upgrade
```

Hope this helps.

---

