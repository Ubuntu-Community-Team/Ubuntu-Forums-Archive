---
title: "Fiesty &amp; Java"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by captgadget on 2007-04-22
I upgraded to Fiesty from Edgy and most everything works fine except Java. When I go to a web page that needs Java it just locks up the harddrive and sits there and I can't close anything with the mouse. I can't even do a control, atl, f2 for a console. Anyone else encounter this?

---

### Post by hyper_ch on 2007-04-22
have you java installed?

I have following isntalled:

```

aptitude install sun-java6-jre sun-java5-jre

```

and I haven encountered yet problems with Java...

---

### Post by zvacet on 2007-04-22
> Click Applications &#8594; Add/Remove. In the top right, change the setting to All available applications. Then select Other in the left panel and then select the Ubuntu restricted extras package. Click OK.

With this you will get Java and some other things.

---

### Post by Seisen on 2007-04-22
My java works fine too, what version of java do you have installed.

---

### Post by Druke on 2007-04-23
prolly has to do with default java being rather out of date

---

### Post by nazish on 2007-04-23
instead of using the ubuntu supplied JAVA you can dowload it from the SUN server. This way you can update it whenever you want it without waiting for the ubuntu team to update JAVA in their repositories.

the steps are,
1.) Download Java from [http://javadl.sun.com/webapps/download/AutoDL?BundleId=11187](http://javadl.sun.com/webapps/download/AutoDL?BundleId=11187)
this is the latest version.

2.) Open terminal and goto location where you  have downloaded the file and run it. Extract it to your location of your choice. Please select it carefully so that you dont delete it by mistake.

3.)after extraction goto
jre1.6.0_01->plugin->i386-ns7

here you wiil find a file called as libjava..._oij.so

right click on this file and select the make link option.
A new link will appear copy this to /home/yourusername/.mozilla/plugins/
and rename this link to libjavaplugin_oji.so
restart firefox and your java is working like never before

---

### Post by hyper_ch on 2007-04-23
it's better first to try the sun-java packages that are available in the official repos. If that doesn't help then another version directly from Sun could be considered.

---

