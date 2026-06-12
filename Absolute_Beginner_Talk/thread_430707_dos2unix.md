---
title: "dos2unix"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by O-pos on 2007-05-02
Hello,

I have Feisty 7.04. I need to install dos2unic, how and can I do that? The only thing I know is that in Debian this program is contained in package "tofrodos"..  :(

---

### Post by 5-HT on 2007-05-02
It's in the repos as *tofrodos*, same as in Debian.

```
sudo aptitude install tofrodos
```

---

### Post by Cypher on 2007-05-02
In Ubuntu, it's the same thing, go to System->Administration->Synaptic Package Manager and search for "tofrodos" and install it. Or 
```

sudo apt-get install tofrodos

```
I think you will find [packages.ubuntu.com]("http://packages.ubuntu.com/") useful to search for packages in general or for packages containing certain files.

---

### Post by dolphs on 2007-05-19
what if you are running server and dont have internet available yet since it doesnt seem to be available on cdrom (7.04)?

---

### Post by Najand on 2007-05-19
Download the package from: [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and take it to the other computer by a flash memory.

---

### Post by dolphs on 2007-05-19
cheers I was afraid of this, so in my case installing WLAN it is needed to have the linux drivers availabe as well tofrodos, doing a "dpkg -i tofrodos*.deb" later. okidoki will add it to disk ;D

---

### Post by chamberlain2006 on 2007-05-19
Do you need some help with your wireless?

---

