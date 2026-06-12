---
title: "Desktop icons when server connection is set-up"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by jd65pl on 2006-09-18
Hello,

When I set-up a server connection an icon is dumped on my desktop. I don't want it there but I want the server shown on the places list still.

Is there anyway I can get shot of these icons?

J

---

### Post by Poeffie on 2006-09-18
I think that problem is caused by using desktop nr 1 or 0 (wich doesnt include background & desktop settings)
Perhaps it is solved if you used ":1" instead of ":0"?
Otherwise I dont know if there is an easy solution.

---

### Post by rene86 on 2006-09-18
Did you use the "Connect to server"-Dialog?
Then this is not a bug, its a feature...

go to terminal:

```

gconf-editor

```

Now you some kind of a registry-editor, but better...
Under apps -> nautilus -> desktop you can unselect "volumes_visible" and they are away, but still in Places...

---

### Post by jd65pl on 2006-09-18
Will this stop me from seeing mounted cd drives external hard drives etc? I Still want to see them just not my server connects

Thanks for your pointer

J

---

