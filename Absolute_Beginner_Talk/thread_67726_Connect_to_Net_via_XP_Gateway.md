---
title: "Connect to Net via XP Gateway?"
date: 2005-09-21
forum: Absolute Beginner Talk
---

### Post by Paul-Henri on 2005-09-21
Hi all,

I'm running Ubuntu 5.04 on a dual boot with XP Pro. My machine is networked to a housemates & his machine is the Internet Gateway.

Can I connect to the net from Ubuntu via this setup? I've seen a few posts about doing it the otherway (ie Ubuntu as the gateway) but thats not an option.

Any help greatly appreciated :)

PS I am currently downloading the 5.10 preview (both U & K versions) so will probably be running one of them by the time I read any replies...

---

### Post by mlomker on 2005-09-21
I believe you just have to set an environment variable pointing to the server and the port number that the proxy server is running on.  I don't know if it's going to work connecting to a machine that is connected to the other, though...you really need your own connection to the gateway machine.

Add this command toward the bottom of the /etc/init.d/bootmisc.sh file and that should do it.  You'll have to substitute in the proper IP address for my.proxy.server and the proper port number, of course.

```

export http_proxy=http://my.proxy.server:3128/

```

---

