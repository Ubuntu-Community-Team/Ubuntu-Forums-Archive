---
title: "GAIM dead AGAIN!"
date: 2005-08-08
forum: Absolute Beginner Talk
---

### Post by gammyhand on 2005-08-08
Really annoyed now. GAIM has died for the second time in a month for no apparent reason. This time it is a "read error" on the contacts list. Last time the only way to fix it was to re-format and re-install ubuntu...if that is going to be the case this time I am going back to windows as MSN is one of my must have programs and I can't keep re-formatting on GAIM's whim.

---

### Post by iH8forcedRegistration on 2005-08-08
[QUOTE=gammyhand]Really annoyed now. GAIM has died for the second time in a month for no apparent reason. This time it is a "read error" on the contacts list. Last time the only way to fix it was to re-format and re-install ubuntu...if that is going to be the case this time I am going back to windows as MSN is one of my must have programs and I can't keep re-formatting on GAIM's whim.[/QUOTE]
 This could be a problem with your gaim profile information. Try this:

Open a terminal and type this:
```

cd ~
mv .gaim .gaim_old

```

then start gaim again. It should start forgetting everything it ever knew about you. If that doesn't fix the problem, I'll be surprised.

If you want your old, broken profile back, do
```

cd ~
rm -Rf .gaim
mv .gaim_old .gaim

```

---

### Post by ubuntu_demon on 2005-08-08
Your msn contact list is also saved on the msn servers. So it might be a server problem. 

If it isn't a server problem probably iH8forcedRegistration's solution will work.

I have never experienced this problem of yours. I use gaim from backports. Installing that version might prevent the problem from happening. You should look at the ubuntuguide and use their sources.list 

[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

after this do :
$sudo apt-get update
$sudo apt-get upgrade

now you have the newest gaim from backports and maybe the problem won't manifest anymore.

---

### Post by gammyhand on 2005-08-08
[QUOTE=iH8forcedRegistration]This could be a problem with your gaim profile information. Try this:

Open a terminal and type this:
```

cd ~
mv .gaim .gaim_old

```

then start gaim again. It should start forgetting everything it ever knew about you. If that doesn't fix the problem, I'll be surprised.

If you want your old, broken profile back, do
```

cd ~
rm -Rf .gaim
mv .gaim_old .gaim

```[/QUOTE]
 Ahh...that fixed it...will remember that for the future :) Thanks.

---

