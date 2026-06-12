---
title: "Made a stupid mistake - deleted my xinetd script"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by tbg58 on 2006-12-01
I know it's a stupid mistake, but I deleted the script xinetd from my /etc/init.d directory on my Edgy box.  I was reconfiguring VNC for headless operation, and made a mistake that makes me look more headless than my box.

I tried to apt-get remove xinetd followed by apt-get install, but the script didn't come back.  I think it has something to do with reversion to inetd after xinetd was removed but I'm not sure.

My choices were:

1.  Wait until I go home and get a copy of the default script from my Edgy box at home tonight and slip it in on the sly.

2.  Go ahead and eat my humble pie and ask for help - I think I'll learn more from this one.

So with my hat in hand, anyone know how I can get my xinetd file back in /etc/init.d where god intended it to be?

(swallowing humble pie)

Rob

---

### Post by SyvanX on 2006-12-01
you could try:
aptitude reinstall xinetd

I don't have it installed, but you could try going into 
/usr/share/xinetd 
to look for the script in there.

---

