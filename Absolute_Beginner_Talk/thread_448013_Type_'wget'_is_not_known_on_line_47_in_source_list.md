---
title: "Type 'wget' is not known on line 47 in source list /etc/apt/sources.list"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by borned08 on 2007-05-18
I just installed ubuntu, trying to make the switch from xp. in the process of installing automatix2 and this error came up.

E: Type 'wget' is not known on line 47 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

reading other posts I was able to get to the source list
the first line is line 47:

wget [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key)

gpg --import automatix2.key
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty maindeb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main”
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main”

i am not sure what else is needed.
thanks.
Eric

---

### Post by taurus on 2007-05-18
> **borned08 said:**
> 
wget [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key)

gpg --import automatix2.key
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty maindeb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
&#8220;deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main&#8221;
&#8220;deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main&#8221;


All those lines shouldn't be in your /etc/apt/sources.list.  Not sure what you did.  Everything you need you can install using synaptic BUT if you must install Automatix, then you only need one line in your /etc/apt/sources.list.

```
deb http://www.getautomatix.com/apt feisty main
```

---

### Post by irish_flu on 2007-05-18
OK sorry about this, because I haven't installed automatix in a long time and I forget what the instructions are.

However, I am pretty sure that "wget" line doesn't belong in your sources.list - it should be typed into the terminal in order to "get" the key.

Can you post a link to the instructions you're using?

---

### Post by jm2003uk on 2007-05-18
Agree with above. Also, these command should be run individually from the terminal (if you still need too):

wget [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key)

gpg --import automatix2.key


You may need sudo for the second command (sudo gpg --import automatix2.key)


Hope this helps!

---

### Post by borned08 on 2007-05-18
Thank you all for your help. I cannot believe the speed in your responses. Let's just say the other os I used to have never had this kind of support. I'll try reinstalling. Thanks again.

---

### Post by zvacet on 2007-05-18
No need for reinstall.Just take taurus advice and you will be fine.

---

### Post by ronbrooks on 2007-05-18
I am also having trouble installing automatix2 When I enter the wget [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key) I get this.


Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.

My source file has the right address in it (deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main)

Dose anyone know why I am getting the Invalid host name.

---

