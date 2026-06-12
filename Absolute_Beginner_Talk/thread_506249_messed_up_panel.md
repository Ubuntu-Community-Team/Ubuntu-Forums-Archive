---
title: "messed up panel"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by AJS302 on 2007-07-21
i am quite new to linux and whilst experimenting i managed to mess up the top panel, is there any way i can reset it to default?

---

### Post by Waappu on 2007-07-21
Hi

Try this.

Type in terminal ```
mv ~/.gconf/apps/panel ~/panel_old
```log out and then back in

---

### Post by AJS302 on 2007-07-21
thank you, it worked perfectly

---

### Post by Waappu on 2007-07-21
Hi

Great. Now if you want you can delete complety those old config. Type in terminal```
rm -r ~/panel_old
```

---

