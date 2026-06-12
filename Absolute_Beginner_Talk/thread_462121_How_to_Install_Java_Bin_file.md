---
title: "How to Install Java Bin file?"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by sibot on 2007-06-02
Hey,
I needed the java software, for running limewire. So i downloaded it directly from the Sun website. The download file was " jre-6u1-linux-i586-rpm.bin "

So i installed alien, and wrote this in the terminal

sudo alien ~/Desktop/jre-6u1-linux-i586-rpm.bin

Somehow i get an error saying "Unknown type of package, jre-6u1-linux-i586-rpm.bin."

I know alien can open rpm files, can it open bin files too? if not, then what should i use?

---

### Post by taurus on 2007-06-02
```
cd ~/Desktop
sudo cp jre-6u1-linux-i586-rpm.bin /opt
cd /opt
sudo sh ./jre-6u1-linux-i586-rpm.bin
sudo update-alternatives --config java
(And pick the one you just installed as your default version.)
java -version
```

But if you are running Feisty, then install it with

```
sudo aptitude update
sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts
java -version
```

---

### Post by viciouslime on 2007-06-02
I think the bin contains the rpm and you have to extract it first, but this is all very messy. Sun Java 6 (i.e. that you've just downloaded) is already in the repos, so just install it as you would anything else, through synaptic. :D

---

### Post by sibot on 2007-06-02
what does "sudo aptitude" do?

---

### Post by zvacet on 2007-06-02
Go to the synaptic and in search box type SUN.After that you will see all versions of JAVA wich are in synaptic.Choose one you want to install by clicking to white box on the left.

---

### Post by sibot on 2007-06-02
thats all cool, but what about the file i downloaded? How do i open that? 

Btw i tried that terminal code and this is what i got 

> 
Couldn't find any package whose name or description matched "sun-java6-jre"
Couldn't find any package whose name or description matched "sun-java6-plugin"
Couldn't find any package whose name or description matched "sun-java6-fonts"


---

### Post by taurus on 2007-06-02
> **sibot said:**
> thats all cool, but what about the file i downloaded? How do i open that? 

Btw i tried that terminal code and this is what i got

Can you include the exact command that you ran when you got that error message?

Which release are you running?

---

### Post by sibot on 2007-06-02
I'm running on Fiesty Fawn

The command was

sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts

---

### Post by taurus on 2007-06-02
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```
Otherwise, Search for java in synaptic, System -> Administration -> Synaptic Package Manager.

---

### Post by sibot on 2007-06-02
Hey taurus, thanks for all the help. But, I needed to know how can i open .bin files in ubuntu. Thing is, I am running on a very slow connection and its very hard for me to download things. It took me 1/2 to download the .bin file for java, and if i could make use out of it, it wouldnt get any better.
Thanks!

---

### Post by lepidopteraphobiac on 2007-06-02
this might help:
[http://ubuntuforums.org/showthread.php?t=412275&highlight=bin+install](http://ubuntuforums.org/showthread.php?t=412275&highlight=bin+install)

had the very same problem myself and it turned out to work quite well...

---

### Post by taurus on 2007-06-02
> **sibot said:**
> Hey taurus, thanks for all the help. But, I needed to know how can i open .bin files in ubuntu. Thing is, I am running on a very slow connection and its very hard for me to download things. It took me 1/2 to download the .bin file for java, and if i could make use out of it, it wouldnt get any better.
Thanks!

From my #2 post.

```
cd ~/Desktop
sudo cp jre-6u1-linux-i586-rpm.bin /opt
cd /opt
**sudo sh ./jre-6u1-linux-i586-rpm.bin**
sudo update-alternatives --config java
(And pick the one you just installed as your default version.)
java -version
```

---

