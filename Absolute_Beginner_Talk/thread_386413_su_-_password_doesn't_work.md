---
title: "su - password doesn't work"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by carusoswi on 2007-03-17
Ok.  I am trying to start a remote session to my office computer from my machine with its newly installed ubuntu 6.10.  In the course of logging onto the remote machine, Thunderbird notifies me that I need to download a java plugin.  I do so.  It doesn't install automatically, so I set about following the instructions to install manually.

The plugin instructions tell me to type su and hit enter.  I do so.  I am prompted for my password.  I enter it.

The machine cooks for a few seconds, then, returns "Sorry".

Now, I only have one password, and I use it everytime I boot up.  I have used it during other install routines and it worked fine.  I've checked and double checked to make certain I am entering in the proper case - caps lock off, num lock on, etc.

So, what am I doing wrong here?

Thanks.

Caruso

---

### Post by 23meg on 2007-03-17
The root account is disabled by default. Use *sudo* as a prefix to the program you want to run as root instead.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by carusoswi on 2007-03-17
Thanks for the reply.  I guess I remain confused as to why linux specific instructions would direct me to do something that doesn't generally will not work.  I don't get it.  I will try your suggestion and see how I make out.

Thanks again.

Caruso

---

### Post by 23meg on 2007-03-17
I can't possibly know why things usually don't work for you, but the reason in this specific case is that the "su" command means "become root", and you can't log in as root in Ubuntu by default. This is a per-distro configuration choice; with many (actually, most) other distributions, "su" would work. It will also work in Ubuntu if you enable the root account (not recommended).

---

### Post by aysiu on 2007-03-17
> **carusoswi said:**
> Thanks for the reply.  I guess I remain confused as to why linux specific instructions would direct me to do something that doesn't generally will not work.  I don't get it.  I will try your suggestion and see how I make out.

Thanks again.

Caruso
Actually, it does *generally* work (meaning "work for almost every single Linux distribution except Ubuntu").

Ubuntu is not like other Linux distributions, though.

It does not default to enabling a root account (the command ```
su
``` switches you to logging as the root user). Read the link posted above for more details:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You may also want to read this to install Java:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by carusoswi on 2007-03-17
Thanks for the replies.  I didn't mean to suggest that things don't usually work for me.  I missed the note in the Java instructions about the versions of linux to which they apply.  Ubuntu is not one of them.

I still cannot get it to work.  The file that I have downloaded is: jre-1_5_0_11-linux-i586-rpm.bin

I am supposed to chmod it, then run 
jre-1_5_0_11-linux-i586-rpm.bin

That is supposed to extract the file.

I understand that my difficulties are the result of my lack of familiarity with this OS.  So, if someone could give me a little more detail about what I should be doing with these files, I would appreciate it.

Caruso

---

### Post by scxtt on 2007-03-17
i doubt that file is going to work, running the .bin will most likely create an rpm - which isn't usable by Ubuntu (or debian-based distros) w/o extra work ...

i recommend installing:
```
[font=courier]sun-java5-bin                   - Sun Java(TM) Runtime Environment (JRE) 5.0
sun-java5-jre                   - Sun Java(TM) Runtime Environment (JRE) 5.0
sun-java5-plugin                - The Java(TM) Plug-in, Java SE 5.0[/font]
```

{**sudo aptitude install sun-java5-bin sun-java5-jre sun-java5-plugin**} to get java working ...

---

### Post by 23meg on 2007-03-17
You downloaded the wrong file. RPM isn't Ubuntu's native package format; though you can convert and install RPM packages, you should only do it if there's no other way to install the software, as a last resort. 

Delete that file, and follow the instructions in the last link aysiu posted.

---

### Post by carusoswi on 2007-03-17
Thanks.  I'll give your suggestions a go.
Caruso

---

### Post by ahmatti on 2007-03-17
Caruso if you are new to Ubuntu and want an easy way to install a lot usefull apps then I suggest you checkout Automatix [http://www.getautomatix.com/](http://www.getautomatix.com/).

---

### Post by carusoswi on 2007-03-17
Learning this OS make me feel really dense, sometimes.  I tried searching for the java version you mention.  Couldn't exactly find it.  The site I was trying to open offered this one - jre-1_5_0_11-linux-i586 - among the choices.  So I tried downloading it and applying the command you suggested to install it.  A bunch of code scrolled by, but the last lines tell me that nothing really happened.

Sorry, but, I could use some more help.

Caruso

---

### Post by Delkster on 2007-03-17
> **carusoswi said:**
> I tried searching for the java version you mention.  Couldn't exactly find it.

It's available in the Ubuntu software repositories, or "channels". However, since Sun Java is not yet free/open source, in Ubuntu it's placed in the so-called multiverse channel which isn't enabled by default. That's probably why you didn't find the packages by name.

If you only need the Java Runtime Environment and browser plugin for running Java programs, do the following (these instructions are approximate since I'm currently using my desktop in a language different than English, but you should be able to get the idea):

1. Open **Applications > Add/Remove**.
2. From the drop-down menu in the top right corner of the window, select to **display all available applications**.
3. Use the search to look for "java" and select the **Sun Java 5.0 Plugin** and **Sun Java 5.0 Runtime** for installation. You'll probably be asked if you want the multiverse component to be enabled. Accept it.
4. Select Ok or Apply. After installing the Java runtime and the plugin restart your browser and other applications that need it. It should work now.

---

