---
title: "compiz slow start up"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by InsertNameHere on 2007-11-08
When I open my computer it's about 40 secs before it got to the login screen, that's fine but it takes about a minute to log in.

The screen starts brown for 1 whole MINUTE (or more) before displaying anything (after the brown it displayed everything)

Before I customized compiz it didn't happen
but all I did was turn on cube and ring switcher, switched metacity themes and got the SUSE start menu thing.

My comp details:

Core 2 Duo 1.66Ghz (the most ever processing power used was 60% on conky)
2 G RAM(400mb normal 700mb windoze in vm)
Intel GFX card.

Please help me speed up login.....
thanks.:)

---

### Post by bks on 2007-11-08
Try this:

```

sudo gedit /etc/usplash.conf

```

Make sure the screen resolutions listed in the file match those for your monitor, if not change them and save the file. Restart and see if it is any better.

---

### Post by InsertNameHere on 2007-11-08
It didn't speed up but it detected my monitor res wrong...

Changing it however didn't help

---

