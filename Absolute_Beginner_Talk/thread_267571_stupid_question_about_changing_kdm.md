---
title: "stupid question about changing kdm"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by Justin Holt on 2006-09-28
Like i said, it is a stupid question, but how do i change the kdm theme to another theme i downloaded off of kde-look.org

---

### Post by ZennouRyuu on 2006-10-04
Not a stupid question at all, KDE does not provide and default GUI for managing this as far as I know. There have been some third party attempts that seem to work ok for people, but I have never used them......

I use the kdmrc config file to change the kdm themes, its easy enough. Just edit /etc/kde3/kdm/kdmrc and change the line that reads

```
Theme=/usr/share/apps/kdm/themes/kubuntu
```

to point to the theme you have downloaded.

---

