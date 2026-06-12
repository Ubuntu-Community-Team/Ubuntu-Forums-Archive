---
title: "Updating Repositories"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2007-07-21
i was updating repositories but the connection broke, now when i tried:

```


shoaibi@Golden-Eagle:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory


```

the result what i got is also shown.....

i tried again and again, and got same response, i restarted and it was okay then, but again the connection breaks, and i start to get this, is there a way to avoid the Error without restarting machine?

---

### Post by ddrichardson on 2007-07-21
Yes if it isn't running delete the lock file:

```
sudo rm /var/lib/apt/lists/lock
```

---

### Post by Kralizec on 2007-07-21
Is the terminal command the only thing you're using to update? Because problems arise if one has Synaptic Package Manager open while trying to update from terminal. There might also be some other application using the file at the time. List some of the applications you're using and I'll look into them to see if they could be causing the problem.

---

