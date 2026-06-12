---
title: "Network initialization problem"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by mahiyar on 2007-12-16
My internet connection is a 256Kbps lan through ethernet. When setting up using pppoeconf I have given the connection to start at boot, only a few time it starts. The next thing is that I keep on using the command >>sudo pon dsl-provider. I keep on doing that for maybe about 10 mins or 15 mins after which the internet starts. On th plog command these are the various types of errors >login incorrect (though the same log in is later ok) > Bad descriptor or file name > something like "I dont like you go away".
The same connection starts in a jiffy in windows. Is there anything wrong in my set up or anything additional that I can do to make connection faster?

---

### Post by cmnorton on 2007-12-16
You'll need to post some log output here. /var/log/syslog is a good place to start. In addition, which version of Ubuntu is this? Is Network Manager available. If it is, why are you running ppoeconf and not using NetworkManager?

---

### Post by mahiyar on 2007-12-17
Thanks for the reply. As soon as I get home from work I will post the syslog as you suggested. I'am running Ububtu Gutsy 7.10. Isn't pppoeconf a part of network manager? What other network managers are there which do not have pppoeconf at their background?

---

### Post by mahiyar on 2007-12-18
The problem disappeared as inexplicably as it had come. Hmm I will have to study network and how it works to get t o the bottom of this. Can anybody suggest some good sites for that?

---

