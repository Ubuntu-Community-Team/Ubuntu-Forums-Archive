---
title: "[SOLVED] I've tried just about everything - can' get Java to work in Firefox"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by SuperDuck on 2007-09-02
Hello all-

I've tried just about everything to install Java, and Firefox still won't recognize it.  I've searched and gone by the advice in a lot of the threads I've found, but I'm not getting anywhere. :(

I've tried following these instructions:
> **capink said:**
> This is how I enabled java. I hope this would help:

1. Install java, the plugin and the fonts

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

2. Create a symlink in the firefox plugins directory

```
sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.00/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins
```

3.Enable Java in firefox

goto > Edit > Preferences > Content > Enable java

And it still doesn't work.  When I run the apt-get it says that I already have Java 6 installed, and when I try and create a symlink it says that it's already there.  I have it enabled in Firefox.

I tried downloading the .bin as suggested on Java's site and attempted to install it, and it didn't work.

When I check on the Java site to verify my installation, it says: 
> Your Java version is 1.4.2. Please click the button below to get the recommended Java for your computer.  

What can I do?

---

### Post by taurus on 2007-09-02
What's the output of this command from a terminal?

```
java --version
```
p.s.  You did remember to restart firefox after you installed java, right?

---

### Post by SuperDuck on 2007-09-02
Yup, I've restarted Firefox every time I've tried something new.

Terminal says I've got 1.4.2, which doesn't make sense because when I run the apt-get for Java 6 it says that it's already installed.

---

### Post by Vadi on 2007-09-02
You know, there's a really easy way to install Java. Too bad it's hidden, I only found it by looking at the features of ubuntu fiesty.

Go here: [http://www.ubuntu.com/getubuntu/releasenotes/704tour](http://www.ubuntu.com/getubuntu/releasenotes/704tour)

And scroll down to "Easy Third Party Installation".

And yep, it really is that easy as just installing that package :D

---

### Post by Delkster on 2007-09-02
Try entering the following command in the terminal:
```
sudo update-java-alternatives --set java-6-sun
```

---

### Post by taurus on 2007-09-02
Try to reconfigure java again with

```
sudo update-alternatives --config java
```
Make sure you make the latest version of java as your default version.  Then, see which version do you use now.

```
java -version
```

---

### Post by Seisen on 2007-09-02
> **SuperDuck said:**
> Yup, I've restarted Firefox every time I've tried something new.

Terminal says I've got 1.4.2, which doesn't make sense because when I run the apt-get for Java 6 it says that it's already installed.

It says that because you need to do this in the terminal.

```
update-java-alternatives -l
``` and select the Java 1.6 version

---

### Post by SuperDuck on 2007-09-02
> **Delkster said:**
> Try entering the following command in the terminal:
```
sudo update-java-alternatives --set java-6-sun
```

Phew, thanks, that one did it.  Is there any documentation for how the update-alternatives command works and how to use it in the future?

Thanks to everyone that replied!

---

### Post by Vadi on 2007-09-02
Edit: Oops, double post.

---

### Post by Delkster on 2007-09-04
If you're already a little familiar with the command line, the manual pages for update-alternatives and, in case of Java, update-java-alternatives would probably be a good source.
```
man update-alternatives
```
```
man update-java-alternatives
```
In case you aren't familiar with using man (or the `less' command), you can scroll the pages with the up/down keys (in Ubuntu the mouse scroll wheel should also work). Page up/down should also work, as well as home/end. The `q' button exits the viewer.

The update-alternatives command processes one command at a time, e.g. you could choose which alternative to use for the `java' command by entering "sudo update-alternatives --config java". However, for choosing the Java package you want to use, update-java-alternatives is better since it updates the alternatives for all Java-related commands at once (java, javac, etc.) In other words, it's a shortcut for handling the alternatives for java-related programs. For configuring other commands you'd use plain update-alternatives instead. All commands which you can have alternative implementations for show up in the /etc/alternatives directory, so you can just view the contents of that directory to find out what commands you can configure.

Basically, with "update-java-alternatives --list" you could see a list of available Java environments. The first column in the list is the name of the environment, the second one is the relative priority that will be used if you use the "--auto" option (automatic selection), and the third one is the path to the Java environment.
```
$ update-java-alternatives --list
java-1.5.0-sun 53 /usr/lib/jvm/java-1.5.0-sun
java-6-sun 63 /usr/lib/jvm/java-6-sun
java-gcj 1041 /usr/lib/jvm/java-gcj
```
As you can see, the free/open source GCJ implementation if Java has a higher priority than the Sun environments. By default the alternatives are chosen automatically based on the priorities, so java-gcj was used by default even though you also had the Sun JVM installed.

After finding out the name of the JVM you want to use, you can use the "--set" action to select it:
```
sudo update-java-alternatives --set java-6-sun
```
Note that while viewing the list doesn't require administrative privileges (sudo), changing the configuration does. The same is true for the update-alternatives command.

With update-alternatives you can also use the --display option to view the current status of the link. It shows not only which alternatives are available but also which one is currently selected and whether the configuration is automatic or manually configured.
```
$ update-alternatives --display traceroute
traceroute - status is auto.
 link currently points to /usr/bin/traceroute.lbl
/usr/bin/traceroute.lbl - priority 100
 slave traceroute.8.gz: /usr/share/man/man8/traceroute.lbl.8.gz
 slave traceroute.sbin: /usr/bin/traceroute.lbl
Current `best' version is /usr/bin/traceroute.lbl.
```

Hopefully this gets you started.

---

### Post by SuperDuck on 2007-09-04
Thanks for your detailed response, Delkster.  I keep forgetting about the built-in "man" commands - they're very useful.  I'm trying to wrap my head around the whys and wherefores for the commands that I'm putting in, and your post helped a lot. :)

The listing of the priorities after the --list command seems counterintuitive.  I would have that the that entries with the smaller number and physically higher on the list would be the higher priority.  I guess it's just something I'll have to get used to!

---

### Post by -SpaZ on 2007-09-04
> **Vadi said:**
> You know, there's a really easy way to install Java. Too bad it's hidden, I only found it by looking at the features of ubuntu fiesty.

Go here: [http://www.ubuntu.com/getubuntu/releasenotes/704tour](http://www.ubuntu.com/getubuntu/releasenotes/704tour)

And scroll down to "Easy Third Party Installation".

And yep, it really is that easy as just installing that package :D

Wow, thanks.  I wonder why people don't recommend this all the time.

---

### Post by Vadi on 2007-09-05
I think it's because it's somewhat like a hidden feature. I've never seen it mentioned other than that place, and only stumbled upon it by accident.

So spread the word about it :D

---

### Post by SuperDuck on 2007-09-05
> **-SpaZ said:**
> Wow, thanks.  I wonder why people don't recommend this all the time.

I've used that to great success, though I went through Synaptic instead of the Add/Remove for Java specifically.  The problem I had with that is that the version of Java that is installed is out of date, unless I'm mistaken.  It gave me the Runtime Environment 1.4 instead of 1.6 - I believe that was part of the problem.

---

### Post by Vadi on 2007-09-05
Newp, I got 1.6.

---

### Post by alienexplorers on 2007-09-05
Go to your firefox plugin directory.  Delete the symbolic link to java.  Re-do the sym link to place the new java plugin in the directory.  reboot and see what happens.

---

### Post by stchman on 2007-09-05
> **SuperDuck said:**
> Hello all-

I've tried just about everything to install Java, and Firefox still won't recognize it.  I've searched and gone by the advice in a lot of the threads I've found, but I'm not getting anywhere. :(

I've tried following these instructions:


And it still doesn't work.  When I run the apt-get it says that I already have Java 6 installed, and when I try and create a symlink it says that it's already there.  I have it enabled in Firefox.

I tried downloading the .bin as suggested on Java's site and attempted to install it, and it didn't work.

When I check on the Java site to verify my installation, it says: 


What can I do?

Uninstall the Java 6 and do this in a terminal.  It works.

```
sudo apt-get install sun-java5-bin sun-java5-jre sun-java5-jdk sun-java5-fonts sun-java5-plugin
```

When this is done you will be fine.

---

