---
title: "filesystem properties..."
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by je1117 on 2007-01-31
Hi guys. I was wondering why when I right click > properties on my filesystem it shows unknown for size, modified, and accessed. Is this part of the permissions or is something up?

Thanks.

---

### Post by jd65pl on 2007-01-31
If you want to know the size of your mounted drives you can use

```
df -h
```

---

### Post by mcduck on 2007-01-31
> **je1117 said:**
> Hi guys. I was wondering why when I right click > properties on my filesystem it shows unknown for size, modified, and accessed. Is this part of the permissions or is something up?

Thanks.
Are you doing this in the 'Computer'-thing in Nautilus? It doesn't actually show that information for any item.

I suppose that is because such thing as 'Computer' doesn't really exist anywhere else than in that particular window, it's just a GUI to make Windows users feel more like at home.

If you actually go to / and check properties you will get all information.

---

