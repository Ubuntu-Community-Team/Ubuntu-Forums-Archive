---
title: "Getting compiz to work!"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by loganm10 on 2007-10-19
Okay, so compiz worked for me in 7.04, but not in 7.10

For some reason my card got blacklisted, which doesnt make much sense because it used to work fine (I have just onboard intel graphics on my toshiba laptop)

So I was a little TO'ed, I went to the Blacklist page on Compiz-Fusions site, and it gave this script:

SKIP_CHECKS=yes compiz --replace

If you run that from the terminal, exactly like that, compiz runs, and it works too!!

Now I wouldnt recommend this for everyone, because Im sure some cards are blacklisted for a reason, but in my case it works great

You can add this script to startup by going System>Preferences>Sessions, and adding that script in there

---

### Post by loganm10 on 2007-10-19
also you can create a file called:
/.config/compiz/compiz-manager

and put:
SKIP_CHECKS=yes

in that file, then compiz will run normally with compiz --replace

---

### Post by jfernandes@inbox.com on 2007-10-19
Is this Compiz work with 32mb nVidia Video Card for Ubuntu 7.10 Please Help me

---

