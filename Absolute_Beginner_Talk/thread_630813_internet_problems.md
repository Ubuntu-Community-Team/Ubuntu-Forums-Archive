---
title: "internet problems"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by letitworknow on 2007-12-03
im not able to connect to the internet through my desktop which uses ubuntu. i went into the comand promt on my laptop used ipconfig to get the ip address, subnet and gateway. Then on my desktop went into manual config; under wired connection; property i canged the setting to static ip and used the address from my lap top and i still cant connect. can i iprelease an renew like on windows? that is how i got my laptop to work but my terminal says "command not found" (i tried ifrelease also)

---

### Post by kelbizzle on 2007-12-03
If you have a Cable modem, and your just swapping the Ethernet back and forth _without power cycling the modem_ Then we may have found the cause to your problem. If not read along to the commands to release and renew your ip. If you have a cable modem you should know...That Most cable modems clone the Hardware address (mac address) of the last machine connected to it. So if you just hot swap the Ethernet cable without power cycling the modem. It still sees the first computer and will refuse to work with the newly connected computer. 

 First change the setting back to configure automatically. With the Ubuntu machine connected  Turn off the modem. Some Internet/voip modems have a battery be sure to remove that too if yours has one. After leaving the modem off for a minute or so plug the power back into it. If your still not able to connect to the Internet. Try the following command to release and renew your ip

```
 ifdown eth0 && ifup eth0
```

---

