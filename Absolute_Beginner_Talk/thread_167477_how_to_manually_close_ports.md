---
title: "how to manually close ports"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by rajan on 2006-04-28
Dear Community,
i'm interested in manually closing my ports that i have open. is there a command/utility for this? i only have port 22 open because i have ssh enabled but i'm obviously not using it all the time. the corresponding question is how do i manually open a port? i'm not sure where this would come in handy (i'd take suggestions). i read some online information regarding firewalls, but i can't find the required info. anyone have a good resource to suggest?

thanks

---

### Post by cgjones on 2006-04-28
What are you using currently to open port 22?

---

### Post by rajan on 2006-04-28
i believe it's just the standard openssh program that synaptic has. i'm not at home so i can't check, but if i'm wrong i'll repost. i gather you're suggesting that whatever i use to open the port i should also use to close it? so does this mean there's no way to close port "x" by command? it makes sense that there wouldn't be anything unless someone has specifically programmed a patchwork code.

---

### Post by Jagot on 2006-04-28
This wiki should help:

[https://wiki.ubuntu.com/IptablesHowTo](https://wiki.ubuntu.com/IptablesHowTo)

---

### Post by cgjones on 2006-04-28
I was just curious if we were dealing with a default install. I would recommend checking out this link.
[http://help.ubuntu.com/starterguide/C/ch03s07.html#firestarter](http://help.ubuntu.com/starterguide/C/ch03s07.html#firestarter)
This will show you how to install a graphical firewall tool, called Firestarter, to configure a firewall. Once you get it installed, it's pretty easy to set up.

---

### Post by rajan on 2006-04-29
iptables looks to be exactly what i need. also i had a look at firestarter a while ago, but i couldn't really find anything regarding the way it works (i could only find information about the gui). maybe it's time for me to look again. from what i've read however, i'm just being paranoid because the only way people can hack your comp if you're using linux (provided you aren't hosting a website) is if they crack your passwd. again, that's just what i've gleaned from the ubuntu manual and other conversations on here, but there definitely doesn't seem to be the terrible coding problems in windows. anyways, thanks for the help and sorry for the late responses.

---

