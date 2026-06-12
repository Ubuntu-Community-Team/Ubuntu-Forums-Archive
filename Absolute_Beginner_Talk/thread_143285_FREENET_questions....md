---
title: "FREENET questions..."
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by Cousindaddy on 2006-03-12
Having some problems installing FREENET.  I dloaded *freenet-stable-latest.tgz* from the FREENET site and followed the installation instructions posted there.  However, when I ran *sh start-freenet.sh* I was never presented with any config questions; instead, I received the following:  > user@machine:~/Desktop/freenet$ sh start-freenet.sh Detected freenet-ext.jar Detected freenet.jar Sun java detected. Sun Java 1.4.2 detected. Starting Freenet now: Command line: java -Xmx128m -XX:MaxDirectMemorySize=128m freenet.node.Main Done user@machine:~/Desktop/freenet$ os.arch = i386 Loading native... Attempting to load freenet/support/CPUInformation/libjcpuid-x86-linux.so Written to /tmp/jcpuid42861lib.tmp: 55692 INFO: Native CPUID library 'freenet/support/CPUInformation/libjcpuid-x86-linux.so' loaded from resource INFO: Optimized native BigInteger library 'net/i2p/util/libjbigi-linux-pentium4.so' loaded from resource Caught freenet.ListenException: tcp//127.0.0.1:8481: Address already in use running or seeding node freenet.ListenException: tcp//127.0.0.1:8481: Address already in use         at freenet.transport.tcpNIOListener.startListener(tcpNIOListener.java:68)         at freenet.transport.tcpNIOListener.(tcpNIOListener.java:50)         at freenet.transport.tcpListeningAddress.getNIOListener(tcpListeningAddress.java:37)         at freenet.interfaces.BaseLocalNIOInterface.getListener(BaseLocalNIOInterface.java:46)         at freenet.interfaces.BaseLocalNIOInterface.(BaseLocalNIOInterface.java:74)         at freenet.interfaces.LocalNIOInterface.(LocalNIOInterface.java:34)         at freenet.node.Main.startNode(Main.java:1723)         at freenet.node.Main.spawnNode(Main.java:1060)         at freenet.node.Main.main(Main.java:908) ERROR: tcp//127.0.0.1:8481: Address already in use freenet.ListenException: tcp//127.0.0.1:8481: Address already in use at freenet.transport.tcpNIOListener.startListener(tcpNIOListener.java:68)         at freenet.transport.tcpNIOListener.(tcpNIOListener.java:50)         at freenet.transport.tcpListeningAddress.getNIOListener(tcpListeningAddress.java:37)         at freenet.interfaces.BaseLocalNIOInterface.getListener(BaseLocalNIOInterface.java:46)         at freenet.interfaces.BaseLocalNIOInterface.(BaseLocalNIOInterface.java:74)         at freenet.interfaces.LocalNIOInterface.(LocalNIOInterface.java:34)         at freenet.node.Main.startNode(Main.java:1723)         at freenet.node.Main.spawnNode(Main.java:1060)         at freenet.node.Main.main(Main.java:908) Could not bind to listening port(s) - maybe another node is running? Or, you might not have privileges to bind to a port < 1024.  At this point I hit ENTER and am returned to the terminal.   Has anyone installed and configured this successfully? and if so, how?  Thanks in advance.

---

### Post by Swab on 2006-03-12
Are you running this as root?  Obvious I know... but just thought I'd check!

---

### Post by Cousindaddy on 2006-03-12
Thanks for the reply.  > Are you running this as root?  It doesn't seem to make any difference.  I still get the same output.

---

