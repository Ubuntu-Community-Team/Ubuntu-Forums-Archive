---
title: "Azureus doesn't show plug-in installer option in menu"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by whee on 2007-04-27
I wanted to install a plug-in for Azureus in Feisty the way i always did in Dapper.
Plug-ins>install(or something similar)
But in Feisty that option doesn't seem to appear in Azureus.
What can be the cause of this and how would one solve this?

---

### Post by whee on 2007-04-27
Anyone has encountered something similar with Azureus?

---

### Post by whee on 2007-04-27
*bump*

---

### Post by Josey on 2007-04-27
azureus has had a lot of problems in ubuntu for quite awhile now and I think the lack of posts may have to do with the fact that most people have stopped using it.

I use ktorrent personally and you can find it in add/remove programs.

---

### Post by whee on 2007-04-27
Does Ktorrent support plugins like Azureus?

---

### Post by LuisGMarine on 2007-04-27
I'm not sure I understand your question.  Is something not working right?  I'm currently using Azureus without any problems, it took a script to get it to work properly, but after that I have not noticed any problems.

---

### Post by Josey on 2007-04-27
> **whee said:**
> Does Ktorrent support plugins like Azureus?

Of course :)

---

### Post by whee on 2007-04-27
> **LuisGMarine said:**
> I'm not sure I understand your question.  Is something not working right?  I'm currently using Azureus without any problems, it took a script to get it to work properly, but after that I have not noticed any problems.

There should be an installation wizard for plug-ins in Azureus under the plugin dropdown menu. (it downloads and installs the selected plug-ins)
But in my installation of Azureus it's not there, so i can't install the plug-ins that i used to install under Windows and Dapper.

---

### Post by dve on 2007-06-14
you can install the plugins manually. Just copy the plugins (.jar files) to plugins directory in the subfolder of the same name as the plugin without the .jar extensions. Below is an example with the html gui plugin (azhtmlwebui_0.7.6.jar) downloaded to /tmp/ with the user jko
```

jko@heidi:/tmp$ mkdir /home/jko/.azureus/plugins/azhtmlwebui/
jko@heidi:/tmp$ cp azhtmlwebui_0.7.6.jar /home/jko/.azureus/plugins/azhtmlwebui/azhtmlwebui.jar

```
note that I dropped out the version number  in the directory _and_ the .jar file.

restart the azureus for changes to take place.

Dve

---

### Post by TizzyD on 2007-07-02
we're still using it.  ;)

I have to note that I was having the same issue.  I realized the file I was trying to install was actually an incomplete file, and so the same sort of problem arose.  When I deleted that file and retrieved a complete one--in this case azhtmlwebui--it worked just fine.

---

