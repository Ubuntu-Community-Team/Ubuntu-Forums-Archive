---
title: "limewire on edgy"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by abu-fatu on 2006-11-10
i was using limewire on dapper but when i up-graded to edgy i cannot get it to work. i installed it using a rpm file using alien sames as in dapper. does anyone have any experience with this?

---

### Post by taurus on 2006-11-10
Try to run limewire from a prompt/terminal (Appications -> Accessories -> Terminal) to see exactly what the error message is...

```
limewire
```

---

### Post by abu-fatu on 2006-11-10
i get "runLime.sh 44: Syntax error: "(" unexpected (expecting "(" )"

---

### Post by taurus on 2006-11-10
What does your /usr/bin/limewire look like anyway?

```
cat /usr/bin/limewire
```

---

### Post by ron999 on 2006-11-10
Yes abu-fatu
I couldn't get Limewire to run when I upgraded to Edgy.
I solved it by using the beta version 4.13.0 instead.
I downloaded the rpm file from
[http://www.limewire.com/english/content/beta.shtml]("http://www.limewire.com/english/content/beta.shtml")
 then converted it to deb using alien.
It works OK now 8)

---

### Post by abu-fatu on 2006-11-10
thanks ron it worked.

---

### Post by the music man on 2006-11-11
I have the same problem and error, but I didn't upgrade linux, but installed xubuntu 6.10 for the first time. I installed limewire at the same way, with alien. This is my /usr/bin/limewire file:

```
#!/bin/bash
cd /usr/lib/LimeWire
sh runLime.sh
```

---

### Post by ashmew2 on 2006-11-11
after u installed limewire , does it show under the applications group on your Internet Menu ?

---

### Post by Perfect Storm on 2006-11-11
You might killall gnome-panel in ubuntu 6.10 first

---

### Post by taurus on 2006-11-11
> **the music man said:**
> I have the same problem and error, but I didn't upgrade linux, but installed xubuntu 6.10 for the first time. I installed limewire at the same way, with alien. This is my /usr/bin/limewire file:

```
#!/bin/bash
cd /usr/lib/LimeWire
sh runLime.sh
```
Change the last line of your /usr/bin/limewire to look like this.

```
bash runLime.sh
```

---

