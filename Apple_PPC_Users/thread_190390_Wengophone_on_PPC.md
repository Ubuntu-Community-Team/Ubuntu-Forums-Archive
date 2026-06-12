---
title: "Wengophone on PPC"
date: 2006-06-06
forum: Apple PPC Users
---

### Post by Ububurns on 2006-06-06
Wengophone is available for PPC (hooray!) and I am having a little trouble.

Whenever go to make a call I receive this error message:

**Couldn't open audio**
[I]Please check that:
Your soundcard is configured properly.
No other program is blocking the soundcard.[/I]

Thus I am unable to send or receive any audio.

I disabled esd, but to no avail.

Any help would be much appreciated!

---

### Post by neocon2005 on 2006-06-06
Try to explicitly kill esd.
ps -A | grep esd
and then kill using the PID.

Also, for some reason WengoPhone 2.0 worked for me but the version in the repos didn't work (0.9something). Get the latest from [http://www.openwengo.com/index.php/mp_download_wp_lin](http://www.openwengo.com/index.php/mp_download_wp_lin)
No install required!

BTW my machine is i386 but I thought these pointers maybe helpful. Good luck!

[QUOTE=Ububurns]Wengophone is available for PPC (hooray!) and I am having a little trouble.

Whenever go to make a call I receive this error message:

**Couldn't open audio**
[I]Please check that:
Your soundcard is configured properly.
No other program is blocking the soundcard.[/I]

Thus I am unable to send or receive any audio.

I disabled esd, but to no avail.

Any help would be much appreciated![/QUOTE]

---

### Post by Ububurns on 2006-06-06
Thanks for your help, but that version is only for x86 processors.

Perhaps I could try compiling it by source... but it seems such a little problem!

Does anyone else have any ideas?  Has anyone had success in running wengophone, in Dapper, on a Mac?

---

### Post by trash on 2007-01-07
No joy in Edgy.. i just tried EasyUbuntu and Wengophone just hangs.

---

