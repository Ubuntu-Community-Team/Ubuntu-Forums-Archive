---
title: "sum-java5-plugin or sun-java6-plugin?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by itchanddino on 2007-04-24
All I really do with java is for websurfing.  Which version should I install?  I've used java5, and I want to use 6, but I'm afraid it's not stable enough.  Thanks!

---

### Post by crimesaucer on 2007-04-24
Java 6 works stable for me.

---

### Post by itchanddino on 2007-04-24
Does anyone know the main differences between the two?  I think I might just install java6 since it's newer and all, but I'm just being curious.

---

### Post by itchanddino on 2007-04-24
Anyone have any experience with these plugins? Thanks!

---

### Post by crimesaucer on 2007-04-24
Well, I had Java5 and went through updates of .8 .9 and .10, and then I missed one upgrade, and when I checked the edgy wiki I saw it had a new Java6.

I just upgraded to keep current with the newest stable release. I maybe saw a little improvement on a site that I use that has a java stream.

On the Feisty wiki you will only see the Java6, so I would just install it: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_J2SE_Runtime_Environment_.28JRE.29_v6.0_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_J2SE_Runtime_Environment_.28JRE.29_v6.0_with_Plug-in_for_Mozilla_Firefox)

I also read somewhere that Sun Java6 helped with some Beryl issues, and even the beta upgrades versions of Java6.01 or .02 betas have even improved more things for Beryl/Compiz. I think you would need the java-package version 0.28 to install the beta upgrades.

But I would just install Sun Java6 now, and then wait until the next stable upgraded versions are on the Feisty wiki page with good instructions of how to upgrade. The betas are more for developers testing.

---

### Post by Sef on 2007-04-24
Java 6 is the default in Feisty.  I would either upgrade to Feisty if you really want Java 6 or wait till it is backported into Edgy.

---

### Post by crimesaucer on 2007-04-24
@ Sef- I thought it was in the repositories. I installed it a while ago in edgy, I could be wrong.


***I'm a beginner at xubuntu, and I'm not a forum administrator so my advice might not be the best, but this is what worked for me and it was really easy.


Follow these instructions of how to install it from edgy's wiki page: 

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_J2SE_Runtime_Environment_.28JRE.29_v6.0_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_J2SE_Runtime_Environment_.28JRE.29_v6.0_with_Plug-in_for_Mozilla_Firefox)

this is all you have to do. Write this in terminal.

```
sudo aptitude install sun-java6-jre sun-java6-plugin
```

then go into Synaptic and do a search for sun-java5-jre and the mozilla plugin, and then mark them for complete removal, and then click apply, and remove them.

...this is where the packages will be in Synaptic:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-30-10.png[/IMG]

remove the plug-in below it too.

*************************************************************

...Now...open up your terminal again and write this:

```
sudo update-alternatives --config java
```

You will now get a list of your java:

Selection Alternative
-----------------------------------------------
1 /usr/bin/gij-wrapper-4.0
2 /usr/bin/gij-wrapper-4.1
+ 3 /usr/lib/jvm/java-gcj/jre/bin/java
* 4 /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 4
Using `/usr/lib/jvm/java-6-sun/jre/bin/java' to provide `java'.

....you will want the star next to the package that says /usr/lib/jvm/java-6-sun/jre/bin/java 

...so select the number that is in front of it, and press enter like it says. (For me it was #4)

Now it should be installed so go and visit a site that uses Java and make sure it works.

---

### Post by mlind on 2007-04-24
If you install Sun java packages provided by Ubuntu, use **update-java-alternatives** instead.

To list all java alternatives
```

update-java-alternatives -l

```

To set sun-java5 as default
```

sudo update-java-alternatives -s java-1.5.0-sun

```

---

