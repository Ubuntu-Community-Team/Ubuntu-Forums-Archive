---
title: "compile kernel 2.6.17?"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by cyme on 2006-08-05
okey i followd this howto [http://www.ubuntuforums.org/showthread.php?t=217657](http://www.ubuntuforums.org/showthread.php?t=217657)
and i got this error :S what am i doing wrong

```
drivers/media/dvb/ttpci/budget-av.c: In function "frontend_init":
drivers/media/dvb/ttpci/budget-av.c:1063: error: "struct budget_av" has no member named "reinitialise_demod"
drivers/media/dvb/ttpci/budget-av.c:1068: error: request for member "tuner_ops" in something not a structure or union
drivers/media/dvb/ttpci/budget-av.c:1068: error: "philips_cu1216_tuner_set_params" undeclared (first use in this function)
drivers/media/dvb/ttpci/budget-av.c:1068: error: (Varje odeklarerad identifierare rapporteras bara
drivers/media/dvb/ttpci/budget-av.c:1068: error: en gång för varje funktion den finns i.)
make[5]: *** [drivers/media/dvb/ttpci/budget-av.o] Fel 1
make[4]: *** [drivers/media/dvb/ttpci] Fel 2
make[3]: *** [drivers/media/dvb] Fel 2
make[2]: *** [drivers/media] Fel 2
make[1]: *** [drivers] Fel 2
make[1]: Leaving directory `/usr/src/linux-2.6.17.7'
make: *** [stamp-build] Fel 2
```

---

### Post by metathran on 2006-08-06
[http://ubuntuforums.org/showpost.php?p=1308736&postcount=106](http://ubuntuforums.org/showpost.php?p=1308736&postcount=106)

---

