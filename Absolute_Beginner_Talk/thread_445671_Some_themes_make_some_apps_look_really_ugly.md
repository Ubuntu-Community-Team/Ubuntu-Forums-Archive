---
title: "Some themes make some apps look really ugly"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by tanelt on 2007-05-16
Some themes like [this one](http://art.gnome.org/themes/gtk2/1345) make Time&Date settings, Synaptic, and some other apps look like crap:

[[img]http://xs115.xs.to/xs115/07203/ScreenshotTimeandDateSettings54.png.xs.jpg[/img]](http://xs115.xs.to/xs115/07203/ScreenshotTimeandDateSettings54.png)


Why's that? I really like the look of that theme "Foresight", but why does it make those apps look like this? :confused:

---

### Post by reclusivemonkey on 2007-05-16
Some applications run as the root user. If you install themes via the preferences, then they only get installed to your home directory, and thus the root user doesn't have the theme files. You can either copy the themes to the right place in the /usr dir, or probably the easiest way is to copy ~/.themes from your home dir to root;

```

sudo cp -r ~/.themes /root

```

should do it. This one puzzled me for a while too! HTH =]

---

### Post by tanelt on 2007-05-16
Copying that directory to /root solved the problem! :KS

Thanks a lot for the help! Now all of the apps have the same great skins.  =)

---

### Post by starcraft.man on 2007-05-16
YAY! Thanks for that, I was wondering how to fix that too... now looking really good :)

---

