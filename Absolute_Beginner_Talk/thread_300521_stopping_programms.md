---
title: "stopping programms"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by mendingo84 on 2006-11-15
why doesn't CTRL+c work on my edgy?
and a secondary question. if i would like to reinstall smth, let's say the /etc/ppp/peers file. what would be the proper apt-get command?

---

### Post by LLRNR on 2006-11-15
Hi, you mean your Ctrl+C doesn't work... in which context ? When you try to copy, or when you try to send SIGINTR to a process in a shell ?

To re-install something you first need to uninstall and then install again. So let's suppose your package is called *package_name*, then you'd say in a terminal:
```
sudo apt-get remove package_name
sudo apt-get install package_name
```

Or even better: ```

sudo aptitude reinstall package_name
```

And if it still doesn't work:
```
sudo aptitude purge package_name
sudo aptitude install package_name
```

EDIT - I'm sorry I now see the title of your thread, "stopping programs"
Please post the output of ```
stty -a
```

---

