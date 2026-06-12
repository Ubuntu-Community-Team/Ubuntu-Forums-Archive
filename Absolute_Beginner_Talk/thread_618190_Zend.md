---
title: "Zend"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by dc_jt on 2007-11-20
I have just downloaded Zend to Ubuntu and when I start it up, the tip box appears then when I close that all I get is a grey screen!!

The toolbar is not visible although it is actually there because I can use it using keyboard shortcuts, however whatever I do the screen just stays grey!!

By the way, the taskbar just says 'Java' rather than 'Zend Development Environment' which I think it should say.

Has this happened to anyone else? How do I fix?

Thanks

---

### Post by Elegorod on 2007-11-20
Isn't it the problem with compiz? If desktop effects are turned on, try to turn them off. 
Are there any exceptions or errors when running from terminal?

---

### Post by hyper_ch on 2007-11-20
could it be that it's based on Java in Linux?

---

### Post by jcfiala on 2007-11-20
You posted the same message twice?  That's not a great idea.

Take a look here:
[http://www.zend.com/support/knowledgebase.php?kbid=241&view_only=1](http://www.zend.com/support/knowledgebase.php?kbid=241&view_only=1)

---

### Post by smartbei on 2007-11-20
I believe you posted in programming talk and I replyed with a possible answer there. If the above messages about XGL/Compiz don't solve your problem...

Try installing the Sun version of the java runtime:
```

sudo aptitude install sun-java6-jre

```
I am not 100% sure that line is right, but it should be good.

---

### Post by dc_jt on 2007-11-20
> **jcfiala said:**
> You posted the same message twice?  That's not a great idea.

Take a look here:
[http://www.zend.com/support/knowledgebase.php?kbid=241&view_only=1](http://www.zend.com/support/knowledgebase.php?kbid=241&view_only=1)

Thank you very much, this fixed the problem :)

---

### Post by 1ONE on 2007-12-01
Thank you, adding 

options="$options -Dawt.toolkit=sun.awt.motif.MToolkit"

to line 1693 helped!

Thanks,

---

### Post by lpanebr on 2007-12-30
Great! The solution on [http://www.zend.com/support/knowledg...41&view_only=1](http://www.zend.com/support/knowledg...41&view_only=1) worked for me to!

Thanks!

---

