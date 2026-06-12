---
title: "ubuntu splash replaced with kubuntu"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by maprx on 2006-10-28
I was setting up ubuntu, I am getting tired of kde and how it looks on my monitor.  This version installed corrected the xorg, downloaded a ton of stuff.  Installed kde just in case and now when unbuntu boots down, i get a kubuntu  splash screen.  When unbuntu boots up I see a kubutu splash and then the flashes and I am loading the ubuntu desktop with sounds.  How can I fix this.  It seems like broke something

mike:confused:

---

### Post by davmac on 2006-10-29
I'm sure there's an easy way to replace the image that is shown but when this happened to me I found it easiest to just remove and reinstall usplash.

Open up a terminal window and type;

"sudo apt-get remove usplash"
"sudo apt-get install usplash"

Hope this helps,

Dave Mac

---

### Post by kylevan on 2006-12-09
I had the same thing happen to me.

```
sudo apt-get remove usplash
```

this will also remove the ubuntu-desktop metapackage, so, just re-install ubuntu-desktop, and things are lovely

```
sudo apt-get install ubuntu-desktop
```

---

