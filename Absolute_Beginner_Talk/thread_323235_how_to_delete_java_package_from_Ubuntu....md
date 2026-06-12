---
title: "how to delete java package from Ubuntu..."
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by Fawad Nazir on 2006-12-21
Hi All,

I have installed Ubuntu and now would like to uninstall current java-runtime or jvm to install a new version.

fawad@nicta-laptop:~$ /usr/bin/java
Usage: gij [OPTION] ... CLASS [ARGS] ...
          to invoke CLASS.main, or
       gij -jar [OPTION] ... JARFILE [ARGS] ...
          to execute a jar file
Try `gij --help' for more information.

I tried different command like $dpkg -r (but dont know what exactly to put in here)

ill be thankful for any help.

---

### Post by jvc26 on 2006-12-21
Have you installed java at all beyond how things are when you get the system up and running? If not then you have nothing to think about really just add in the new version of JRE/JDK whichever you need:
1.5
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox)
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_JRE_v5.0_Update_10](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_JRE_v5.0_Update_10)
JDK 1.5
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Java_Development_Kit_.28JDK.29_v5.0](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Java_Development_Kit_.28JDK.29_v5.0)

Or 1.6 (via a more complex route:
[http://www.ubuntuforums.org/showpost.php?p=1877195&postcount=15](http://www.ubuntuforums.org/showpost.php?p=1877195&postcount=15)

Il

---

### Post by Fawad Nazir on 2006-12-21
No i have not installed java after installing Ubuntu. So you mean i should just install the new version of java and it will upgrade the previous one?

---

### Post by jvc26 on 2006-12-21
Well when I first installed ubuntu I installed the 1.5 JRE and later the JDK with no problems whatsoever, and then recently put the JDK 1.6 on for some extra bits and pieces and to play about with the new release. (via the link posted above) I just went for it there was no problems updating - there isnt is a JDK on there to start with and possibly not a JRE.
Il

---

### Post by Fawad Nazir on 2006-12-21
Thanks a lot, It did work.

---

