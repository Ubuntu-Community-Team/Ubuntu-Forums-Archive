---
title: "java install"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by 01queen on 2008-04-03
Hey. I am having a little problem installing java
I followed these directions

[http://java.com/en/download/help/5000010500.xml#install](http://java.com/en/download/help/5000010500.xml#install)

but when I get to the part of enabling I see the step
Go to Edit > Preferences. Under Advanced category > Select Enable Java 


I do not see enable Java.


Any help would be great!

---

### Post by privaterolf on 2008-04-03
I'd use the Synaptic Package Manager...I've never actually had to install Java.

Anyway:

System-->Administration--->Synaptic Package Manager

Once there, hit Ctrl+F and search for java.

---

### Post by Hospadar on 2008-04-03
you'll want the"sun-java6" flavor of java probably, that's the latest sun version.  It'll generally get the best performance and compatability.

---

### Post by 01queen on 2008-04-04
so how do I install java to work? I went to system, administrator, and then I dont see the package thing you were talking about.  thanks!

---

### Post by zvacet on 2008-04-05
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by 01queen on 2008-04-05
okay i did that. nothing happened tho. still nothing under there
or do I need to put in my cd or anything like that?

do I need to restart?

---

### Post by Tyke91 on 2008-04-05
once you do the above line (install restricted extras) you should have java.

---

### Post by mivo on 2008-04-05
Well, the package names you want are *sun-java6-jre* and *sun-java6-bin*. They should be found in Synaptic. You can also install them from the shell with:

```
sudo apt-get install sun-java6-jre sun-java6-bin
```

If you need Java Webstart on a 64-bit system, this requires additional steps (let us know if that's the case). :)

---

### Post by gandaran on 2008-04-06
> **01queen said:**
> okay i did that. nothing happened tho. still nothing under there
or do I need to put in my cd or anything like that?

do I need to restart?

have you enabled all the ubuntu repository's? that is all you need, then go to synaptic and look up ubuntu-restricted-extras or just sun-java6-plugin, mark for install and click apply.
this is for 32-bit.

for 64-bit you have to install icedtea-java-plugin

---

### Post by kleo skywalker on 2008-04-06
> **01queen said:**
> so how do I install java to work? I went to system, administrator, and then I dont see the package thing you were talking about.  thanks!

Really? There is nothing that says **Synaptic Package Manager** in your **System-->Administration** menu? Does your user account have administrative privileges?
What happens when you go to **Applications-->Accessories-->Terminal** and run ```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by 01queen on 2008-05-31
> **kleo skywalker said:**
> Really? There is nothing that says **Synaptic Package Manager** in your **System-->Administration** menu? Does your user account have administrative privileges?
What happens when you go to **Applications-->Accessories-->Terminal** and run ```
sudo apt-get install ubuntu-restricted-extras
```


when i do that, the gnome manual pops up.

i will try the others when i have the cd

i'm sorry i havent replied in a long time. things have been hetic.

thanks for all your help!

---

