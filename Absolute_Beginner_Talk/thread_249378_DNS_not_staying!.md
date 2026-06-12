---
title: "DNS not staying!"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by Lunchmeat on 2006-09-02
After a very long strugle to get my system online, i found (thanks to the irc chanel guys!) that I needed to change the dns from my router to my ISP's online dns server.

I have done this both in the relevant text file and in the netwprk manager, but either way, it resets to 192.168.1.1 after about 30 minutes... what can I do to make it stick?

thanks!

---

### Post by TFX360 on 2006-09-02
> **Lunchmeat said:**
> After a very long strugle to get my system online, i found (thanks to the irc chanel guys!) that I needed to change the dns from my router to my ISP's online dns server.

I have done this both in the relevant text file and in the netwprk manager, but either way, it resets to 192.168.1.1 after about 30 minutes... what can I do to make it stick?

thanks!


Open up a terminal

Find your active card. You can check that with

```
sudo ifconfig
```

Edit the interfaces file:

```
sudo nano /etc/network/interfaces
```

and add a line to the end of that card in the interfaces file

```
dns-nameservers xxx.xxx.xxx.xxx
```

Where xxx.xxx.xxx.xxx is the dns server you want to use

For example mine could be: 83.80.1.160


Good luck!

xxx.xxx.xxx.xxx

---

### Post by Lunchmeat on 2006-09-02
thanks, i've done that, hopefully it'll stay in place now. Do you know why it was changing btw?

---

### Post by TFX360 on 2006-09-02
> **Lunchmeat said:**
> thanks, i've done that, hopefully it'll stay in place now. Do you know why it was changing btw?

Could be a timeout somewhere. Maybe even one in your router.

Let me know if this stays!

ps: I will be on vacation on sunday for a week

---

### Post by Lunchmeat on 2006-09-02
I have added the script, but it still resets. I have also set the router to not interfere, and it has always (and still does) worked on other machines...

Any ideas?

thanks,

---

