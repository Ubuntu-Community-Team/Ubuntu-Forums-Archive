---
title: "Wireless Network Switching"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by Cloey64 on 2007-10-10
At school we have multiple wireless networks, all connecting to the same overall network, but having different names such as "Campus" and "Dorms". When I am in class working on my computer, I am connected to the "Campus" wireless routers, and sometimes class ends and I don't want to shut down so I just close the screen and go back to my dorm. The problem comes when I open my computer back up again. I put in my password and everything pops back up again, but my wireless starts looking for "Campus" and instead of realizing it can't find "Campus" and start looking for "Dorms", It won't even switch to wired if I plug it in. It just keeps spinning its wheels until I restart it, then it finds "Dorms". Is there any way to make it more intelligent in switching networks after coming back from sleep? Restarting the computer to reconnect to the wireless kind of defeats the purpose of just putting it to sleep at the end of class so I can work on stuff when I get back to my dorm.

Ps. When I am in my dorm, it can easily switch between wired and wireless, so it does know how to switch networks.

---

### Post by jfinkels on 2007-10-11
Let's say for the sake of example, the ESSID (the 'name') of the network is "Dorms" and your wireless network interface is called 'eth1'. To set the wireless network to which you want your interface to connect, type in the terminal:```
sudo iwconfig eth1 essid Dorms
``` To release and renew your lease with the network, type the following:```
sudo ifdown eth1 && sudo ifup eth1
```

Instead of doing this everytime you change networks, you can put this in a script (a text file called "reconnect.sh" or whatever you want to name it) that looks like this:```

#!/bin/bash
iwconfig $1 essid $2
ifdown $1 && ifup $1
exit 0

```
make it an executable file:```
chmod +x reconnect.sh
```

And run it by typing:```
 sudo ./reconnect eth1 Dorms
```

---

