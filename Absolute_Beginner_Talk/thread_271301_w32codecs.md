---
title: "w32codecs"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by eriefisher on 2006-10-04
I've been out of touch for awhile. I just did a fresh install of Kubuntu 5.10 and I can't find the w32codecs. It looks like the repos are down. Is this right? Can I still get them somewhere? Would upgrading to Dapper make any difference? Thanks.

---

### Post by Lord Illidan on 2006-10-04
> **eriefisher said:**
> I've been out of touch for awhile. I just did a fresh install of Kubuntu 5.10 and I can't find the w32codecs. It looks like the repos are down. Is this right? Can I still get them somewhere? Would upgrading to Dapper make any difference? Thanks.

I would suggest installing Dapper freshly..or wait for Edgy. You can still find the w32 codecs here : [https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5](https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5)

---

### Post by aysiu on 2006-10-04
Upgrading to Dapper won't make a difference. w32codecs is a proprietary package and will never be included in a default Ubuntu installation.

If you want to install it for Breezy, just paste these three commands in the terminal: ```
wget -c http://packages.freecontrib.org/plf/pool/breezy/non-free/w32codecs_20050412-1plf4_i386.deb
sudo dpkg -i w32codecs_20050412-1plf4_i386.deb
rm w32codecs_20050412-1plf4_i386.deb
```

---

### Post by eriefisher on 2006-10-04
Thanks but that looks like it's for Dapper. I guess I'm out of luck for breezy. Will the dapper file work in breezy?

---

### Post by Lord Illidan on 2006-10-04
> **aysiu said:**
> Upgrading to Dapper won't make a difference. w32codecs is a proprietary package and will never be included in a default Ubuntu installation.

If you want to install it for Breezy, just paste these three commands in the terminal: ```
wget -c http://packages.freecontrib.org/plf/pool/breezy/non-free/w32codecs_20050412-1plf4_i386.deb
sudo dpkg -i w32codecs_20050412-1plf4_i386.deb
rm w32codecs_20050412-1plf4_i386.deb
```

Once again, aysiu saves the day..

Dapper might not include w32codecs, and nor will Edgy, but what I meant is that it will iron out diverse bugs, as well as introduce some new ones....well I like being up to date..why are you still running Breezy :)

---

### Post by eriefisher on 2006-10-04
Thanks Aysiu, I'm trying it now. It looks like it's going to work. Thanks again.

---

### Post by aysiu on 2006-10-04
> **Lord Illidan said:**
> Once again, aysiu saves the day..

Dapper might not include w32codecs, and nor will Edgy, but what I meant is that it will iron out diverse bugs, as well as introduce some new ones....well I like being up to date..why are you still running Breezy :)
Yes, I too would recommend installing Dapper, as Breezy is almost a year old already. But if you already have Breezy installed, upgrading to Dapper doesn't magically install *w32codecs*.

---

### Post by eriefisher on 2006-10-04
> **Lord Illidan said:**
> Once again, aysiu saves the day..

Dapper might not include w32codecs, and nor will Edgy, but what I meant is that it will iron out diverse bugs, as well as introduce some new ones....well I like being up to date..why are you still running Breezy :)

It's just been a question of time. I can't download it at home due to dial up so I just need to spend some time at a friend's or family's computor. Hopfully soon though. Thanks for the help all.

---

### Post by Lord Illidan on 2006-10-04
> **aysiu said:**
> Yes, I too would recommend installing Dapper, as Breezy is almost a year old already. But if you already have Breezy installed, upgrading to Dapper doesn't magically install *w32codecs*.

ok ok sir..:mrgreen:

---

### Post by kjaggu on 2006-11-03
Thanks a lot for the codecs.

---

### Post by Jason Weiss on 2006-11-05
Hi, 

I am another nu bee so sorry if this has been covered a million time. 

I installed w32codes fine, however movies now play but there is no sound?

Any sugestions

---

