---
title: "No display"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by IanBraby on 2008-02-09
OK - here's a poser!

I decided to try out the ATI driver for my computer in place of the open source version and, on rebooting, I have no display - my monitor tells me that it's being asked to display too high a resolution!

Now, I've tried recovery mode but, of course, this is a CLI and I don't have a clue what I need to do to restore the open source display driver from the CLI. Can anyone please offer a quick solution for me?

---

### Post by taurus on 2008-02-09
```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

