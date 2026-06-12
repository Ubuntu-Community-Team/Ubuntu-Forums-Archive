---
title: "unable to update pkgs"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by SilverLinux on 2008-03-17
I am a total (old) newbie.  I thought all was well and something happened and I get the following msg:'E:Malformed line 77 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read.' can anyone help with this?
Thaniks so much.

---

### Post by bsharp on 2008-03-17
could you post your /etc/apt/sources.list?

---

### Post by Oldsoldier2003 on 2008-03-17
> **SilverLinux said:**
> I am a total (old) newbie.  I thought all was well and something happened and I get the following msg:'E:Malformed line 77 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read.' can anyone help with this?
Thaniks so much.

post your sources.list or just look at line 77 for some obvious error.

---

### Post by SilverLinux on 2008-03-17
I will try but not sure how to do it.

---

### Post by Oldsoldier2003 on 2008-03-17
> **SilverLinux said:**
> I will try but not sure how to do it.

```
cat /etc/apt/sources.list
```
then paste the results into a reply, we can work from there.

---

### Post by bsharp on 2008-03-17
```
gedit /etc/apt/sources.list
```
in a terminal, select everything and then paste it in [ code][ /code] brackets in a reply.

---

### Post by SilverLinux on 2008-03-17
Thanks to everyone.  I solved the problems by reinstalling.  I wasn't that far along so I didn't lose anything.
Thanks again.  I am sure I will be back.

---

### Post by Oldsoldier2003 on 2008-03-17
> **SilverLinux said:**
> Thanks to everyone.  I solved the problems by reinstalling.  I wasn't that far along so I didn't lose anything.
Thanks again.  I am sure I will be back.

I'm glad to hear you got it sorted. Although I'm sure we could have fixed you up without resorting to a reinstall, at the early stages of your Ubuntu experiences its always satisfying to solve an issue on your own even if it means doing a fast reinstall. Welcome to the Ubuntu community and have fun! If you run into any more problems, don't be afraid to post there are tons of helpful people here!

---

