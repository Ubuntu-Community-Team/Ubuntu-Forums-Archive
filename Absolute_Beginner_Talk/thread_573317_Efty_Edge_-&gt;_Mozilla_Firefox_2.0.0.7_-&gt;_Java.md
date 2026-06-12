---
title: "Efty Edge -&gt; Mozilla Firefox 2.0.0.7 -&gt; Java (any upgrade from 1.4.2)..."
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by JollyMambo on 2007-10-11
All that I am trying to do is to get any upgrade from the java 1.4.2 onto Mozilla Firefox browser running Edgy Eft Ubuntu.

What are the steps towards doing this?  Are there other methods available than just one?  I am relatively new to Linux based OS's and could use some help.

---

### Post by steve.horsley on 2007-10-11
Use synaptic (System->Administration->Synaptic) and search (name only) for "sun" or "jre". Mark and install sun-java6-jre and sun-java6-plugin. That should do the trick.

---

### Post by stchman on 2007-10-11
> **JollyMambo said:**
> All that I am trying to do is to get any upgrade from the java 1.4.2 onto Mozilla Firefox browser running Edgy Eft Ubuntu.

What are the steps towards doing this?  Are there other methods available than just one?  I am relatively new to Linux based OS's and could use some help.

2.0.0.7 Firefox won't be in the repos as that update is Windows specific.  2.0.0.6 is the latest for Ubuntu.

Do this to install the 1.5 JRE and SDK.

```
sudo apt-get install sun-java5-bin sun-java5-jre sun-java5-jdk sun-java5-fonts sun-java5-plugin
```

This will install the Firefox plugin as well.

---

