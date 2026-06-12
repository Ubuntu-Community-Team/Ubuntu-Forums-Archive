---
title: "[SOLVED] gpg fsfe crypto key - procedure - key with two signatures?"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by milosz.galazka on 2008-01-25
Hello,

I used [http://fsfe.org/en/card/howto/subkey_howto](http://fsfe.org/en/card/howto/subkey_howto) to setup my keys some time ago.

Lately I was recovering keys from backup using the same procedure to secure them on my computer.

After importing sub.seckey and pubring.gpg (look at step 6.6 and later in the [howto]("http://fsfe.org/en/card/howto/subkey_howto")) my subkey (sub 1024R/123456 created: 2007-06-19 expires: never usage: S) has two signatures:

sub   1024R/123456 2007-06-19
sig          78901234 2007-06-19  Milosz Galazka <milosz@sleeplessbeastie.eu>
sig          78901234 2007-06-19  Milosz Galazka <milosz@sleeplessbeastie.eu>

Is that ok?

Thanks

---

### Post by nowshining on 2008-01-26
i don't thiink so, re-create ur keys a new - some things don't restore from backup nicely.

---

### Post by milosz.galazka on 2008-01-26
> **nowshining said:**
> i don't thiink so, re-create ur keys a new - some things don't restore from backup nicely.

But I have full key with all sub/secret keys on the backup so I was only skipping some steps in the howto. 

Maybe I did something wrong?

---

### Post by nowshining on 2008-01-26
i know nothing more, that's all i would suggest -delete ur ol' restored versions, re-create the keys.

---

### Post by milosz.galazka on 2008-01-27
I found an answer. I used gpgsplit before importing sub.secring and deleted that signature :) so it's not importing again

---

### Post by nowshining on 2008-01-27
happy u got it solved :)

---

