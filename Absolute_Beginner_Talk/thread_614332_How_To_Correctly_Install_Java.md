---
title: "How To Correctly Install Java?"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by chaos.- on 2007-11-15
Well i just reformated my linux drive as i installed Xubuntu on it previously but now i plan to install Ubuntu 7.10 and i was wondering what is the right way to install Java and JRE and the plugin for Firefox 

last time i installed java on xubuntu i had numerous problems and the plugin did not work and even the links were broken

so any help would be great :)

---

### Post by LaRoza on 2007-11-15
Install it through Add/Remove. It should be easy. I installed:

```

sudo aptitude install sun-java6-jdk

```

because I also do programming, but you probably don't need all that.

---

### Post by chaos.- on 2007-11-15
nop i do not do programming so you mind telling me how to make the plugin for java work because last time it didnt

---

### Post by LaRoza on 2007-11-15
It just worked on my end, so I am not sure what you did.

In Add/Remove type "java" and install Java Web Start (that is what I have, among other things).

---

### Post by rsambuca on 2007-11-15
If you want to instal java, as well as some codecs, etc. all at once, you can just```
sudo apt-get install xubuntu-restricted-extras
```

---

### Post by chaos.- on 2007-11-15
and this should also get the firefox plugin for java and set it up correctly?

---

### Post by LaRoza on 2007-11-15
> **chaos.- said:**
> and this should also get the firefox plugin for java and set it up correctly?

It did for me.

---

### Post by whitespy9 on 2007-11-15
::::::THREADJACKING:::::::::::

Is there a list of what is available via apt-get?

I installed the java 6 sdk w/ netbeans (know a better compiler?) from a download via sun.

but a "sudo apt-get install sun-java-sdk-netbeans" would freaking rock on... :guitar:

---

### Post by LaRoza on 2007-11-15
> **whitespy9 said:**
> ::::::THREADJACKING:::::::::::

Is there a list of what is available via apt-get?

I installed the java 6 sdk w/ netbeans (know a better compiler?) from a download via sun.

but a "sudo apt-get install sun-java-sdk-netbeans" would freaking rock on... :guitar:

```

sudo aptitude install sun-java6-jdk

```

This gets you the compiler among many other things.

Netbeans is not a compiler, so if you want an IDE, you'll have to get that separately. I don't use IDE's, so I don't know what is "good". Look in the programming talk section and the stickies for info on IDE's.

---

### Post by Inxsible on 2007-11-15
you dont really need the jdk if you are not planning on developing java code.
you can simply install the jre```
sudo aptitude install sun-java6-jre
```

---

### Post by Inxsible on 2007-11-15
> **whitespy9 said:**
> ::::::THREADJACKING:::::::::::

Is there a list of what is available via apt-get?

I installed the java 6 sdk w/ netbeans (know a better compiler?) from a download via sun.

but a "sudo apt-get install sun-java-sdk-netbeans" would freaking rock on... :guitar:
As far as IDE's are concerned, look for eclipse. Its the best IDE IMHO and its in the ubuntu repos (although one version older )

---

