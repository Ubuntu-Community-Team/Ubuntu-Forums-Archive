---
title: "[SOLVED] Need help with (apt-key add)"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by MozartlovesUbun2 on 2007-12-21
Hi, i have virtualbox all setup and running fine, I've added the
deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) gutsy non-free
in to my /etc/apt/sources.list

**now how do i do this?**

>     * The innotek public key for apt-secure can be downloaded here. You can add this key with

      apt-key add innotek.asc

    The key fingerprint is

    6947 BD50 026A E8C8 9AC4  09FD 390E C3FF 927C CC73
    innotek GmbH (archive signing key) <info@innotek.de>



**it's explained here, but i am having a little trouble following it**
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)
can someone please give me an easy how to, thanks

====================================================
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: GnuPG v1.4.6 (GNU/Linux)

mQGiBEZkBn8RBACccOdQohVvrpVvgBx2F8j1fv+0UwzGwyVFhGzUNBUIClsLQEMf
jFAspPFUsndzzCnotrFJpKc5ES/Lf9Yt2LuVr3bsUB8kF6AEJTuBdapwiQIXH72M
80MRhFLquuCDXS8RFvMmhXxmjpTUchOWpFNH4CC9FQNuoMBqUPJovYaLLwCgwbAV
1+2328/lcXkO5uC8mZN9KJUEAI7ZUJZeAqrnptCyha8sZf8UUkFh6AGMJPxafK1z
cis65BOFXYyq8G2qhPKqSFPAUAfjb7E7ONK1kMcMfPE1dKFE1bZ//pjjHzUds6/y
UP1LeuYveWnIQmsGv3+OkfUovVDc4BdyIGMruPu4VBy0FyefTjf47Am4D69LZ9Wz
+IrSA/9GXrzzJkn0sfHtXo3ihIhZzZtZGYsNaLqF9pb0Pk/6SeBq3EgTBGIuSFdj
HemwbaPrb7WzGKEZcaRNzrgfx13uQbsQoCJM9XTr5I37+nA8UkibcuXyPKEgSBNt
I+jx9Cv6+86ivc0Dx8kExauoSE1rWksFwhk+VscaMzezkfe1U7Q0aW5ub3RlayBH
bWJIIChhcmNoaXZlIHNpZ25pbmcga2V5KSA8aW5mb0Bpbm5vdGVrLmRlPohgBBMR
AgAgBQJGZAZ/AhsDBgsJCAcDAgQVAggDBBYCAwECHgECF4AACgkQOQ7D/5J8zHNV
ngCgnzBMPLtVSP7U0988Q4A03XjYjg0An3wHt385u1hAXBgCIWA4J/WQOGIluQIN
BEZkBoEQCAC7eZCkCrT0ZNAgqIHv3SUxieqiMMNDfMsrwHO1cdO0zuMkcGDRDENE
sNbqdvL9TRWBb/ub0gcl3bFATihAP68tssqFMv9fsHIFK7y9obS5vRUUi2NJKAMv
XTxmYcBlXnEBLfpJR1Vct60+dcmkF0cgMm8m5BhjLt8aAPUUsDvZo/yUMVYbV+4s
ulKPw2h7nubsHUPb+0pVNHyzJlWt1On0jW5t3XF8En9m3f0PWlmBJOnaZOb0cLrB
Om6qiKK+a7ps0jf/2047Kkto1rToEAlut+KwwQaLQxPcI7jRirDZ+4nYgQJGiQLL
PHPSOVNwRDw/AS8X2Q6CxqjeZCXRuqUHAAMFB/9Vn6psB1appyYZS7p+2bsChnjv
NyA9SAVRAMHfhDXNiD1EHEExedP/KgIBGMUSwrc8g/8IqdwFIPUPueIEt2PkbI5i
zR8ADdW3tkgKnBI/3hxin2r9osvpNZUJsqamPpmth5G07Oj/MGtFgL8aLqXN8hIP
L1CrcvWnAsizIC+/RzqHZQVYkVWh7/Z7Vt321H+1fqTpTAs1VLKIcruCrVBMW5Kh
568Zla8r+EvrLPTLvdOtabDuhsYnyqWEWJfiiSlTB+Wm1nilTKz9r1qDikOsM51O
f4vobGqYLJrlW4dx3XA7yDhmTQwLTG48fh/3ORQoxCp4z+sHwDPIXeH3g7PUiEkE
GBECAAkFAkZkBoECGwwACgkQOQ7D/5J8zHMU2wCgusNPxQhdlszpi2vvFHoRL67+
2kgAnRvA99DMrSFPDALce3Rx0lXGlImA
=Ow4f
-----END PGP PUBLIC KEY BLOCK-----

I downloaded the **innotek.asc** key to my desktop
then put: **apt-key add innotek.asc** in the terminal

> mozart@network:~$ sudo su
[sudo] password for mozart:
root@network:/home/mozart# apt-key add innotek.asc
gpg: can't open `innotek.asc': No such file or directory
root@network:/home/mozart# 



so how do I do it the right way?

---

### Post by MozartlovesUbun2 on 2007-12-21
SOLVED

i put the downloaded key in my home folder from the desktop
and then ran the script again

---

