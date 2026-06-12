---
title: "help installing azureus/bittyrant"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by mode87 on 2007-02-22
i am having the following problem 

kyle@kyle-desktop:/opt/azureus$ ./azureus
Starting Azureus...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.4.2]
Configuring environment...
Loading Azureus:
java -Xms16m -Xmx128m -cp "/opt/azureus/Azureus2.jar:/opt/azureus/swt.jar" -Djava.library.path="/opt/azureus" -Dazureus.install.path="/opt/azureus" org.gudy.azureus2.ui.swt.Main ''
java.lang.NoClassDefFoundError: org.gudy.azureus2.core3.peer.TyrantStats
   at java.lang.Class.initializeClass(libgcj.so.70)
   at org.gudy.azureus2.core3.util.Constants.<clinit>(Constants.java:68)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at org.gudy.azureus2.core3.config.COConfigurationManager.preInitialise(COConfigurationManager.java:88)
   at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:50)
   at org.gudy.azureus2.ui.swt.Main.main(Main.java:162)
Caused by: java.lang.VerifyError: verification failed at PC 16 in org.gudy.azureus2.core3.peer.TyrantStats:fileLog((J)V): incompatible type on stack
   at java.lang.Class.initializeClass(libgcj.so.70)
   ...5 more
java.lang.NoClassDefFoundError: org.gudy.azureus2.core3.util.Constants
   at java.lang.Class.initializeClass(libgcj.so.70)
   at org.gudy.azureus2.core3.util.SystemProperties.getUserPath(SystemProperties.java:166)
   at org.gudy.azureus2.core3.util.FileUtil.readResilientConfigFile(FileUtil.java:440)
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.load(ConfigurationManager.java:145)
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.load(ConfigurationManager.java:193)
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.getInstance(ConfigurationManager.java:69)
   at org.gudy.azureus2.core3.logging.impl.LoggerImpl.init(LoggerImpl.java:90)
   at org.gudy.azureus2.core3.logging.Logger.<clinit>(Logger.java:48)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at org.gudy.azureus2.ui.swt.StartServer.<init>(StartServer.java:70)
   at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:56)
   at org.gudy.azureus2.ui.swt.Main.main(Main.java:162)
DEBUG::Thu Feb 22 12:12:11 EST 2007::java.lang.Class::initializeClass::-1:
  Error initializing Logger
    StartServer::<init>::70,Main::<init>::56,Main::main::162
java.lang.NoClassDefFoundError: org.gudy.azureus2.core3.util.Constants
   at java.lang.Class.initializeClass(libgcj.so.70)
   at org.gudy.azureus2.core3.util.SystemProperties.getUserPath(SystemProperties.java:166)
   at org.gudy.azureus2.core3.util.FileUtil.readResilientConfigFile(FileUtil.java:440)
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.load(ConfigurationManager.java:145)
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.load(ConfigurationManager.java:193)
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.getInstance(ConfigurationManager.java:69)
   at org.gudy.azureus2.core3.logging.impl.LoggerImpl.init(LoggerImpl.java:90)
   at org.gudy.azureus2.core3.logging.Logger.<clinit>(Logger.java:48)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at org.gudy.azureus2.ui.swt.StartServer.<init>(StartServer.java:70)
   at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:56)
   at org.gudy.azureus2.ui.swt.Main.main(Main.java:162)
Exception in thread "main" java.lang.NoClassDefFoundError: org.gudy.azureus2.core3.util.Constants
   at java.lang.Class.initializeClass(libgcj.so.70)
   at org.gudy.azureus2.core3.util.SystemProperties.getUserPath(SystemProperties.java:166)
   at org.gudy.azureus2.core3.util.FileUtil.readResilientConfigFile(FileUtil.java:440)
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.load(ConfigurationManager.java:145)
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.load(ConfigurationManager.java:193)
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.getInstance(ConfigurationManager.java:79)
   at org.gudy.azureus2.core3.config.COConfigurationManager.initialise(COConfigurationManager.java:105)
   at com.aelitis.azureus.core.impl.AzureusCoreImpl.<init>(AzureusCoreImpl.java:143)
   at com.aelitis.azureus.core.impl.AzureusCoreImpl.create(AzureusCoreImpl.java:92)
   at com.aelitis.azureus.core.AzureusCoreFactory.create(AzureusCoreFactory.java:46)
   at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:143)
   at org.gudy.azureus2.ui.swt.Main.main(Main.java:162)
Azureus TERMINATED.

if i cant run the ./azureus then how can i get it to work? please help me. thanks

---

### Post by nickoli_02 on 2007-02-22
How did you install Azureus? Did you get it from the repos with apt or synaptics?

---

### Post by Perfect Storm on 2007-02-22
You need sun java 1.5 or 1.6

---

### Post by mahy on 2007-02-22
you have to install the proper Java. Run Synaptic and look for packages named

sun-java5-*

Then open the terminal and run 

sudo update-alternatives --config java

and select Sun JRE instead of GCJ. That should fix it.

---

### Post by mode87 on 2007-02-22
thank you so much, that fixed the problem. i had the right one installed but it was using the gcj instead of jre. thanks again.

---

