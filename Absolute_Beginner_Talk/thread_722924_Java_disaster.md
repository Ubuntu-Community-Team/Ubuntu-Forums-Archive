---
title: "Java disaster"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by Garmuar on 2008-03-13
I am new to ubuntu and very confused with synaptic manager.  
In an effort to get java to work for Pogo, My wife started intalling java packages.  Now I have  a java 1.4, a 5, a 6 and an Icetea java installed and add/remove programs will not uninstall them.  It says an app. is using java at the moment and to use synaptic to uninstall java and the application.

I open synaptic and can't find any of the installed Java on the list.  I tried the filters, "installed" and everything and.......nothing.   How else can I remove all of this and start over??  

By the way, Pogo still didn't work.  LOL

Thanks in advanced.

---

### Post by Hospadar on 2008-03-13
probably what was installed are the sun-java packages.  try (in synaptic) going to "Search" choose "Name" from the drop down menu and search for "sun"  look for packages labled "sun-java-<something or other>"

As for icetea, do the same kind of search for "icetea" (not as sure about that one, but it's there somewhere.)

Another thing, to make your shell (the thing which executes programs) actually use a certain java version when something calls "java", you need to run (in a terminal Applications->Accessories->Terminal) run ```
sudo update-alternatives --config java
``` and choose the java version you want.  You can do this even before you uninstall the unwated javas (you may want to to make sure you keep the right version).  To test which version of java is currently in use, try doing "java --version"

One last thing, the default java jvm, I foget what it's called, g-something, is needed for a lot of system things, so you can't get rid of it, don't worry though, when uninstalling packages, it is obviously different from the sun java packages.

---

### Post by dstin1 on 2008-03-13
I am new to this to but when I installed java I just clicked the install missing plugin in Firefox and that worked just fine.

When I tried to install java in another distro I had the same problem I had 4 versions of java and the icetea thing and still couldn't view pages, then I changed to Unbutu and had no problems with just installing the plugin

---

### Post by Garmuar on 2008-03-13
I was able to select sun java 6 but when I checked version afterward I got this:
 java --version
Unrecognized option: --version
Could not create the Java virtual machine.

I typed about:plugins in firefox and the only java plugin was the Icetea not the sun java 6 plugin and runtime that I selected.

---

### Post by kostkon on 2008-03-13
> **Garmuar said:**
> I am new to ubuntu and very confused with synaptic manager.  
In an effort to get java to work for Pogo, My wife started intalling java packages.  Now I have  a java 1.4, a 5, a 6 and an Icetea java installed and add/remove programs will not uninstall them.  It says an app. is using java at the moment and to use synaptic to uninstall java and the application.

I open synaptic and can't find any of the installed Java on the list.  I tried the filters, "installed" and everything and.......nothing.   How else can I remove all of this and start over??  

By the way, Pogo still didn't work.  LOL

Thanks in advanced.

Maybe some process is running in the background that actually uses Java. Go to *System -> Administration -> System Monitor* and at the *Processes* tab, check for any application that you may think is running and uses Java.

If you find any process like that, try to kill it.

After that, you should be able to remove any of the java packages that you have installed and you don't want anymore. The packages you should install or keep are the *sun-java6-jre* and *sun-java6-plugin*.

Furthermore, you should open a terminal and do what *Hospadar* has recommended
```
sudo update-alternatives --config java
```
and select the Sun java as the default.

---

### Post by Garmuar on 2008-03-13
I figured out how to change the repositories in synaptic and found Icetea and the Java packages.  I could then uninstall all but java 6, which I already had as default.  After this, fire fox was finally able to ditch Icetea and automaticlly started using the java 6 plugin.

Thank you all for the help.  Pogo works great now.  My wife will be happy.  LOL

---

