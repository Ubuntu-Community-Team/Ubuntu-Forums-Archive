---
title: "how would i go about installing this?..."
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by Bleak Outlook on 2007-07-04
> ati-driver-installer-8.38.6-x86.x86_64.run

if you could give "copy and paste" commands i'd be very greatfull

---

### Post by Malibu Illusion on 2007-07-04
Use this:

```
chmod +x ati-driver-installer-8.38.6-x86.x86_64.run
```

Then:

```
sudo sh ati-driver-installer-8.38.6-x86.x86_64.run
```

---

### Post by Bleak Outlook on 2007-07-04
thanks for your quick reply

should it be in any specific folder? as its on my desktop and the terminal can not see it

all i get is this..

```

chmod: cannot access`ati-driver-installer-8.38.6-x86.x86_64.run':No such file or directory

```

---

### Post by Paul820 on 2007-07-04
You need to type: cd /home/yourusernamehere/Desktop

---

### Post by Malibu Illusion on 2007-07-04
Make sure you actually navigate to the "Desktop" directory via the CLI where it resides before issuing those commands.

```
cd ~/Desktop
```

---

### Post by Bleak Outlook on 2007-07-04
thanks that worked a treat

---

