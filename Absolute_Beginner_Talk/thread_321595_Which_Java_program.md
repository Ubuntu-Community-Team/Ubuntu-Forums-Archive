---
title: "Which Java program?"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by OrangeCrate on 2006-12-19
My apologies, a search of the forum is not giving me the answer I'm looking for...

There are two Java plug-ins available:

Java Web Start 1.4
Sun Java 5.0 Runtime

Which one should I install for Firefox, or should I install both?

Edit:

I have gone ahead and installed 5.0, from "add/remove", should I also install 1.4?

---

### Post by LookTJ on 2006-12-19
You can make a deb package of Sun JRE 6, which I don't know how.

---

### Post by jvc26 on 2006-12-19
lol, the process that Taylor is talking about is here (but thats to do with the JDK 1.6):
Post #15
[http://www.ubuntuforums.org/showthread.php?t=316980&page=2](http://www.ubuntuforums.org/showthread.php?t=316980&page=2)

If you just want the java plugins for firefox have you tried here:
[http://www.ubuntuforums.org/showthread.php?t=316980&page=2](http://www.ubuntuforums.org/showthread.php?t=316980&page=2)

Or if you want the JRE and JDK 1.5 (available from the repos) try:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_JRE_v5.0_Update_10](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_JRE_v5.0_Update_10)
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Java_Development_Kit_.28JDK.29_v5.0](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Java_Development_Kit_.28JDK.29_v5.0)

Not sure exactly what you're after hope that helps :),
Il

---

### Post by OrangeCrate on 2006-12-19
> **Illuvator said:**
> 
Not sure exactly what you're after...
Il

Thank you for your response.

As I was setting up Dapper, I found them on the repositories, and as I mentioned in my "Edit:", I went ahead and installed Java 5.0 Runtime.

My question was, and still is, should I also install Java Web Start 1.4?

---

### Post by chinocracy on 2007-02-05
I think only one is needed. I installed my Java 1.4 via downloading debs and manually installing them. I tried it on the Java 5, it didn't seem to work. So I guess only one can be installed at one time.

---

### Post by phossal on 2007-02-05
You can install multiple Java's. I recommend downloading version 6 directly from Sun, though, rather than using the packages. Version 6 comes with Java Web Start, and the Firefox plugin, although installing the JDK is just a little more work (when you get it from SUN).

Not *every* JRE or JDK has to be *registered* with your system (ie update-alternatives), but can exist as a stand-alone. You can, in fact, run multiple java-enabled programs, like Tomcat, eclipse, etc. That's the cool thing about Java, it's plug-and-play (building block style) like Ubuntu (and *nix) in general.

---

### Post by Perfect Storm on 2007-02-05
> **chinocracy said:**
> I think only one is needed. I installed my Java 1.4 via downloading debs and manually installing them. I tried it on the Java 5, it didn't seem to work. So I guess only one can be installed at one time.

You properly forgot to reconfigure which version of Java your system should use by default.

---

### Post by phossal on 2007-02-05
> **Artificial Intelligence said:**
> You properly forgot to reconfigure which version of Java your system should use by default.

You mean, after installing JDK 5.0 from the repositories, it doesn't update update-alternatives as the default? That's *horrible*. It's even less useful than I thought.

If that's really so, the OP has run this?:
```
sudo update-alternatives --config java
```

What about his Java plugin? Does he have to create the symlink himself? If so, that would make downloading the packages utterly useless - a complete waste of time since you can pull 6.0 (and any updates) right from SUN. I knew I liked *my* method, but I was referring total neophytes to the packages thinking it was their quick fix.

---

### Post by Perfect Storm on 2007-02-05
Well my experience everytime I run multiply Java on my machine (espicially when running 1.4 not sun, sun1.5 or sun1.6) you need to tell it which one to use by default.

---

### Post by OrangeCrate on 2007-02-05
I installed 1.5, and everything is working fine. Thanks for the responses.

---

### Post by chinocracy on 2007-02-06
> **Artificial Intelligence said:**
> You properly forgot to reconfigure which version of Java your system should use by default.

Actually, I didn't pay attention to some of the messages. I have 1.4. When I tried the Java 5 package sun-java-jre, it listed 2 dependencies as missing... which are sun-java-jre and sun-java-bin, the very same files I was trying to install! So it seems the two files have to be installed together, which is probably more smoothly done via Synaptic or Add/Remove, and these don't access my local files. 

By the way, I'm still not that familiar with system tweaking, so how could I configure the default Java version? Thanks.

BTW, good going, Orangecrate.

---

### Post by phossal on 2007-02-06
If you're using the Ubuntu "system", the various JRE's are managed through update-alternatives, which is configured like so:
```
sudo update-alternatives --config java
```
You view the alternatives like this:
```
sudo update-alternatives --display java
```

And you can manually install new ones, using the --install flag, which I've shown how to do in a tutorial about manually downloading and installing the JDK and eclipse - linked in my sig.

---

### Post by bonzini on 2007-02-06
> **OrangeCrate said:**
> Thank you for your response.

As I was setting up Dapper, I found them on the repositories, and as I mentioned in my "Edit:", I went ahead and installed Java 5.0 Runtime.

My question was, and still is, should I also install Java Web Start 1.4?

Java Web Start is completely different and distinct from Java Runtime Environment.

Web Start lets application developers build real applications (not just applets) that can be deployed over the net and managed via Web Start.

If you want to read about it, take a look at:

[http://java.sun.com/products/javawebstart/index.jsp](http://java.sun.com/products/javawebstart/index.jsp)

OK your question: "should I install Java Web Start"?  For Web Start to be useful to you, you have to find an application you want that's packaged up for use with Web Start.  Or of course you can write your own applications and package them up with Web Start, but then you'll need a bit more than JRE :-)  If you don't know of a specific need for it, then you probably don't need it (you can always install it later if you find that you need it).

If all you want to do is make sure that your browsing experience is complete, then it doesn't hurt to install it.  You might stumble upon a Java app one day that requires it to deploy.

---

### Post by phossal on 2007-02-06
> **bonzini said:**
> Java Web Start is completely different and distinct from Java Runtime Environment.

True, *sort of*. It's totally different and distinct in the same way the plugin for Firefox is. With JDK 6, javaws is included, just like the .so plugin. If you download the new JDK right from SUN, you essentially *have* installed the JRE, the plugin, and Web Start. It's just a matter of altering your path and creating links.

---

### Post by morningboat on 2007-02-06
Java Web Start appeared ever since Java 1.4  After that, the Java Web Start is bundled with the Java Runtime (1.4, 1.5, and of course 1.6), so that if you installed the Sun java, you automatically get the Java Web Start. 

To install the Java Runtime in Unbuntu Dapper, as well as the firefox plugins, please refer to this link: [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox)

---

### Post by phossal on 2007-02-06
> **morningboat said:**
> Java Web Start appeared ever since Java 1.4  After that, the Java Web Start is bundled with the Java Runtime (1.4, 1.5, and of course 1.6), so that i***f you installed the Sun java, you automatically get the Java Web Start. ***

To install the Java Runtime in Unbuntu Dapper, as well as the firefox plugins, please refer to this link: [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox)

I just said that. *javaws* is the executable.

---

### Post by chinocracy on 2007-02-08
> **phossal said:**
> 
```
sudo update-alternatives --config java
```
```
sudo update-alternatives --display java
```
And you can manually install new ones, using the --install flag, which I've shown how to do in a tutorial about manually downloading and installing the JDK and eclipse - linked in my sig.

Thanks for the tip. Will try out later. 

And thanks for the explanations on Java. Something a non-developer has to learn every day.

---

### Post by chinocracy on 2007-02-25
Now I have 1.4 Webstart, Java 5 and Java 6 all installed at once! I think I confused my computer. I wonder how to configure the default version...

---

