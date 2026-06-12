---
title: "MacBook Pro 5,4 Tweaking help"
date: 2009-09-25
forum: Apple Hardware Users
---

### Post by Ravernomina on 2009-09-25
Hello all, as you all know i have Ubuntu On My Mac :). Now i just need some Help tweaking it.

UniBody MacBook Pro mid 2009
**_Problems:_**

[U][B]Adjusting Screen Brightness.
Making Backlit keyboard Off when turning computer on
Adjusting Fan Speed.
[/B][/U]
If anyone knows how to do any of these could you please tell me? THANKS!!!
       Ravernomina 

:popcorn::popcorn::popcorn:

---

### Post by Bachstelze on 2009-09-25
[This]("https://help.ubuntu.com/community/MacBook5-1/Jaunty") might help.

---

### Post by Ravernomina on 2009-09-25
Alright i got my Fan Problem Solved :)

used this command

```
echo 4000 > /sys/devices/platform/applesmc.768/fan1_output
```

---

### Post by buntuLo on 2009-09-25
that command isn't very safe, you'd better change only the minimum value, so that the fans can spin faster than your setting if needed:
```
echo 4000 | sudo tee /sys/devices/platform/applesmc.768/fan1_min
echo 4000 | sudo tee /sys/devices/platform/applesmc.768/fan2_min
```

---

### Post by Ravernomina on 2009-09-25
Thanks you For that one it works a lot better (:

---

