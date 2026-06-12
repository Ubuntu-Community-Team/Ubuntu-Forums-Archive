---
title: "[SOLVED] Limewire blank screen with Compiz-Fusion"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by meindian523 on 2008-01-08
I'm facing a problem with Limewire showing me a blank screen when I login with Compiz-Fusion.There's a thread in the Tutorials and Tips section dealing with the same issue with Beryl,but that solution doesn't work with Compiz-Fusion.I have tried the Ubuntu community documentation too,but no luck.I had to reinstall Limewire since there was no filename~ file(for /usr/bin/limewire) to restore to,so basically I have a kind-of brand new installation of Limewire we can all tinker with.:)

Does somebody have a better solution which actually works?

---

### Post by meindian523 on 2008-01-08
For the record:

The tutorials and tips thread:

[http://ubuntuforums.org/showthread.php?t=430403](http://ubuntuforums.org/showthread.php?t=430403)

The Ubuntu Community Documentation:

[https://help.ubuntu.com/community/LimeWire](https://help.ubuntu.com/community/LimeWire)

Both didn't work for me. :(

---

### Post by PeterJS on 2008-01-08
Limewire is java isn't it? You don't happen to be running Beryl.

---

### Post by meindian523 on 2008-01-08
Limewire IS Java but I happen to be running not Beryl but Compiz-Fusion.

---

### Post by PeterJS on 2008-01-08
I know beryl had a bug with not playing nice with java. But I thought that was fixed in Compiz. So much for that though.

---

### Post by meindian523 on 2008-01-08
But is there a fix for this?Some solution?

---

### Post by PeterJS on 2008-01-08
I thought it was fixed. Obviously I was wrong.

---

### Post by meindian523 on 2008-01-09
I found that from your previous post,with my previous post,I was trying to ask whether any of the people out there knew a solution,

---

### Post by meindian523 on 2008-01-11
um,bump.

---

### Post by swoll1980 on 2008-01-11
in compiz-manager go down to utilities make sure work arounds is enabled if it is click on it and see if the java work around is enabled

---

### Post by meindian523 on 2008-01-11
Both are enabled.Now what?

---

### Post by swoll1980 on 2008-01-11
Thats a strange problem I thought for sure it was the workaround the only other solution I know of is the bash script but you have tried that as well. go to javas web site see if the "can you see this java image" test works Do you have java installed

---

### Post by meindian523 on 2008-01-11
sun-java5-jre and sun-java-bin,both from the repos.

---

### Post by swoll1980 on 2008-01-11
go to java.com and click on "do I have java" see if it's working

---

### Post by meindian523 on 2008-01-11
The Verify Java Installation applet doesn't run because I don't have the Java plugin for Firefox,I tried the Install Missing plugins but it came up with Plugin not Available.

---

### Post by swoll1980 on 2008-01-11
if you run limewire in the terminal does it give you a error message

---

### Post by meindian523 on 2008-01-11
Just this:

```
easwarh@l1nuxr0cks:~$ limewire 
Starting LimeWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_11]
Configuring environment...
Loading LimeWire:
/usr/share/themes/Human/gtk-2.0/gtkrc:71: Engine "ubuntulooks" is unsupported, ignoring
/usr/share/themes/Human/gtk-2.0/gtkrc:241: Priority specification is unsupported, ignoring
easwarh@l1nuxr0cks:~$ 

```

Does that make some sense to you?I don't think a theme engine should do what's happening.I got back the prompt after shutting down Limewire.

---

### Post by swoll1980 on 2008-01-11
have you ever tried frostwire? I would try it just to see if it works limewire is open source frostwire is all of limewires source with a chatroom feature added to it if you like it and it works you wont have to deal with this crap anymore [www.frostwire.com](www.frostwire.com)

---

### Post by meindian523 on 2008-01-11
Um,can frostwire connect to Limewire's network?

---

### Post by swoll1980 on 2008-01-11
yes it's like 99% limewire same network same everything

---

### Post by meindian523 on 2008-01-11
I will try that but I would still like Limewire running.

---

### Post by swoll1980 on 2008-01-11
yeah that would drive me nuts but if it works you will no it's not a problem with your workarounds because frostwire uses java as well

---

### Post by meindian523 on 2008-01-11
lol

---

### Post by swoll1980 on 2008-01-11
or try this [http://limewirepro.at.tt/](http://limewirepro.at.tt/) it's limewire pro but compiled independently so it's free

---

### Post by meindian523 on 2008-01-11
Now you tell me.

---

### Post by swoll1980 on 2008-01-11
sorry just thought of it

---

### Post by meindian523 on 2008-01-11
Frostwire works.

---

### Post by swoll1980 on 2008-01-11
try the limewire pro see if that works for you

---

### Post by meindian523 on 2008-01-11
But it's S..L....O.......W.
Will try LimewirePro later.My bandwidth's limited you know. :) .Thanks for all the help.

---

### Post by swoll1980 on 2008-01-11
cool just post back whenever let me know how it turns out

---

### Post by meindian523 on 2008-01-11
I will be sure to do that.

---

### Post by meindian523 on 2008-01-13
I tried Limewire Pro and no go,wonder how the same code in Frostwire works so well.

---

### Post by DrFugly on 2008-05-20
I had the same issue and realized that the issue only occured when using Java 5 and is fixed with Java 6. So I am now able to use limewire w/ compiz running with no issue.

Inorder to make sure that you are using java 6 and not 5 you can use the following commands in the terminal:

> cd /usr/lib/LimeWire
/usr/lib/jvm/java-6-sun/bin/java -jar LimeWire.jar


basically go to the limewire directory then point to java 6 and run that java
this approach requires that your "PATH" variable has a '.' at the start of it. If you notice that its STILL trying to use java 5 then try the following:

> export PATH=".:${PATH}"

and then try the commands I gave before. 
This did it for me.

---

### Post by meindian523 on 2008-05-20
I'll try that once I upgrade to Hardy and get back.Thanks for the effort.:)

---

