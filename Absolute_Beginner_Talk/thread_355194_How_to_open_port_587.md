---
title: "How to open port 587"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by pcflunkies on 2007-02-06
I am having problems sending mail, I just setup my email using evolution, I can recieve, but not send. I am not sure where or how to see what ports are open as well as how to open a port.

Any help is much appreciated.

Just incase I am using
smtp.1and1.com
"Server requires authentication" is checked
No encryption
Plain "Authentication" (I have also tried Login which are the only two types available after I click the "Check for Supported Types" button)

---

### Post by m.musashi on 2007-02-06
I can't help you with the email as I don't use it (I mean I use web mail). I'm not sure if ports are going to be the solution to your problem but I guess it's worth a try. There are a couple things we need to know - or at least you will need to know. Are you using a router or any kind of hardware firewall? If so, you will need to know how to adjust the settings of the firewall or router. A common method is to use a web browser and type in the setup page IP address. 192.168.1.1 is a common one for Linksys. I don't know about others. You may also need to change the local software firewall. Firestarter is a nice GUI for the built in firewall. Install it if you haven't.

```
sudo apt-get install firestarter
```

It isn't necessary but if you want to make changes to ports it's the easiest way.

Once installed you can go to the policy tab and add a port to allow traffic.

 Again, I'm not sure if this is what you need to do. Perhaps someone else can point you in the right direction.

---

### Post by pcflunkies on 2007-02-06
I got Firestarter installed, but How do I enable / disable ports. I can only use "IP, host or network"

---

### Post by m.musashi on 2007-02-06
I uninstalled fireworks so I'm going from memory here (it seemed to be slowing down my internet - I'm still trying to figure that out). Anyway, there is a tab called policy or policies. On that tab are two sections - one for outbound and one for inbound. Click the appropriate one and then choose to add rule. In the rule tool that pops up, type the port number and a name. Close and click the apply rule button near the top. That should do it. Let me know if I got something wrong. I can always intall it again if I need to.

---

### Post by m.musashi on 2007-02-07
Actually, since you are having trouble sending, you really shouldn't need to do this. There is an outbound policy option for either blacklisting or whitelisting. If you set it to blacklist, it will allow all outbound traffic unless you specifically add something to block.

---

