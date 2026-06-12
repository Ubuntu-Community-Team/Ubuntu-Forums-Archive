---
title: "firefox/audacious closes constantly?"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by keef247 on 2007-05-07
i've just had a problem recently with running azureus and frostwire so installed sun java...(if that helps) and now whenever im on firefox/audacious they both close half way through using them.at random times of use.
how do i fix this and is it the sun java?
cheers

---

### Post by meborc on 2007-05-07
run firefox from terminal and give us the output of the error when it appears :)

---

### Post by keef247 on 2007-05-08
```
dave@mypc:~$ firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
java.io.FileNotFoundException: /home/otacon/.azureus/plugins/bdcc/status.properties (Permission denied)
        at java.io.FileOutputStream.open(Native Method)
        at java.io.FileOutputStream.<init>(FileOutputStream.java:179)
        at java.io.FileOutputStream.<init>(FileOutputStream.java:131)
        at org.cneclipse.bdcc.BDCCPlugin.updateHistoryData(BDCCPlugin.java:75)
        at org.cneclipse.bdcc.BDCCPlugin$2.downloadRemoved(BDCCPlugin.java:165)
        at org.gudy.azureus2.pluginsimpl.local.download.DownloadManagerImpl$1.downloadManagerRemoved(DownloadManagerImpl.java:151)
        at org.gudy.azureus2.core3.global.impl.GlobalManagerImpl$1.dispatch(GlobalManagerImpl.java:100)
        at org.gudy.azureus2.core3.util.ListenerManager.dispatchInternal(ListenerManager.java:374)
        at org.gudy.azureus2.core3.util.ListenerManager.dispatchLoop(ListenerManager.java:450)
        at org.gudy.azureus2.core3.util.ListenerManager$1.runSupport(ListenerManager.java:133)
        at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:69)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Segmentation fault (core dumped)

```

---

### Post by ikonia on 2007-05-09
This is the same error as you posted in a seperate ubuntu forum thread

[http://ubuntuforums.org/showthread.php?p=2620967#post2620967](http://ubuntuforums.org/showthread.php?p=2620967#post2620967)

Why have you posted this exact same error log twice ?

The problem is still the same 

> 
java.io.FileNotFoundException: /home/otacon/.azureus/plugins/bdcc/status.properties (Permission denied)


and then you've posted this exact same error log in another forum 

[http://forums.hexus.net/showthread.php?t=107131](http://forums.hexus.net/showthread.php?t=107131)

You'll get better support if 

a.) you don't post the same issue multiple times with different headers
b.) you keep your reputation in place by not spamming every forum you can find with the same questions 
c.) explain what you've editid in your posts as pretty much every thread you make is edited by you and its hard to know if you've changed any important details.

---

### Post by meborc on 2007-05-14
i hope you have figured it out... but if not then you should change the permissions to that folder... the easiest is to "sudo nautilus" to get root permissions... then go to the folder - right-click and make it read/writeable to your username... should work then

ps. srry - was away for a while... my university studies are finishing and i need to start studying for once in my life :(

---

