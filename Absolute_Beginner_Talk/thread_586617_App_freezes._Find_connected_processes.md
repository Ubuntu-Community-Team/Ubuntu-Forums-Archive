---
title: "App freezes. Find connected processes?"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Ondkloss on 2007-10-22
I'm having some trubble with Azureus so it freezes pretty much on my command. Anyways, that's not the issue. When it freezes I'm unable to start it again becouse it figures Azureus is already running.

Am I somehow able to see what processes was started when running "azureus" command, and then nuke them to be able to start a new Azureus without having to boot every time? Ty!

---

### Post by ed-koala on 2007-10-22
You can find out which processes are running thru the System - Administration - System Monitor

Check before you run Azureus, and after.  That will tell you which process(es) related to Azureus are running.

As for it freezing, when exactly does it happen?  Or does it seem to shut down just after it starts?

---

### Post by Hospadar on 2007-10-22
Azureus will run two processes - "azureus" and a java process.  so if azureus is freezing, kill azureus (often the java process will die when that is killed) and then also look for a big java process.

---

### Post by Ondkloss on 2007-10-22
thanks! worked out great. sorted by ID and quickly saw the newly created processes. turns out Azureus was using 50% (100% of one of my cores) even after I killed it using xkill. now I just gotta repair Azureus.

-- it's freezing when I open a torrent file. It starts and runs forever when I do nothing. I've installed it custom so I can use version 2.5.0.4 instead of new version. also custom installed JDK6, but that doesn't seem to bring me any problems as I'm running Eclipse perf. Have no idea why Azureus freezes at that exact point though...

btw, is there any terminal command to open the System Monitor gui? (would like to make shortcut similar to windows ctrl+alt+del)

when I run Azureus from terminal I get this heap of text:

```
java -Xms16m -Xmx128m -cp "/usr/lib/azureus/Azureus2.jar:/usr/lib/azureus/swt.jar" -Djava.library.path="/usr/lib/azureus" -Dazureus.install.path="/usr/lib/azureus" org.gudy.azureus2.ui.swt.Main ''
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
DEBUG::Mon Oct 22 15:35:13 GMT 2007::com.aelitis.azureus.core.networkmanager.impl.tcp.VirtualBlockingServerChannelSelector::start::92:
    IncomingSocketChannelManager::start::378,IncomingSocketChannelManager::<init>::140,TCPNetworkManager::<init>::127,TCPNetworkManager::<clinit>::43,NetworkManager::getMinMssSize::150,ByteBucket::ensureByteBucketMinBurstRate::150,ByteBucket::<init>::63,ByteBucket::<init>::49,TransferProcessor::<init>::62,NetworkManager::<init>::124,NetworkManager::<clinit>::50,AzureusCoreImpl::<init>::182,AzureusCoreImpl::create::93,AzureusCoreFactory::create::46,Main::<init>::76,Main::main::180
java.net.BindException: Address already in use
        at sun.nio.ch.Net.bind(Native Method)
        at sun.nio.ch.ServerSocketChannelImpl.bind(ServerSocketChannelImpl.java:119)
        at sun.nio.ch.ServerSocketAdaptor.bind(ServerSocketAdaptor.java:59)
        at com.aelitis.azureus.core.networkmanager.impl.tcp.VirtualBlockingServerChannelSelector.start(VirtualBlockingServerChannelSelector.java:79)
        at com.aelitis.azureus.core.networkmanager.impl.tcp.IncomingSocketChannelManager.start(IncomingSocketChannelManager.java:378)
        at com.aelitis.azureus.core.networkmanager.impl.tcp.IncomingSocketChannelManager.<init>(IncomingSocketChannelManager.java:140)
        at com.aelitis.azureus.core.networkmanager.impl.tcp.TCPNetworkManager.<init>(TCPNetworkManager.java:127)
        at com.aelitis.azureus.core.networkmanager.impl.tcp.TCPNetworkManager.<clinit>(TCPNetworkManager.java:43)
        at com.aelitis.azureus.core.networkmanager.NetworkManager.getMinMssSize(NetworkManager.java:150)
        at com.aelitis.azureus.core.networkmanager.impl.ByteBucket.ensureByteBucketMinBurstRate(ByteBucket.java:150)
        at com.aelitis.azureus.core.networkmanager.impl.ByteBucket.<init>(ByteBucket.java:63)
        at com.aelitis.azureus.core.networkmanager.impl.ByteBucket.<init>(ByteBucket.java:49)
        at com.aelitis.azureus.core.networkmanager.impl.TransferProcessor.<init>(TransferProcessor.java:62)
        at com.aelitis.azureus.core.networkmanager.NetworkManager.<init>(NetworkManager.java:124)
        at com.aelitis.azureus.core.networkmanager.NetworkManager.<clinit>(NetworkManager.java:50)
        at com.aelitis.azureus.core.impl.AzureusCoreImpl.<init>(AzureusCoreImpl.java:182)
        at com.aelitis.azureus.core.impl.AzureusCoreImpl.create(AzureusCoreImpl.java:93)
        at com.aelitis.azureus.core.AzureusCoreFactory.create(AzureusCoreFactory.java:46)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:76)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:180)
[alert] Alert:3:ERROR, unable to bind TCP incoming server socket to 57500
DEBUG::Mon Oct 22 15:35:13 GMT 2007::com.aelitis.azureus.core.networkmanager.impl.tcp.VirtualBlockingServerChannelSelector::start::93:
  java.net.BindException: Address already in use
        at sun.nio.ch.Net.bind(Native Method)
        at sun.nio.ch.ServerSocketChannelImpl.bind(ServerSocketChannelImpl.java:119)
        at sun.nio.ch.ServerSocketAdaptor.bind(ServerSocketAdaptor.java:59)
        at com.aelitis.azureus.core.networkmanager.impl.tcp.VirtualBlockingServerChannelSelector.start(VirtualBlockingServerChannelSelector.java:79)
        at com.aelitis.azureus.core.networkmanager.impl.tcp.IncomingSocketChannelManager.start(IncomingSocketChannelManager.java:378)
        at com.aelitis.azureus.core.networkmanager.impl.tcp.IncomingSocketChannelManager.<init>(IncomingSocketChannelManager.java:140)
        at com.aelitis.azureus.core.networkmanager.impl.tcp.TCPNetworkManager.<init>(TCPNetworkManager.java:127)
        at com.aelitis.azureus.core.networkmanager.impl.tcp.TCPNetworkManager.<clinit>(TCPNetworkManager.java:43)
        at com.aelitis.azureus.core.networkmanager.NetworkManager.getMinMssSize(NetworkManager.java:150)
        at com.aelitis.azureus.core.networkmanager.impl.ByteBucket.ensureByteBucketMinBurstRate(ByteBucket.java:150)
        at com.aelitis.azureus.core.networkmanager.impl.ByteBucket.<init>(ByteBucket.java:63)
        at com.aelitis.azureus.core.networkmanager.impl.ByteBucket.<init>(ByteBucket.java:49)
        at com.aelitis.azureus.core.networkmanager.impl.TransferProcessor.<init>(TransferProcessor.java:62)
        at com.aelitis.azureus.core.networkmanager.NetworkManager.<init>(NetworkManager.java:124)
        at com.aelitis.azureus.core.networkmanager.NetworkManager.<clinit>(NetworkManager.java:50)
        at com.aelitis.azureus.core.impl.AzureusCoreImpl.<init>(AzureusCoreImpl.java:182)
        at com.aelitis.azureus.core.impl.AzureusCoreImpl.create(AzureusCoreImpl.java:93)
        at com.aelitis.azureus.core.AzureusCoreFactory.create(AzureusCoreFactory.java:46)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:76)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:180)

[alert] Alert:3:Failed to establish listen on port UDP:57500.
Check that other applications aren't already using this port.
Also check for another copy of Azureus running.
[net] PRUDPPacketReceiver: DatagramSocket bind failed on port 57500
DEBUG::Mon Oct 22 15:35:13 GMT 2007::com.aelitis.net.udp.uc.impl.PRUDPPacketHandlerImpl::receiveLoop::435:
  java.net.BindException: Address already in use
        at java.net.PlainDatagramSocketImpl.bind0(Native Method)
        at java.net.PlainDatagramSocketImpl.bind(PlainDatagramSocketImpl.java:82)
        at java.net.DatagramSocket.bind(DatagramSocket.java:368)
        at java.net.DatagramSocket.<init>(DatagramSocket.java:210)
        at java.net.DatagramSocket.<init>(DatagramSocket.java:261)
        at java.net.DatagramSocket.<init>(DatagramSocket.java:234)
        at com.aelitis.net.udp.uc.impl.PRUDPPacketHandlerImpl.receiveLoop(PRUDPPacketHandlerImpl.java:317)
        at com.aelitis.net.udp.uc.impl.PRUDPPacketHandlerImpl$1.runSupport(PRUDPPacketHandlerImpl.java:128)
        at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:69)


(SWT:6670): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width 250 and height -1
```

---

### Post by Beggar on 2007-10-22
The better way to kill the process is run xkill from the terminal/run application dialog, then just click on the azureus window.

Are you sure there is only 1 azureus running? To find out whats using those ports, run 

```
netstat -v
```

---

### Post by Ondkloss on 2007-10-22
actually I dunno why that port problem occured. got it down to this now (including force quit at end):

```
Starting Azureus...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_03]
Configuring environment...
Loading Azureus:
java -Xms16m -Xmx128m -cp "/usr/lib/azureus/Azureus2.jar:/usr/lib/azureus/swt.jar" -Djava.library.path="/usr/lib/azureus" -Dazureus.install.path="/usr/lib/azureus" org.gudy.azureus2.ui.swt.Main ''
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
/usr/lib/azureus/azureus: line 112:  9125 Killed                  ${JAVA_PROGRAM_DIR}java -Xms16m -Xmx128m -cp "${CLASSPATH}" -Djava.library.path="${PROGRAM_DIR}" -Dazureus.install.path="${PROGRAM_DIR}" org.gudy.azureus2.ui.swt.Main "$@"
Azureus TERMINATED.
```

still it totally freezes up when adding a torrent. I think my release should be stable as well. got it of SourceForge. the add window seems to 'double up' or nudge or something, cause some gfx dubble up.

[COLOR="RoyalBlue"][freeze screenshot]("http://folk.ntnu.no/halvors/givekk/donasjoner/azureusFreeze.png")[/COLOR]

---

### Post by Beggar on 2007-10-22
Do you have the same problem with the azureus in the repos?

---

### Post by Ondkloss on 2007-10-22
ok, so I removed 2.5.0.4 and tried apt-get install azureus.
unfortunatly I got even shorter doing so, as it crashes when starting.

```
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb460274b, pid=6036, tid=3085011856
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0_03-b05 mixed mode, sharing)
# Problematic frame:
# C  [libglibjni-0.4.so+0xb74b]
#
# An error report file with more information is saved as hs_err_pid6036.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)
```

This happens INSTANTLY after I try to start the app and the splash has finished.
btw, in what directory is this errorlog put?

---

