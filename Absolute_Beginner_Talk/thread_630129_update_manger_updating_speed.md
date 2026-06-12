---
title: "update manger updating speed"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by siongz on 2007-12-03
hi.. i think i have a problem with my update manager... its downloading speed is extremely unstable... like from 8000B/s to abt 30KB/s.. so.. is the problem with the server or issit with my connection???

---

### Post by jordanmthomas on 2007-12-03
I would say the server.  I had the same problem when I used to use Ubuntu.  You can try to find a better server to use (I found that de.ubuntu.whatever was faster than us.ubuntu.whatever)

However, if this problem happens across different programs (like when you're downloading something in firefox) then it could be your connection.

---

### Post by FakeOutdoorsman on 2007-12-03
Try choosing a new repository server. System -> Administration -> Software Sources -> Ubuntu Software Tab.  Choose the dropdown menu and click "Other...". A list of servers will appear sorted by country.  Test some to see which is fastest or you can try "Select Best Server" which will ping servers and will attempt to pick the fastest for you.  Manually choosing a close mirror server resulted in the best speed for me, especially during new Ubuntu releases.

---

### Post by baxterdog on 2007-12-03
I didn't have any problems, but I tried 'System-->Administration-->Software Sources' and all I got was a blank popup. What is that all about?

---

### Post by siongz on 2007-12-03
thank you... it worked like a charm... :KS

---

### Post by FakeOutdoorsman on 2007-12-03
baxterdog,

Try opening Software Sources in a terminal.  This way you might be able to view any error messages:

```
gksudo software-properties-gtk
```

---

