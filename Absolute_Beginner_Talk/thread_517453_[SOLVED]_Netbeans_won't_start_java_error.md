---
title: "[SOLVED] Netbeans won't start java error"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by purdticker on 2007-08-04
When I start netbeans, it just shows up as a gray screen.

This is the error I get in terminal:

> 
java.net.UnknownHostException: fermmons: fermmons
        at java.net.InetAddress.getLocalHost(InetAddress.java:1315)
        at org.netbeans.CLIHandler.initialize(CLIHandler.java:487)
        at org.netbeans.CLIHandler.initialize(CLIHandler.java:291)
        at org.netbeans.Main.execute(Main.java:161)
        at org.netbeans.Main.main(Main.java:48)


fermmons is my computer name.

> 
$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)


---

### Post by purdticker on 2007-08-04
I'm getting this same exception when trying to start apache geronimo web server.  I think this is a java issue w/ Ubuntu.

---

### Post by purdticker on 2007-08-04
Must be a DNS issue.  Can't resolve fermmons... anyone know enough basic networking in ubuntu to help me out?

---

### Post by purdticker on 2007-08-04
Tried to ping myself...

>  
$ ping fermmons
ping: unknown host fermmons


---

### Post by spur on 2007-08-04
I read somewhere its a Java bug in 1. 6.0 and updating to 1.6.1 fixes it. I havent tried that yet myself though. I am waiting for the update to appear in the repositories. I have an earlier version (1.4) installed and run that.

---

### Post by purdticker on 2007-08-13
This was actually because server "fermmons" (my computer name) wasn't listed in /etc/hosts file

> sudo gedit /etc/hosts

Insert "127.0.0.1 fermmons"

---

