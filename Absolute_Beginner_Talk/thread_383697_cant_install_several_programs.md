---
title: "cant install several programs"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by familyjules74123 on 2007-03-13
hello all,

I just installed edgy eft and when I tried to install several different programs i got a message before it even tried to download the package that said that my system could not support it.  I have installed these programs on dapper drake on this computer before installing edgy.  So, I was wondering what the problem was if anyone has any idea.  Also, I was wondering if someone could outline the basic improvements from dapper to edgy.

---

### Post by taurus on 2007-03-13
Can you share the name of those programs and how do you try to install them, synaptic/apt-get/aptitude?

---

### Post by ohzopants on 2007-03-13
In your synaptice sources files (/etc/apt/sources.list) you have to change "dapper" to "edgy".  Essentially your sources file says which version you are using and checks the repositories for packages that work with that version.

---

### Post by familyjules74123 on 2007-03-13
i can only recall one off-hand; I am on my windows partition right now.  That is xxms the program that is like winamp.

I tried to install them using synaptics package manager.

> In your synaptice sources files (/etc/apt/sources.list) you have to change "dapper" to "edgy". Essentially your sources file says which version you are using and checks the repositories for packages that work with that version.

Would this be the problem even if it was an install and not an upgrade?  Because I didnt upgrade, I just installed edgy right over the dapper edition.

---

### Post by ohzopants on 2007-03-14
No, it's not a problem if it's a new install.  You do need to add the proper repositories to the list though.  How are you trying to install them? What errors do you get?

---

### Post by familyjules74123 on 2007-03-14
I am using synaptics to install them.

the error message is something like "your system cannot install this".  Again, I am on my windows partition posting this so I'm not sure exactly what it says.  I know my system can use them though because I installed them when I was using Dapper.

---

