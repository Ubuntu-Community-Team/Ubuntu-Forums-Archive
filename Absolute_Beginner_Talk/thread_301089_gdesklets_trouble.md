---
title: "gdesklets trouble"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by DSn0wMan on 2006-11-16
I mistakenly enabled the translucent property in my gdesklets, and it really looks bad.

```
gdesklets --translucent
```

Unfortunately I can't figure out a way to disable this. Any advice would be appreciated.

---

### Post by taurus on 2006-11-16
Start gDesklets.  Place a cursor on the icon (upper right corner of the panel) and click the right mouse.  Pick Configuratioon and uncheck Translucency...  Close it (Stop daemon) and restart it again!

Otherwise, remane ~/.gdesklets to something else.

```
mv ~/.gdesklets  ~/.gdesklets-old
```

---

### Post by DSn0wMan on 2006-11-16
```
mv ~/.gdesklets  ~/.gdesklets-old
```

Thanks that worked perfectly.

---

### Post by taurus on 2006-11-16
And if you don't have anything important in ~/.gdesklets-old that you want to move over to ~/.gdesklets, you can delete it if you wish...

```
rm -rf ~/.gdesklets-old
```

---

