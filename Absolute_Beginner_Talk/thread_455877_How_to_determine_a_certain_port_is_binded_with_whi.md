---
title: "How to determine a certain port is binded with which program"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by NeoRc on 2007-05-27
I wanna run a webserver, but a port that used by the server is binded with another program. I don't wanna change it, so I wanna know which program it is.

---

### Post by ruy_lopez on 2007-05-27
```
sudo netstat -atp
```

This'll show the listening network connections, the final column lists the processes that are binding to the sockets.

Close your browser before running it, otherwise the output will be flooded with your web-connections.

---

