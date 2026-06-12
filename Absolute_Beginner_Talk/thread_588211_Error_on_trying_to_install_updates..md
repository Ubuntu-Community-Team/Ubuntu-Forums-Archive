---
title: "Error on trying to install updates."
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by wjhildreth on 2007-10-23
Hello all,

I upgraded to gutsy and initially had an error with tzdata.To fix this I had to force the removal of tzdata and reinstall it along with other missing packages. Well every thing was working great until this morning when the following updates were available.

```


firefox
forefox-gnome-support
ghostscript
ghostscrip-x
gs-common
gs-esp
gs-esp-x
libgs8
libssl0.9.8
openssl

kdelibs-data
kdelibs4c2a


```

When installing I get the following error

```

E: tzdata: subprocess post-installation script returned error exit status 10

```

Can someone provide me some guidance on how to go about fixing this?

Many Thanks for your time and energy!

Warm Regards,

Joe Hildreth

---

### Post by cmnorton on 2007-10-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/147200](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/147200) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				It's being worked as a bug.

---

### Post by wjhildreth on 2007-10-23
Thanks for the info. I tried changing the timezone to Europe/Berlin and reinstall tzdata but still get the same error.

Any other ideas?

Thanks,

Joe

---

### Post by wjhildreth on 2007-10-23
Well, if i remove tzdata I am able to install all of the other updated packages. My problems all seem to be with the tzdata package. Removing and reinstalling with a different timezone does not help my situation. It is a little frustrating. I know just enough about Linux to be dangerous to myself, but not enough to really figure out what is going on with tzdata.

Regards,

Joe

:(

---

