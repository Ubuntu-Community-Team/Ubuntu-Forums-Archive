---
title: "help with Tomcat plugin ."
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by sjosh_theone on 2007-12-01
Hello guys .
I installed eclipse from synaptic .  By the way I am using ubuntu 7.04. Synaptic took care of everything. 
Now I want Tomcat 5.5 plugin for eclipse. I can see the eclipse.tomcat dir in my eclipse dir. 
Where the hell is my bin folder in it???I cant even locate my server.xml file. I checked my /usr/share/tomcat folder but to no avail. 
do I need install tomcat using apt-get or aptitude and then download the plugin???

---

### Post by aktiwers on 2007-12-02
Remember you can always run the whereis command:
```
whereis eclipse
```

My plugin folder is located at:
> /usr/lib/eclipse/plugins

And if you look in /usr/lib/eclipse/ you will see some of the common folders.

Else the locate command can be useful here as well:
```
locate eclipse
```

But to be honest with you, I normally install it manually, so I have it all in my home folder. Just makes it a lot easier.

---

