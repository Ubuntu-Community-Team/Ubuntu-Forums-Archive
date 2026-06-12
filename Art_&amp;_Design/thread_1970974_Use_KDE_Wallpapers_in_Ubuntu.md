---
title: "Use KDE Wallpapers in Ubuntu"
date: 2012-05-01
forum: Art &amp; Design
---

### Post by stephenmac7 on 2012-05-01
So, earlier today I wanted to use kde wallpapers in Ubuntu but couldn't so I created a script to symlink the wallpapers to the current directory which should be pictures so that it would show up in the Pictures Folder section of the wallpaper selector. To use run:
```
python -c "import sys; py3 = sys.version_info[0] > 2; u = __import__('urllib.request' if py3 else 'urllib', fromlist=1); exec(u.urlopen('http://pastie.org/pastes/3846882/download').read());"
```
in the Pictures folder.

Also, the resolution can be changed on line 10. Be sure to install kde-wallpapers and kdewallpapers before running

---

