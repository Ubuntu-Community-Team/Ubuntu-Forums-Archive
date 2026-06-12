---
title: "Java VRM Installation"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by winterj on 2007-01-31
Has anyone had problems installing Java Virtual Machine into Firefox? (dapper) Before i start getting really in depth just wanted to know how you all did the install, maybe there is another way of going about this.

[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml) is the link i'm using to test, when i do manual plugin install, that's when the problems start.

---

### Post by AndyCooll on 2007-01-31
Easiest way to install Java is to use Automatix (see the link in my signature).

:cool:

---

### Post by SinxarKnights on 2007-01-31
Yes. The plug in doesn't seem to work correctly. Even installing the JDK and updating the java home variable didn't work. Use Automatix2, it installed the JVM perfectly for me (on a fresh edgy install).

---

### Post by phossal on 2007-02-03
> **SinxarKnights said:**
> Yes. The plug in doesn't seem to work correctly. Even installing the JDK and updating the java home variable didn't work. Use Automatix2, it installed the JVM perfectly for me (on a fresh edgy install).
That's funny. Installing the JDK (even Version 6, which comes with Web Start), and setting the JAVA_HOME variable doesn't have anything to *do* with the plugin for Firefox. The plugin lives in */path_to_jdk/jre/plugin/i386/ns7/libjavaplugin_oji.so*  and it needs to *go* in */usr/lib/firefox/plugins*

You do that by making a link: (my jdk is /usr/lib/Java6)
```
sudo ln -s /usr/lib/Java6/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins
```

Automatix is *great* and *easy* (supposedly), but perhaps learning something is useful too.

---

### Post by jackrobinson on 2007-02-03
> **phossal said:**
> Automatix is *great* and *easy* (supposedly), but perhaps learning something is useful too.
The truth of the supposition is in the taste.. what YOU NEED to learn is that a lot of users want things WORKING before they are even remotely inclined to start learning..
-JR

---

### Post by phossal on 2007-02-03
> **jackrobinson said:**
> The truth of the supposition is in the taste.. what YOU NEED to learn is that a lot of users want things WORKING before they are even remotely inclined to start learning..
-JR

I assume your comment was some sort of response to my post, since you quoted me and coincidentally used the word "learning". Apparently it isn't obvious to you that I *take it for granted* users want things *working.* That a person might feel otherwise never occurred to me.

A couple of the people who posted before me, to whom I was replying, had used my tutorial to install the JDK directly from the vendor site. They expressed disappointment that the plugin "didn't work". While I wrote the tutorial primarily for developers who wanted better performance from eclipse, I didn't mind sharing a detail or two. 

There isn't an option for installing software on Ubuntu that I would or wouldn't use 100% of the time, and I don't think I suggested here that everyone give up automatix, or even learn. I've found that those who don't *want* to learn are blessed exceedingly with the talent to avoid it. I don't see the *downside* of following up after a previously made recommendation was poorly received to shed light on the missing pieces though. 

I'll consider what other value your post might have beyond prompting me for clarification on why I would spend any time giving advice to anyone about anything. I doubt there is any, but perhaps I *do* have something to learn.

---

