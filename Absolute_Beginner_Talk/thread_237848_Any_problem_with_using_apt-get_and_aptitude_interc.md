---
title: "Any problem with using apt-get and aptitude interchangeably for package management?"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-08-16
Most of the time I'm using aptitude for package management. However, some utilities like auto-apt uses apt-get in the backend. 

Would that be any problem with installing/uninstalling 'apt-get installed' packages with aptitude?

Thanks.

---

### Post by AirRaven on 2006-08-16
Basically, if you install something with apt-get, it doesn't remember the dependencies it retrieved whilst retrieving the package- so if you use [FONT="Courier New"]apt-get install kopete[/FONT], it'll get some of the Qt libraries and so on, but when you type [FONT="Courier New"]apt-get remove kopete[/FONT], it'll simply remove the Kopete package without removing the Qt libraries it depended on.

Aptitude remembers the dependencies- if you use [FONT="Courier New"]aptitude install kopete[/FONT] then [FONT="Courier New"]aptitude remove kopete[/FONT], you'll remove all the dependencies as well. Unfortunately, if you use [FONT="Courier New"]apt-get[/FONT] to install a package, aptitude won't know which dependancies to remove when you run [FONT="Courier New"]aptitude remove package[/FONT], so you'll have it acting just like [FONT="Courier New"]apt-get remove package[/FONT]- not taking the dependancies into account.

So, yeah- in answer to your original question, it should work fine. It just won't remove the dependencies.

---

### Post by u04f061 on 2006-08-16
> **AirRaven said:**
> Basically, if you install something with apt-get, it doesn't remember the dependencies it retrieved whilst retrieving the package- so if you use [FONT="Courier New"]apt-get install kopete[/FONT], it'll get some of the Qt libraries and so on, but when you type [FONT="Courier New"]apt-get remove kopete[/FONT], it'll simply remove the Kopete package without removing the Qt libraries it depended on.

what aptitude will do when we install two things depending on one?
i mean if i install geda first with aptitude and it depends upon let gnucap.it will install both.then i install oregano with aptitude it also depends on gnucap.when i remove geda using aptitude ,with oregano remaining in my pc. would it remove gnucap without noticing that oregano depends on it?

also if i install oregano with apt then i remove geda with aptituse again what would be the case??

thanx in advane

---

### Post by arjun.shankar on 2006-08-17
The whole thing is like a tree.

Visualize A at the root, and B and C are it's branches. D is a leaf on branch B.

So:

D depends on B
B and C depend on A

Lets say, currently none of A,B,C,D are installed.

If you ask to install D, then A, and B will get installed (no matter what you use, apt-get or aptitude)

Now, if you ask to install C, it will install without trouble.

If you ask to remove D now, aptitude wont remove A (which it had installed earlier, to satisfy D's deps) because a currently installed package (namely C) still depends on it.

Hope that clears it up.

---

