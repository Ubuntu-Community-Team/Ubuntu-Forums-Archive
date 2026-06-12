---
title: "Slow Download in Ubuntu"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by justincormier on 2007-04-05
Anyone else have slow download speeds in Ubuntu?  I googled it before i asked for help and didnt find much... How can i fix this.. 

TIme Warner Cable
Linksys Router
Netgear Wireless card 

Internet was super speedy on windows.. dont know why netgear/linkys would clash on Ubuntu..

any help would be apreciated. thanks!

Justin

---

### Post by halitech on 2007-04-05
have you turned off IPv6 yet?

in the address bar, type

```
about:config
```

and turn off IPv6. Also,  check this setting for network.http.pipelining.maxrequests and try setting that up to 32, then restart Firefox and check again

---

### Post by justincormier on 2007-04-05
couldnt find IPv6... but found the other...

is it odd i couldnt find that?

---

### Post by halitech on 2007-04-05
wierd, I found it when I used the filter to find just ipv6. try this and see if you can find it

network.dns.disableipv6

---

