---
title: "Java Problems"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by wintersenda on 2008-02-22
Hi,
    I am trying to run some java applications and i keep getting the following error:

Failed to load Main-Class manifest attribute from datastudio-install.jar

I tried running the sh file directly but a blank box just pops up. Anyone any ideas? Thanks a million.

---

### Post by toa on 2008-02-22
Make sure you have, jave completely installed, i use Automatix and he does the job

---

### Post by jeffus_il on 2008-02-22
Did a google search on "manifest attribute java" on came up with this:
> [B][SIZE=-1]org.apache.tools.ant.taskdefs[/SIZE] 
Class Manifest.Attribute[/B]

 java.lang.Object
  |
  +--**org.apache.tools.ant.taskdefs.Manifest.Attribute**
**Enclosing class:**[Manifest]("http://www.dpml.net/api/ant/1.6.5/org/apache/tools/ant/taskdefs/Manifest.html")here: [http://www.dpml.net/api/ant/1.6.5/org/apache/tools/ant/taskdefs/Manifest.Attribute.html](http://www.dpml.net/api/ant/1.6.5/org/apache/tools/ant/taskdefs/Manifest.Attribute.html)

 The Manifest class is part of the apache ant stuff. I would use synaptic to search for ant and manifest. Try installing the ant or ant-optional package ...

---

### Post by r4ik on 2008-02-22
I assume you have the extra's enabled,

 How to add extra repositories
[edit]
Menu Method for Adding Repositories

    * Choose distribution-friendly repositories. These are part of the Ubuntu distribution system. This is the recommended method. 

System-->Administration-->Software Sources

Check the repositories you think you will need (main, universe, restricted, multiverse). You probably won't need the 'sources' repository.

    * Add any third-party repositories. Such repositories are not monitored in any way. Some are quite popular, however. Use any third-party repository at your own risk. 

System-->Administration-->Software Sources-->Third-party software-->Add

Add the name of your repository. In this example, we will use Medibuntu, a popular third-party repository not affiliated with Ubuntu in any way.

APT line: deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

    * Download any needed gpg keys and add them to the keylist. This key verifies the repository to your system. The Medibuntu repository (not affiliated with Ubuntu) example is shown: 

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -

If so try,

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

In a Terminal.

Good luck !

---

