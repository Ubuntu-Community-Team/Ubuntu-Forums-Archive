---
title: "Java in firefox not working."
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by achelis on 2008-03-11
Hi

I'm new to Ubuntu/Linux, and I haven't been able to get Java to work in Firefox. It's working fine elsewhere. Firefox asks for me to install a plugin when I get to a web-page using java, but the only plugin I can install is : The GCJ Web Browser Plugin (Using IcedTea). 
I tried installing that but that didn't work - no errors just blank pages.

Is there other plugins that work or is IcedTea the only choice (right now I'm running Firefox through wine which works better - that is it works :) )

Hope someone can help me.

---

### Post by dmsynck on 2008-03-11
I am trying to understand why you would need to run Firefox through Wine if you are running Firefox natively on Ubuntu.

---

### Post by Mark Bowers on 2008-03-11
I'm doing this from memory as I'm at a Windoze station right now, but... there are several ways to install Java, and I'd recommend that you install the Java Runtime Environment, not just a plug-in.

First of all you can do this from the command prompt, but I don't remember the exact commands. I think its:

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

The second and I think easier way is to install "ubuntu restricted extras" from Add/Remove programs from your application bar. JRE is included in the "ubuntu restricted extras" installation.

Be sure to close down Firefox before trying either of the above. After you've installed the above restart Firefox and you should be in business. A good way to tell if you have everything you need to is to play a video at youtube.com

M. Bowers

---

### Post by Mark Bowers on 2008-03-11
I forgot to mention that the instructions assume you are using 32-bit Ubuntu. If you are running 64-bit, there are problems with the current version of Java. I've heard of work arounds, but the pending Java 7, as I understand it, will include 64-bit support.

M. Bowers

---

### Post by achelis on 2008-03-11
> **dmsynck said:**
> I am trying to understand why you would need to run Firefox through Wine if you are running Firefox natively on Ubuntu.

Because I can't get java working when running natively.

@Mark: Thx but it didn't do it for me. 

```

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
sun-java6-jre set to manual installed.
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

```

Youtube does work however - but at my banks website I still get the "missing plugin".

When I click it I go to a screen saying: Available Plugin Downloads, The following plugins are available: Java Runtime Environment.
Press next to install.

So i do - and get to the next screen: No plugins were installed. And a button labeled: "Manual Install". 

Clicking that takes me to the following download page ([http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com](http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com))

Where I kinda get to the conclusion that applets must be what's not working as it says to use the 32-bit version (I'm on a 64-bit).

I'll try to install the 32-bit version now... and will let you know in a minute how i fared.
Thanks for helping :)

---

### Post by Mark Bowers on 2008-03-11
Well, as mentioned in my last post - JRE in 64-bit is a whole different issue. Checkout this post, as it has the best advice I've seen thus far.

[http://wernerroth.de/index.php/2008/01/22/firefox-64-bit-java-ica-und-flash-plugins-using-kubuntu-710/](http://wernerroth.de/index.php/2008/01/22/firefox-64-bit-java-ica-und-flash-plugins-using-kubuntu-710/)

Mark Bowers

---

### Post by achelis on 2008-03-11
Well.. got as far as installing the j2se-1,4 webstart, 

Now I went according to a guide at java.com ([http://java.com/en/download/help/5000010500.xml#100](http://java.com/en/download/help/5000010500.xml#100))

Standing in the directory of my firefox-plugins folder:
```

ln -s /usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so
```

Which semi-worked. Now java shows up as enabled when i go to the about:plugins page in Firefox - problem is that when I go to the verify installation page ([http://java.com/en/download/installed.jsp](http://java.com/en/download/installed.jsp)) it doesn't work, and when I go to the page of my bank the applet starts and crashes the browser :/

Ideas are more than welcome - but for now I think I'll call it a night.

EDIT: Thanks Mark, will check that out before calling it a night then :)

---

### Post by achelis on 2008-03-11
Well - according to that there isn't much of a choice but to wait for Java 7.

Thanks a lot for the help - think this is as good as it gets for now.

---

### Post by Mark Bowers on 2008-03-11
You can switch back to 32-bit..... that's what I finally did. :)

Take care,

Mark B.

---

