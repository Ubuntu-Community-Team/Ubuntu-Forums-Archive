---
title: "KTorrent stopped working!"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by Angus77 on 2007-08-21
I was using KTorrent 2.1, but I was thinking it was slow. I read that 2.2 was a lot better, so I installed it (although it wasn't available through Synaptic), and everything was fine for the moment. But the next time I turned on the computer, KTorrent just simply wouldn't start up (no error messages or anything, it just wouldn't start).

I removed it and reinstalled KTorrent 2.1 again using Synaptic, but I still have the same problem.

Can anyone please help?

---

### Post by prince_niceguy on 2007-08-22
Run ktorrent through console and post the error log in the console. We can figure out something from there.

---

### Post by kostkon on 2007-08-22
> **Angus77 said:**
> I was using KTorrent 2.1, but I was thinking it was slow. I read that 2.2 was a lot better, so I installed it (although it wasn't available through Synaptic), and everything was fine for the moment. But the next time I turned on the computer, KTorrent just simply wouldn't start up (no error messages or anything, it just wouldn't start).

I removed it and reinstalled KTorrent 2.1 again using Synaptic, but I still have the same problem.

Can anyone please help?

How did you install it? Assuming you use 7.04, if you activate the *backports* repository in your Software Sources (**System -> Administration -> Software Sources**), you should be able to install the 2.2 version of *KTorrent* from Synaptic.

Thus, try installing it this way. Also, if you're using *Ubuntu*, I don't know about *Kubuntu*, before you run *KTorrent* again, try to delete the configuration file for *KTorrent*, named *ktorrentrc*, that you will find inside your home directory in *.kde/share/config*. Maybe this will solve your problem, but be warned, maybe you will lose any torrents you had downloading and any configurations.

Nevertheless, try doing what *prince_niceguy* has recommended; run it from console and post here any error messages or warnings that *KTorrent* will give.

---

### Post by Angus77 on 2007-08-22
I run ktorrent throught he terminal and it says```
ktorrent is already running!
```

And apparently it is. Some of my torrents have actually finished downloading. But I can't get the interface to display.

I originally downloaded KTorrent 2.2.1 from the KTorrent site, since there was a Feisty package there. 

As kostkon suggested, I enabled backports in Synaptic as (nice to know about that!), but the problem persists. When I click on the KTorrent icon, a spectral window flashes appears to open, but then nothing happens.

---

### Post by kostkon on 2007-08-23
Why don't you just kill the running instance of *KTorrent*? Go to **System -> Administration -> System Monitor** and find it on the list. Then select *End Process*. If this does not work, right click on your selection and do a *Kill Process*.

Then run it again and I believe everything will be OK.

---

### Post by prince_niceguy on 2007-08-23
or alternately run the following command

killall ktorrent

once ktorrent are killed you can start ktorrent again.

---

### Post by Angus77 on 2007-08-23
I tried ending and then killing the process, but I still can't open the interface.

Again, I can still download torrents, but I don't know when they finish. I open a new torrent and choose what files I want and where to save it, etc. but when I check the properties of the files, it says they are the size they would be after they finish downloading. KTorrent still gives me a popup window when a torrent finishes, but if I happen not to see the popup window I have no other way to tell if a torrent is actually finished.

---

### Post by Angus77 on 2007-08-24
I followed prince_niceguy's advice and ran 
```
killall ktorrent
```
and then ran ktorrent again. This time I got this: 
```
Qt: Warning: X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Qt: Warning: Failed to open device
Qt: Warning: X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Qt: Warning: Failed to open device

```

---

### Post by Angus77 on 2007-08-24
I don't know why I bothered doing this, but I ran ktorrent through the terminal immediately after the last post (even though according to the System Monitor it was already running) and got this:
```
ktorrent is already running!
Qt: Warning: QFile::writeBlock: File not open
Qt: Warning: QFile::writeBlock: File not open
Qt: Warning: QFile::writeBlock: File not open
Qt: Warning: QFile::writeBlock: File not open

```

So I assume it has something to do with Qt? which I don't know a whole lot about...

---

### Post by hyper_ch on 2007-08-24
run this and post the result:

```

ps aux | grep ktorrent

```

---

### Post by Angus77 on 2007-08-24
Here's what I get: 
```
andrew    6010  3.7  5.1 408416 105944 ?       Sl   22:29   0:40 ktorrent --icon=ktorrent -caption KTorrent
andrew    6057  0.0  0.4 124804  8844 ?        S    22:29   0:00 kio_file [kdeinit] file /tmp/ksocket-andrew/klauncherVdeRhb.slave-socket /tmp/ksocket-andrew/ktorrentkX8Qga.slave-socket
andrew    6061  0.0  0.4 229252  9224 ?        S    22:29   0:00 kio_http [kdeinit] http /tmp/ksocket-andrew/klauncherVdeRhb.slave-socket /tmp/ksocket-andrew/ktorrentEgE87a.slave-socket
andrew    6062  0.0  0.4 229252  9164 ?        S    22:29   0:00 kio_http [kdeinit] http /tmp/ksocket-andrew/klauncherVdeRhb.slave-socket /tmp/ksocket-andrew/ktorrentrYlFZb.slave-socket
andrew    6063  0.0  0.4 229252  9036 ?        S    22:29   0:00 kio_http [kdeinit] http /tmp/ksocket-andrew/klauncherVdeRhb.slave-socket /tmp/ksocket-andrew/ktorrentrI5Jka.slave-socket
andrew    6386  0.0  0.0   5024   828 pts/0    S+   22:47   0:00 grep ktorrent

```

---

### Post by hyper_ch on 2007-08-24
ktorrent ist sill running...

---

### Post by Angus77 on 2007-08-24
Yeah, I know. But the interface won't open.

---

### Post by Sayers on 2007-08-24
Either you have it automatically start, take that off and maybe just do a hard-restart. That will most-definitely kill it.

---

### Post by hyper_ch on 2007-08-24
Kill those processes:

6010
6057
6061
6062
6063

```

kill -s 6010

```

and so on...

after that do again the ps aux | grep ktorrent

---

### Post by prince_niceguy on 2007-08-24
> **Angus77 said:**
> I followed prince_niceguy's advice and ran 
```
Qt: Warning: X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Qt: Warning: Failed to open device
Qt: Warning: X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Qt: Warning: Failed to open device

```

These are harmless errors. Though you can avoid by removing wacom from the xorg.conf. But main problem is ktorrent. Seems it is getting stuck accessing some file and hence it is not continuing.

I used to use ktorrent but I moved to utorrent over wine as ktorrent was too unstable for me.

---

### Post by Angus77 on 2007-09-08
I removed ktorrent 2.2 completely and replaced it with 2.1, and finally got it to open for me again!

Then 2.2 came in as an official upgrade on Synaptic. I figured the official version would have everything solved, so I installed it. Big mistake! Back to square one.

---

### Post by hyper_ch on 2007-09-08
use rTorrent instead ;)

---

### Post by Angus77 on 2007-09-09
Thanks hyper_ch! 

A solution that works!

---

### Post by hyper_ch on 2007-09-09
using rtorrent?

---

### Post by prince_niceguy on 2007-09-09
using azureus in background on P III system. it keeps downloading in background and I do not have to worry at all of shutdown on my local laptop.

---

### Post by Angus77 on 2007-09-10
rtorrent's great!

I can't get Azureus or uTorrent (with Wine) to work at all. I can add new torrents to KTorrent and they'll download properly, but I can't watch their progress (or even know if they really are progressing until I get a popup window when a torrent is completed!)

---

### Post by prince_niceguy on 2007-09-11
what is the error you are facing with azurerus??? can you post the errors from the terminal?

---

### Post by wolfen69 on 2007-09-11
ktorrent has never worked good for me in gnome. ive tried it several times on fresh installs, and it would freeze up every time. i just stopped using it. i use the default bittorrent client for sharing linux iso's, and bittornado for media files.

---

### Post by Angus77 on 2007-09-14
prince_niceguy:

I've never run azureus from the terminal before. It just never opens up.

Here's the output I get from the terminal:

```
DEBUG::Fri Sep 14 14:15:38 GMT+09:00 2007::com.aelitis.azureus.core.networkmanager.impl.tcp.VirtualBlockingServerChannelSelector::start::92:
    IncomingSocketChannelManager::start::299,IncomingSocketChannelManager::<init>::110,TCPNetworkManager::<init>::111,TCPNetworkManager::<clinit>::41,NetworkManager::getMinMssSize::151,ByteBucket::ensureByteBucketMinBurstRate::150,ByteBucket::<init>::63,ByteBucket::<init>::49,TransferProcessor::<init>::60,NetworkManager::<init>::124,NetworkManager::<clinit>::50,AzureusCoreImpl::<init>::177,AzureusCoreImpl::create::92,AzureusCoreFactory::create::46,Main::<init>::143,Main::main::162
java.net.BindException: Address already in use
        at sun.nio.ch.Net.bind(Native Method)
        at sun.nio.ch.ServerSocketChannelImpl.bind(ServerSocketChannelImpl.java:119)
        at sun.nio.ch.ServerSocketAdaptor.bind(ServerSocketAdaptor.java:59)
        at com.aelitis.azureus.core.networkmanager.impl.tcp.VirtualBlockingServerChannelSelector.start(VirtualBlockingServerChannelSelector.java:79)
        at com.aelitis.azureus.core.networkmanager.impl.tcp.IncomingSocketChannelManager.start(IncomingSocketChannelManager.java:299)
        at com.aelitis.azureus.core.networkmanager.impl.tcp.IncomingSocketChannelManager.<init>(IncomingSocketChannelManager.java:110)
        at com.aelitis.azureus.core.networkmanager.impl.tcp.TCPNetworkManager.<init>(TCPNetworkManager.java:111)
        at com.aelitis.azureus.core.networkmanager.impl.tcp.TCPNetworkManager.<clinit>(TCPNetworkManager.java:41)
        at com.aelitis.azureus.core.networkmanager.NetworkManager.getMinMssSize(NetworkManager.java:151)
        at com.aelitis.azureus.core.networkmanager.impl.ByteBucket.ensureByteBucketMinBurstRate(ByteBucket.java:150)
        at com.aelitis.azureus.core.networkmanager.impl.ByteBucket.<init>(ByteBucket.java:63)
        at com.aelitis.azureus.core.networkmanager.impl.ByteBucket.<init>(ByteBucket.java:49)
        at com.aelitis.azureus.core.networkmanager.impl.TransferProcessor.<init>(TransferProcessor.java:60)
        at com.aelitis.azureus.core.networkmanager.NetworkManager.<init>(NetworkManager.java:124)
        at com.aelitis.azureus.core.networkmanager.NetworkManager.<clinit>(NetworkManager.java:50)
        at com.aelitis.azureus.core.impl.AzureusCoreImpl.<init>(AzureusCoreImpl.java:177)
        at com.aelitis.azureus.core.impl.AzureusCoreImpl.create(AzureusCoreImpl.java:92)
        at com.aelitis.azureus.core.AzureusCoreFactory.create(AzureusCoreFactory.java:46)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:143)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:162)
DEBUG::Fri Sep 14 14:15:39 GMT+09:00 2007::com.aelitis.azureus.core.networkmanager.impl.tcp.VirtualBlockingServerChannelSelector::start::93:
  java.net.BindException: Address already in use
        at sun.nio.ch.Net.bind(Native Method)
        at sun.nio.ch.ServerSocketChannelImpl.bind(ServerSocketChannelImpl.java:119)
        at sun.nio.ch.ServerSocketAdaptor.bind(ServerSocketAdaptor.java:59)
        at com.aelitis.azureus.core.networkmanager.impl.tcp.VirtualBlockingServerChannelSelector.start(VirtualBlockingServerChannelSelector.java:79)
        at com.aelitis.azureus.core.networkmanager.impl.tcp.IncomingSocketChannelManager.start(IncomingSocketChannelManager.java:299)
        at com.aelitis.azureus.core.networkmanager.impl.tcp.IncomingSocketChannelManager.<init>(IncomingSocketChannelManager.java:110)
        at com.aelitis.azureus.core.networkmanager.impl.tcp.TCPNetworkManager.<init>(TCPNetworkManager.java:111)
        at com.aelitis.azureus.core.networkmanager.impl.tcp.TCPNetworkManager.<clinit>(TCPNetworkManager.java:41)
        at com.aelitis.azureus.core.networkmanager.NetworkManager.getMinMssSize(NetworkManager.java:151)
        at com.aelitis.azureus.core.networkmanager.impl.ByteBucket.ensureByteBucketMinBurstRate(ByteBucket.java:150)
        at com.aelitis.azureus.core.networkmanager.impl.ByteBucket.<init>(ByteBucket.java:63)
        at com.aelitis.azureus.core.networkmanager.impl.ByteBucket.<init>(ByteBucket.java:49)
        at com.aelitis.azureus.core.networkmanager.impl.TransferProcessor.<init>(TransferProcessor.java:60)
        at com.aelitis.azureus.core.networkmanager.NetworkManager.<init>(NetworkManager.java:124)
        at com.aelitis.azureus.core.networkmanager.NetworkManager.<clinit>(NetworkManager.java:50)
        at com.aelitis.azureus.core.impl.AzureusCoreImpl.<init>(AzureusCoreImpl.java:177)
        at com.aelitis.azureus.core.impl.AzureusCoreImpl.create(AzureusCoreImpl.java:92)
        at com.aelitis.azureus.core.AzureusCoreFactory.create(AzureusCoreFactory.java:46)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:143)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:162)

DEBUG::Fri Sep 14 14:15:46 GMT+09:00 2007::org.gudy.azureus2.core3.config.impl.ConfigurationManager::getIntParameterRaw::268:
  java.lang.ClassCastException: [B cannot be cast to java.lang.Long
        at org.gudy.azureus2.core3.config.impl.ConfigurationManager.getIntParameterRaw(ConfigurationManager.java:266)
        at org.gudy.azureus2.core3.config.impl.ConfigurationManager.getIntParameter(ConfigurationManager.java:274)
        at org.gudy.azureus2.core3.config.COConfigurationManager.getIntParameter(COConfigurationManager.java:171)
        at org.gudy.azureus2.ui.swt.mainwindow.MainWindow.checkForWhatsNewWindow(MainWindow.java:1543)
        at org.gudy.azureus2.ui.swt.mainwindow.MainWindow.showMainWindow(MainWindow.java:675)
        at org.gudy.azureus2.ui.swt.mainwindow.MainWindow.runSupport(MainWindow.java:571)
        at org.gudy.azureus2.core3.util.AERunnable.run(AERunnable.java:38)
        at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
        at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:123)
        at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3157)
        at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2859)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:125)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:61)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:110)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:147)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:162)

#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002aaadd286c9f, pid=7838, tid=1076017472
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.6.0-b105 mixed mode)
# Problematic frame:
# C  [libglibjni-0.4.so+0x9c9f]
#
# An error report file with more information is saved as hs_err_pid7838.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)
```

So something's wrong with Java rather than azureus?

---

### Post by prince_niceguy on 2007-09-15
download a lower version of the jre and install the same and make azureus use the same... seems some problem with java6...

---

### Post by Angus77 on 2007-09-26
Doesn't seem to have worked...

---

### Post by prince_niceguy on 2007-09-27
seems there is some bug in azureus package which is in the repository. download the version from the net and use the same. should help.

---

### Post by Angus77 on 2007-09-27
I tried it, and this was the output I got:

```
Starting Azureus...
Suitable java version found [java = 1.6.0]
Configuring environment...
Java exec found in PATH. Verifying...
GRE/XULRunner automatically found
Loading Azureus:
java -Xmx128m -cp "./Azureus2.jar:./swt.jar" -Djava.library.path="/home/andrew/Desktop/azureus" -Dazureus.install.path="/home/andrew/Desktop/azureus" -Dazureus.script="Desktop/azureus/azureus" -Dazureus.script.version=2 org.gudy.azureus2.ui.swt.Main 
DEBUG::Thu Sep 27 14:43:38 GMT+09:00 2007::com.aelitis.azureus.core.versioncheck.VersionCheckClient::getVersionCheckInfoSupport::212:
    VersionCheckClient::getExternalIpAddress::312,UtilitiesImpl::getPublicAddress::366,DHTTransportUDPImpl::getExternalAddress::623,DHTTransportUDPImpl::<init>::269,DHTTransportFactory::createUDP::65,DHTPluginImpl::<init>::160,DHTPlugin$11::runSupport::807,AEThread::run::69
java.net.ConnectException: Connection refused
        at java.net.PlainSocketImpl.socketConnect(Native Method)
        at java.net.PlainSocketImpl.doConnect(PlainSocketImpl.java:333)
        at java.net.PlainSocketImpl.connectToAddress(PlainSocketImpl.java:195)
        at java.net.PlainSocketImpl.connect(PlainSocketImpl.java:182)
        at java.net.Socket.connect(Socket.java:519)
        at sun.net.NetworkClient.doConnect(NetworkClient.java:155)
        at sun.net.www.http.HttpClient.openServer(HttpClient.java:388)
        at sun.net.www.http.HttpClient.openServer(HttpClient.java:500)
        at sun.net.www.http.HttpClient.<init>(HttpClient.java:233)
        at sun.net.www.http.HttpClient.New(HttpClient.java:306)
        at sun.net.www.http.HttpClient.New(HttpClient.java:318)
        at sun.net.www.protocol.http.HttpURLConnection.getNewHttpClient(HttpURLConnection.java:792)
        at sun.net.www.protocol.http.HttpURLConnection.plainConnect(HttpURLConnection.java:733)
        at sun.net.www.protocol.http.HttpURLConnection.connect(HttpURLConnection.java:658)
        at com.aelitis.azureus.core.versioncheck.VersionCheckClient.executeHTTP(VersionCheckClient.java:526)
        at com.aelitis.azureus.core.versioncheck.VersionCheckClient.performVersionCheck(VersionCheckClient.java:432)
        at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getVersionCheckInfoSupport(VersionCheckClient.java:205)
        at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getExternalIpAddress(VersionCheckClient.java:312)
        at org.gudy.azureus2.pluginsimpl.local.utils.UtilitiesImpl.getPublicAddress(UtilitiesImpl.java:366)
        at com.aelitis.azureus.core.dht.transport.udp.impl.DHTTransportUDPImpl.getExternalAddress(DHTTransportUDPImpl.java:623)
        at com.aelitis.azureus.core.dht.transport.udp.impl.DHTTransportUDPImpl.<init>(DHTTransportUDPImpl.java:269)
        at com.aelitis.azureus.core.dht.transport.DHTTransportFactory.createUDP(DHTTransportFactory.java:65)
        at com.aelitis.azureus.plugins.dht.impl.DHTPluginImpl.<init>(DHTPluginImpl.java:160)
        at com.aelitis.azureus.plugins.dht.DHTPlugin$11.runSupport(DHTPlugin.java:807)
        at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:69)
```

The interface wouldn't open.

Could this have anything to do with my hardware? I've got amd_64.

---

### Post by prince_niceguy on 2007-09-28
are you behind a firewall or something. seems there is some problem in udp protocol. amd64 should not be an issue. or not sure might be as you might be using 32 bit jar for azureus against 64 bit jvm. try posting this in 64 bit forum. i used to use 64 bit but now i am having all 32 bit cpu so am not using 64 bit.

---

### Post by Angus77 on 2007-09-28
I'm pretty sure I'm not behind a firewall, because my torrents still download all right. The azureus I have is definitely the 64bit version. I guess I'll post in the 64 bit forum. Thanks for your help!

---

