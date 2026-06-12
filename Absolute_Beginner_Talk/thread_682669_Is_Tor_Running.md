---
title: "Is Tor Running?"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by Hoom@n on 2008-01-30
Hello!
First I've to tell I read [https://help.ubuntu.com/community/TOR](https://help.ubuntu.com/community/TOR) and I couldn't find the answer plus that I installed it from [http://ubuntuforums.org/showthread.php?t=476831](http://ubuntuforums.org/showthread.php?t=476831)
I installed tor, privoxy and torbutton. When tor button is enable I can surf the web with another ip and when it's disabled there is no problem. So everything is ok. But now the problem:
How can I see that is tor running or not? I mean even when tor is enabled I can't see its process in system monitor or there is no folder or file named tor in my computer. I just want to see when is it running and how can I uninstall it if neede?
Thank you.

---

### Post by frodon on 2008-01-30
To stop it :
```
sudo /etc/init.d/tor stop
```

To see if it is currently running (should be the case by default) you can check if a process with the word tor is running, the following command will return you all the active processes containing the word tor :
```
ps -aef | grep -i tor
```

---

### Post by Hoom@n on 2008-01-30
Thank you. I could stop and start it again. But I couldn't get how can i use the second command. (it gives me a lot information which i don't know what to do with!) Please tell me how to use it!

---

