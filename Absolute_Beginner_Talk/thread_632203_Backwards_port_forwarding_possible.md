---
title: "Backwards port forwarding possible?"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by arijarot on 2007-12-05
[Forgive me if I use these concepts incorrectly]

I would like to "port forward" backwards. What I'm wondering is if it's possible to not change any of the settings on the router but, maybe?, ssh tunnel backwards through another port or something? 
I'm trying to make myself connectable for torrent uploads, but it says that I need to enable port forwarding as my router (external IP) is dropping my machine's (internal IP) connection attempts from  peers who are trying to download my torrents. Now I've read that I need to forward my routers port 6881 (e.g.) to my internal IP, but I can't change the routers settings (not admin). 
So, back to my question: Is it possible to "port backwards" on my machine to the router through ssh tunneling or something, I dunno?

Any suggestions would be greatly appreciated!

Thanks

-A

---

### Post by HermanAB on 2007-12-05
Read the ssh man page on -L and -R.

Cheers,

H.

---

### Post by arijarot on 2007-12-05
> **HermanAB said:**
> Read the ssh man page on -L and -R.

Cheers,

H.

Thank you :) hopefully this'll work!

---

### Post by psusi on 2007-12-05
No, you have to fix the router to forward some ports to you, or if the router supports UPnP and you use a bt client that does as well, that will take care of the forwarding for you automatically.

---

### Post by arijarot on 2007-12-05
> **HermanAB said:**
> Read the ssh man page on -L and -R.

Cheers,

H.

So, I'm not sure if I understand...

ALL I have to do is :

```
#ssh -L [127.0.0.1:]6881:192.168.2.5:6881
```
```
#ssh -R [127.0.0.1:]6881:192.168.2.1:6881
```

and enable server’s GatewayPorts option (see sshd_config(5))?

Thanks

---

### Post by psusi on 2007-12-05
SSH is not going to help you unless you have ssh access to the router, which most don't even support, and if you have ssh access you should be able to just forward the ports normally.

---

### Post by arijarot on 2007-12-05
> **psusi said:**
> SSH is not going to help you unless you have ssh access to the router, which most don't even support, and if you have ssh access you should be able to just forward the ports normally.

Oh, well that's disappointing! Thanks for letting me know...

---

### Post by Dr Small on 2007-12-05
> **psusi said:**
> SSH is not going to help you unless you have ssh access to the router, which most don't even support, and if you have ssh access you should be able to just forward the ports normally.
You could have SSH access to your router if your router was a pc you built as a firewall and had openssh-server on it ;) But, like you said, most don't, expecially if it's a store bought one.

Dr Small

---

