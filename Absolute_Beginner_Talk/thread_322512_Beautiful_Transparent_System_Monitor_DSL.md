---
title: "Beautiful Transparent System Monitor: DSL"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by andrew.46 on 2006-12-20
Hi,

 Is there an equivalent for the rather nice transparent System Monitor I have seen in the Damn Small Linux distro? I am running 5.10 and the System Monitor that comes by default is not nearly as pretty :) 

 BTW is there a neat way of showing exactly what version of Ubuntu I am running?

                       Thanks,

                                Andrew

---

### Post by angkor on 2006-12-20
> **andrew.46 said:**
>  BTW is there a neat way of showing exactly what version of Ubuntu I am running?


Ctrl+Alt+F1 will work. (Ctrl+Alt+F7 to get back)

You can also check System -> About Ubuntu.

Do you have a screenshot showing the system monitor?

Edit: It could be [conky]("http://conky.sourceforge.net/").

---

### Post by K.Mandla on 2006-12-20
If you mean the onscreen system resources monitor on the desktop, that's Conky.

If you want to know about the version of linux you're running, you could enter this in a terminal:

```
uname
```
If you use conky, there's a ton of great ways to show what kind of Linux you're using. Look [here]("http://www.ubuntuforums.org/showthread.php?t=281865") and [here]("http://www.ubuntuforums.org/showthread.php?t=205865").

---

### Post by angkor on 2006-12-20
> **K.Mandla said:**
> If you want to know about the version of linux you're running, you could enter this in a terminal:
```
uname
```

Uname gives me:

```
~$ uname
Linux
```

---

### Post by maxamillion on 2006-12-20
The system monitor used in DSL is called [Torsmo]("http://torsmo.sourceforge.net/") and the Ubuntu equivalent would be [Conky]("http://conky.sourceforge.net/") (as mentioned by others)

You need to use "uname -r" to view the kernel release version and that will be able to be cross referenced with that Ubuntu release you are running.

---

### Post by K.Mandla on 2006-12-20
> **angkor said:**
> Uname gives me:

```
~$ uname
Linux
```
Oops, my fault. That should be *uname -a*.

---

### Post by K.Mandla on 2006-12-20
> **maxamillion said:**
> The system monitor used in DSL is called [Torsmo]("http://torsmo.sourceforge.net/") and the Ubuntu equivalent would be [Conky]("http://conky.sourceforge.net/") (as mentioned by others)
Oops, my fault again. That'll teach me to reply too quickly. :oops:

---

### Post by invisage01 on 2006-12-20
is it possible that you saw one of the [Gdesklet]("http://www.gdesklets.org/")'s on a desktop?

i know that i have seen some nice system monitors that sit on the desktop - these are definately transparent in alot of cases?

---

### Post by angkor on 2006-12-20
> **invisage01 said:**
> is it possible that you saw one of the [Gdesklet]("http://www.gdesklets.org/")'s on a desktop?

i know that i have seen some nice system monitors that sit on the desktop - these are definately transparent in alot of cases?

There's also [gkrellm]("http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html"). There's a transparent theme available.

```
sudo aptitude install gkrellm
```

---

### Post by andrew.46 on 2006-12-20
> **angkor said:**
> 

Do you have a screenshot showing the system monitor?

Edit: It could be [conky]("http://conky.sourceforge.net/").

 Hi,

 Found a quite elegant screenshot at:

[http://www.tuxmachines.org/gallery/dsl23/desktop?full=1](http://www.tuxmachines.org/gallery/dsl23/desktop?full=1)

             Andrew

---

