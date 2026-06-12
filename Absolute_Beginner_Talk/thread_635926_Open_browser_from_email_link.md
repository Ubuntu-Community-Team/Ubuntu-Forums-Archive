---
title: "Open browser from email link"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by TouchuvGrey on 2007-12-09
When i click on a link in an email ( Thunderbird 2.0.0.9 ) it opens
the link in a terminal. I want it to open my browser ( Firefox 
2.0.0.11 ) what do i need to do to make this happen ?

---

### Post by Delvien on 2007-12-09
> **TouchuvGrey said:**
> When i click on a link in an email ( Thunderbird 2.0.0.9 ) it opens
the link in a terminal. I want it to open my browser ( Firefox 
2.0.0.11 ) what do i need to do to make this happen ?

Should just be able to right click it and select "Open in a browser" (wording might be different.)

---

### Post by erfahren on 2007-12-09
That's odd. See what the default browser is set to in System > Preferences > Preferred Applications.

the command in there should be:
```

firefox %s

```

---

### Post by TouchuvGrey on 2007-12-09
> **erfahren said:**
> That's odd. See what the default browser is set to in System > Preferences > Preferred Applications.

the command in there should be:
```

firefox %s

```

   That did it, thank you.    :popcorn:

---

### Post by erfahren on 2007-12-09
if you haven't come accross this site yet you may find it helpful
[http://www.linuxcommand.org/writing_shell_scripts.php](http://www.linuxcommand.org/writing_shell_scripts.php)

---

