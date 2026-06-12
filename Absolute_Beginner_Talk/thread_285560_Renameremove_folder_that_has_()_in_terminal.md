---
title: "Rename/remove folder that has () in terminal"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by SunnyM on 2006-10-27
For some crazy reason, when I mounted my secondary hardrive, it picked 3 of the folders on there and made them root only. I have no idea why, and the rest of the folders on there appear to be fine. So I copied all the files in these folders to a new folder I created that isn't messed up. Then I started to delete the folders in terminal, and everything was going great until I got to a folder labled Drawings (Scanned) which has another wierd folder inside it. I can't remove it in terminal by using Drawings* because I get a message that it's not empty, but I can't delete the folder inside because
```
sudo rmdir /media/windows/photos/Drawings\ (Scanned)/Tattoos/
```gives me this error:
```
bash: syntax error near unexpected token `('
```Any help would be much appreciated. Thanks in advance.

---

### Post by Denn1s on 2006-10-27
Do you need to do it in terminal? You could try:
```
sudo nautilus
```
and try to delete the folder using the explorer

---

### Post by magicfab on 2006-10-27
Type only part of the path and then use the "TAB" key to autocomplete it. You may see it is escaped to accomodate the special characters. And don't use () in future folder names ;)

---

### Post by aysiu on 2006-10-27
> **Denn1s said:**
> Do you need to do it in terminal? You could try:
```
sudo nautilus
```
and try to delete the folder using the explorer
You mean ```
gksudo nautilus
```

---

### Post by SunnyM on 2006-10-27
@denn1s *dies* You have no idea how awesome you are! I wish I'd known that the whole time, I could have cut/pasted the files instead of copying them.
](*,)

---

### Post by SunnyM on 2006-10-27
> **magicfab said:**
> Type only part of the path and then use the "TAB" key to autocomplete it. You may see it is escaped to accomodate the special characters. And don't use () in future folder names ;)

I have no intention of it. In fact, since switching to ubuntu, I've learned the evils of sloppy file naming, lol. I now use all lowercase, _ instead of space, etc. Makes life much easier. There's still quite a few things I still need to fix the names of, though.

---

### Post by IYY on 2006-10-27
Why not just do it like this? :-k 

```

sudo rmdir "/media/windows/photos/Drawings (Scanned) Tattoos"
```

---

