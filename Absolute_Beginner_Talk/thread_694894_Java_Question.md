---
title: "Java Question"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by rkrakora on 2008-02-12
At the risk of getting hammered for asking a Java question that has already been answered 800 times, I'm going for it anyway.  Here is my question:

I am attempting to set up Frostwire, and have successfully downloaded to my machine.  However, it seems I do not have the proper Java version installed.  [1.5]  I went to the Synaptic Package Mgr and each of the Sun Java versions have a little star with the icon, and I get dependency errors when attempting to upload.  

Here is additional info from the command line:

[COLOR="Blue"]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java6-bin: Depends: unixodbc but it is not installable
                 Depends: libstdc++5 but it is not installable
  sun-java6-jre: Depends: java-common (>= 0.24) but it is not installable
E: Broken package[/COLOR]s


How can I correct these unmet dependencies if I cannot install whats needed to correct?

I appreciate any replies!

Best, 
Rich.

---

### Post by taurus on 2008-02-12
While you are in synaptic, go into Settings -> Repositories and put a check mark in front of all the lines except the last one, Source code, and the Cdrom in the bottom window.  Close it and press the Refresh.  Now, see if you can install sun-java6-bin, sun-java6.jre, & sun-java6-plugin.

---

### Post by rkrakora on 2008-02-12
You're good!

Thank you very much.  That worked perfectly.

---

