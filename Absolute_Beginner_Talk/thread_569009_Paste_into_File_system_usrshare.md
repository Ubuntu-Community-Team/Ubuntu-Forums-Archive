---
title: "Paste into File system usr/share/"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by Najmudin on 2007-10-06
Hi

I downloaded some dictionary files for "stardict" and i have to put them into :
/usr/share/stardict/dic
but i can't paste any file there , there is no access .
my quistion is how can i paste them there , should i use the terminal or what can i do ?:confused:

---

### Post by taurus on 2007-10-06
Press <Alt>F2 and type

```
gksudo nautilus
```
Now, navigate to where stardict is and move it to /usr/share/stardict/dic.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by mysticmatrix on 2007-10-06
> **Najmudin said:**
> Hi

I downloaded some dictionary files for "stardict" and i have to put them into :
/usr/share/stardict/dic
but i can't paste any file there , there is no access .
my quistion is how can i paste them there , should i use the terminal or what can i do ?:confused:

Most probably they will have a package that you can install to get extra dictionary. That might not be advertised on website, but may be present in Synaptic Manager.
Open System-->Administration-->Synaptic Manager and do a search for stardict. You might get package you want.

In case you DO want to write into that protected area, do
```

gksudo nautilus
```

at teminal. Then perform drag drop as simple operation.

---

### Post by Najmudin on 2007-10-06
Thanks allot people , it works .:)

---

