---
title: "glossy panels"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by syalam on 2007-02-22
I see screenshots of people with glassy/glossy panels, I was wondering how to achieve this effect. I've been on gnome-look.org but I haven't found any good glossy ones. Does anyone have any recommendations?

---

### Post by carlosfocker on 2007-02-22
Search around on [http://www.gnome-look.org/](http://www.gnome-look.org/) or [http://art.gnome.org/](http://art.gnome.org/) .

Take a look and find something you like.

---

### Post by neji on 2007-02-22
the transparent panels are done with beryl, check out beryl themes on gnome-look

---

### Post by mcduck on 2007-02-22
You can use any picture you want as panel background. Even transparent images work fine (although this is broken in Dapper, you get funny colors with transparent images). I have made quite many ones, if you want you can download them all from here: [panels.tar.gz]("http://www.elisanet.fi/~z626117/random/panels.tar.gz")

For best look you need to enable scaling of panel background pictures:

1.Open Configuration Editor (press Alt-F2 and run 'gconf-editor')
2. Browse to apps/panel/toplevels/<yourpanelname>/background
3. Enable 'rotate' and 'stretch' (you only need 'rotate' for vertical panels)

---

