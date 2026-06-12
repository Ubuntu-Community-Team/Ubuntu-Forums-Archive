---
title: "[SOLVED] display problem, screen problem"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by obscur156 on 2008-01-30
Ok,when i was using a crt monitor i was able to use ubuntu,now that i have change my monitor to a compaq wf1907 lcd,i cant see anything.

When i boot i can enter my name and password but after that,the monitor stays orange and nothing is happening.

Somebody have a clue of what can be the prob?

Thanks ,best regards.

---

### Post by overdrank on 2008-01-30
> **obscur156 said:**
> Ok,when i was using a crt monitor i was able to use ubuntu,now that i have change my monitor to a compaq wf1907 lcd,i cant see anything.

When i boot i can enter my name and password but after that,the monitor stays orange and nothing is happening.

Somebody have a clue of what can be the prob?

Thanks ,best regards.

HI and have you tried to reconfigure you xorg with the new monitor? ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by dcstar on 2008-01-30
> **obscur156 said:**
> Ok,when i was using a crt monitor i was able to use ubuntu,now that i have change my monitor to a compaq wf1907 lcd,i cant see anything.

When i boot i can enter my name and password but after that,the monitor stays orange and nothing is happening.

Somebody have a clue of what can be the prob?

Thanks ,best regards.

You need to reconfigure your system to a compatible refresh rate for your new monitor.

Press CTRL-ALT-F1 at the login screen, then login to the text terminal and:
```
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart
```

---

### Post by obscur156 on 2008-01-30
i cant go to the terminal or tell me how to do it without being able to log to the session.

And thanks for that quick reply OVER :)

---

### Post by overdrank on 2008-01-30
> **obscur156 said:**
> i cant go to the terminal or tell me how to do it without being able to log to the session.

And thanks for that quick reply OVER :)

HI and at the login screen just use alt,ctrl, F1 keys to reach a terminal.

---

### Post by obscur156 on 2008-01-30
thanks dcstar ,will try that.

Best regards

---

### Post by obscur156 on 2008-01-30
Thanks Over,regards.

---

