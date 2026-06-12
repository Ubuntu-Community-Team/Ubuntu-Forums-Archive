---
title: "cannot access certain websites"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by %hMa@?b&lt;C on 2007-10-07
today something weird happened with my home desktop, I can access some websites (search.com, proxify.com (which is necessacary to visit sites taht cannot load)) but cannot access a lot more (google, gmail, ubuntuforums).  the sites just cannot load. I can ping, it get the IP address, but no responses.  the router (actiontec) can ping the sites adn get response, but the computer cant.  It works in a live cd, but to boot from hard drive (ubuntu feisty) it does not.  any help would be appreciated.

---

### Post by MWilliams13 on 2007-10-07
check your blocked sites.

---

### Post by %hMa@?b&lt;C on 2007-10-07
blocked from where?  My router has no blocked sites on it.  I can also access from a live cd, so the router is not the problem.

---

### Post by n3tfury on 2007-10-07
you haven't messed with your hosts file have you?  do you have a static ip for your linux box? is your router wireless? is it secure and have you changed the default password?

---

### Post by wormser on 2007-10-07
It sounds like this might be a DNS issue.  Try pinging by name and ip number.

```
 ping ubuntuforums.org
 ping 91.189.94.186
```

If the ip address works and the name does not then this is a DNS issue.  Go to System> Administration> Network> DNS tab.  Use 4.2.2.2 and 4.2.2.1 as DNS servers.

If it is not get us more information so we can help.

---

### Post by %hMa@?b&lt;C on 2007-10-07
it hangs on both ping name and ip addy.  
it does have wireless (works with laptop attached)
have not messed with anything 
i reset router to factory defaults (it worked coming from box) but still did not work after that.  
it is not to do with DNS, becasue it works with some websites.

---

### Post by n3tfury on 2007-10-08
post your hosts file just for kicks.

/etc/hosts

---

