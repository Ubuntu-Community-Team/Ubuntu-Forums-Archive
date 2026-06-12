---
title: "Firestarter Automatic detection?"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by KOTAPAKA on 2008-02-19
Hello 
I've just noticed on my startup that next to "Starting firestarter"
The reason seems to be that firestarter does not detect which connection is in use (Wii-Fi or cable in my case). How do I make it detect it by itself?

---

### Post by randy78 on 2008-02-19
Firestarter is just a front-end for IpTables, meaning that you just use it when you want to change a rule.

It isn't like ZoneAlarm or Comodo, where a fancy screen pops up telling you that X application or IP has just been blocked...

No need to worry about it, it's more of a set it and forget it solution.

Hope that explains things ;)

---

### Post by jan quark on 2008-02-19
you can see what process is currently running with this command
```

top
```

start firestarter through the terminal
and see if any error messages will show up

---

### Post by seventhc on 2008-02-19
You might need to make sure it's using the correct connection (eth0 eth1) whatever it may be. I don't have firestarter on my machine so I can't remember exactly where the option is, but if you open firestarter it is a fairly small menu. So it should be easy to find. :)

---

### Post by kpkeerthi on 2008-02-19
To start firestarter
```

sudo /etc/init.d/firestarter start

```

---

### Post by KOTAPAKA on 2008-02-19
I fixed it. I have changed my question now. What can i say i am a newbie :)

---

