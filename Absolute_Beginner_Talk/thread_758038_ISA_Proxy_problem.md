---
title: "ISA Proxy problem"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by Arazu on 2008-04-17
"407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied."

That is whenever Ubuntu tries to update anything. I can get out with Firefox. I've done some searching and what little I've found didn't work. I am the server admin so if I need to make a change there it's possible.

Hopefully someone knows a way around this. Ubuntu is basically useless if I can't get this solved. And that would suck.

Thanks in advance.

---

### Post by Arazu on 2008-04-18
Bump.

Obviously Ubuntu isn't sending any credentials to ISA so the requests are rejected. I've added a username/password everywhere I can find.

Please help.

---

### Post by quirks on 2008-04-18
1. How did you manage to get out with Firefox, i.e., how do you authenticate there?
2. How are users authenticated, form-based login/HTTP Basic authentication/NTLM/Kerberos?

quirks

---

### Post by quirks on 2008-04-18
No matter what your answer to my previous post is, you might want to try out what I found here (if you haven't already): [http://ubuntuforums.org/archive/index.php/t-29159.html](http://ubuntuforums.org/archive/index.php/t-29159.html)

quirks

---

### Post by Arazu on 2008-04-18
> **quirks said:**
> 1. How did you manage to get out with Firefox, i.e., how do you authenticate there?
2. How are users authenticated, form-based login/HTTP Basic authentication/NTLM/Kerberos?

quirks

1. In Firefox I just put in the proxy ip:port. The ISA server still tells Firefox to prompt me for a username/password when I first load a page. That's typical of any machine not running an OS that can log into the network (Mac, XP Home for our one crappy machine that I don't want to upgrade, Vista Home for personal laptops, etc.).

2. Anyone logged into an XP Pro machine is automatically given access if they are a member of the Internet Users group. I guess that would be Kerberos? If it's not an OS that is capable of network login (again Mac, Vista Home for personal laptops, etc.) then the server will prompt for a login. The problem is that if the OS makes a request there is no login prompt.

Since Ubuntu is making the request ISA just says "I don't know you. Buh bye."

I'm checking your link right now.

Thanks! I know this is possible, I just need to figure out how. It just takes time. Shoot, it took me 5 hours of Google abuse to fix my acpi issue but now Ubuntu can actually power off my machine.

---

### Post by Arazu on 2008-04-18
Per your link I created /etc/apt/apt.conf.d/01proxy and the contents are as follows:

```
Acquire::http::Proxy "http://username:password@000.000.000.000:8080";
```

I still get the error when I run sudo aptitude update.

---

### Post by quirks on 2008-04-19
I'm not sure if the following is different from adding the proxy to the /etc/apt/apt.conf.d/01proxy config file, but it is worth giving it a shot:

1. Go to System -> Administration -> Synaptic Package Manager.
2. In Synaptic, go to Settings -> Preferences.
3. Switch to the Network tab and enter the proxy settings. You also have the option to enter a username and password to authenticate to the ISA server.

quirks

---

### Post by renezito on 2008-06-12
Hi,
  I tried configuring my proxy (sistema/preferencias/proxy de la red) and it doesn't work for me. Then I try what you post here (administracion/synaptic/preferences), network tab... entered the information, but it doesn't work :(
  The result:

Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) hardy-proposed/universe Packages
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) hardy/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

can you or somebody help me?
Thanks =)
P.D.: Sorry for my english, I speak spanish :D

---

### Post by renezito on 2008-06-13
It's OK now. I had configured the Server in Chile for "software source" in System/Administration.  Now I set to "Principal Server" and when I try sudo apt-get update it download without problems. I supposed it was a problem with the cl.ubuntu....

---

