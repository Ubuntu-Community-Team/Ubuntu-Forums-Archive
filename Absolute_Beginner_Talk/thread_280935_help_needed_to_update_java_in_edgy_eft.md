---
title: "help needed to update java in edgy eft"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by Ben4ever on 2006-10-20
I'm using Ubuntu 6.10 (edgy eft) but i have a problem installing java 5:-k 
I've downloaded the file of the java homepage, but i don't know how to run automatix to install it. i really need java 5 to run frostwire/limewire in edgy eft.:confused: 
please if you know the answer, reply

Ben4ever

---

### Post by Ben Sprinkle on 2006-10-20
Right click the .bin=>properties/attribs=>enable execute
```

./jrebin.bin

```
Will extract in current directory. To use type like:
```

'/home/$USER/Desktop/jre/bin/java' '/home/$USER/Desktop/classname'
```

---

### Post by Perfect Storm on 2006-10-20
NB: (important) requires that you have universe/multiverse enable in your sourcelist.

Download Java Runtime Environment (JRE) 5.0 Update 9: [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp) pick **Linux self-extracting file**. Download it to your **Desktop**.

```
cd Desktop
sudo apt-get install build-essential
sudo apt-get install fakeroot java-package java-common
fakeroot make-jpkg jre-1_5_0_09-linux-i586.bin
sudo dpkg -i sun-j2re1.5_1.5.0+update09_i386.deb
sudo update-alternatives --config java

```
When asking for which version you want to choose pick;
```
  3        /usr/lib/j2sdk1.5-sun/bin/java
```

Testing;
```
java -version
```


Making a Launcher for Java Control Center;
```
sudo nano /usr/share/applications/java.desktop
```

fill in;

[b]
[Desktop Entry]
Name=Java Control Center
Comment=Java Options & Configuration.
Exec=sh /usr/lib/j2re1.5-sun/bin/ControlPanel
Icon=
Terminal=false
Type=Application
Categories=Application;System;
[/b]

Save and exit. <ctrl> + <o> | <ctrl> + <x>
You can find it now under Applications tab ---> System Tools.

---

### Post by Ben Sprinkle on 2006-10-20
I see you got a new avatar AI.
Anyway use what AI said. ^

---

### Post by Perfect Storm on 2006-10-20
I have used this avatar before, but it's been awhile ;)

---

### Post by Ben Sprinkle on 2006-10-20
Oh noes, you changed your ubuntu-love sig!
I liked seeing that as it matched your avatar.
I wish that one girl was still around to make those neat power puff avatars. They rock.

---

### Post by Perfect Storm on 2006-10-20
Kassatra isn't an admin anymore, she usually made our Power Puff avatars :mrgreen: ...I had a very evil one (as one I requested) 8) 



I still have my sig pic and old avatar, which I'll use again in near future.

---

### Post by Ben Sprinkle on 2006-10-20
Well why isn't she here anymore! :frown: :icon_frown: :'(!
I want one! :'(
Well, she should come back and make a request thread or something. I think she is awsome.

---

### Post by Ben4ever on 2006-10-20
when i do: sudo dpkg -i sun-j2re1.5_1.5.0+update09_i386.deb
it says that there is no such file or directory
i don't understand anything of it anymore](*,)

---

### Post by Ben Sprinkle on 2006-10-20
```

sudo dpkg -i sun-j2re1.5_1.5.0+update09_i386.deb

```
Provide your location in it...
```

sudo dpkg -i '/home/$USER/sun-j2re1.5_1.5.0+update09_i386.deb'

```
Is an example.

---

### Post by goofla on 2006-11-09
AI,

Thank you for this very accurate and knowledgable post! I too ran the Java installer out of the box and although it ran fine, I could not launch apps as an error "OOps you do not have java yada yada yada installed" so your post was the sure fix!

---

### Post by Perfect Storm on 2006-11-09
Thanks ^_^
It's always nice to get replies that tells it works, it keeps the spirit up :)

---

### Post by robert114 on 2006-11-22
Artificial Intelligence Thanx this howto goes to my websit for future use!

---

