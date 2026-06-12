---
title: "Ubuntu Server 7.04 Boot into Command Line"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by ianmar on 2007-07-05
Currently have Ubuntu Server 7.04 installed , with GNOME GUI interface. 

Was just wondering, how do you change the boot sequence ( im guessing in /etc/event.d ) to it boots into Command line at default?

Thanks :)

---

### Post by scxtt on 2007-07-05
stop gdm from being started @ boot: **sudo rm /etc/rc2.d/S99gdm**

---

### Post by ianmar on 2007-07-05
can we boot into GNOME in the Command line with the startx command  after we've removed that file ?

edit : just checked and theres no such file. Theres a S13gdm , I've tried removing that and it seems fine ! Thanks :)

---

### Post by scxtt on 2007-07-05
sure can, as long as it's your $XSESSION (can't remember if ubuntu uses that or not, but if you booted into gnome previously, you'll still be able to) ...

---

### Post by mrblack448 on 2007-07-05
SXXgdm should just be a link to the init script, so deleting it shouldn't prevent starting X

you could also just rename it to sXXgdm and it won't start up, then you can just rename it back if you want to

---

### Post by scxtt on 2007-07-05
yes, but those are parsed when you boot to a specific run-level - so when run-level 2 is init'd, all the scripts in it's respective directory are started - you remove that link, it won't be started ... that's what the "Services" gui does as well (and could be used to put the link back) ...

---

### Post by mrblack448 on 2007-07-05
but when it parses those it just looks for the ones that start with "S", right? at least that's what Slowaris does

i just get nervous rm'ing anything :)

i didn't notice that in the "Services" GUI, i'll have to check that out

i was actually looking for an answer to this same question, i just wasn't sure how it worked in Ubuntu. i was looking for /etc/inittab like in Redhat

---

### Post by tribaal on 2007-07-05
It Starts services with a "S" as first letter, and Kills (gracefully) those links that start with a "K" :)

Hope this helps :)

- trib'

---

### Post by scxtt on 2007-07-05
> **mrblack448 said:**
> but when it parses those it just looks for the ones that start with "S", right? at least that's what Slowaris does

i just get nervous rm'ing anything :)

i didn't notice that in the "Services" GUI, i'll have to check that out

i was actually looking for an answer to this same question, i just wasn't sure how it worked in Ubuntu. i was looking for /etc/inittab like in Redhatunderstandable, but in this case it's just removing a symbolic link - no biggie :) ...

S = start, K = kill where the lower the #, the higher the priority ... for ubuntu (gnome) there's something called "services", for kubuntu (KDE) - you can get to it via "system settings" ... *ubuntu doesn't use inittab, which was annoying for me too cause i was used to it ... as far as i remember, red hat just had a boot level w/o X - but it's been a while since i've used anything red hat like (well, i used RHEL5 for a while w/in the past month, but i stopped) ...

---

