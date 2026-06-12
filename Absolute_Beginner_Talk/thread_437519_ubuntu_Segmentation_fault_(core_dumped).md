---
title: "ubuntu Segmentation fault (core dumped)"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by keef247 on 2007-05-08
ubuntu Segmentation fault (core dumped)

when running firefox or audacious.
firefdave:mypc:~$ firefox
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
at org.gudy.azureus2.pluginsimpl.local.download.DownloadManagerImpl$1.downloadManagerRemoved(DownloadMa nagerImpl.java:151)
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

---

### Post by Qchan on 2007-05-08
[b][color=darkred]
It appears to be trying to load up something for your .azureus folder. If you don't have permission to your .azureus folder, you can type:

> 
cd /home/otacon/.azureus

sudo chown <your username> * -r


Now try again and it should work for ya, buddy.
[/b][/color]

---

### Post by ikonia on 2007-05-09
The error is right there - in clear text english
java.io.FileNotFoundException: /home/otacon/.azureus/plugins/bdcc/status.properties (Permission denied)


You've posted this other forums two, try keep it specific.

[http://forums.hexus.net/showthread.php?t=107131](http://forums.hexus.net/showthread.php?t=107131)

along with pretty much every other thread you post here.

---

### Post by keef247 on 2007-05-09
> **ikonia said:**
> The error is right there - in clear text english
java.io.FileNotFoundException: /home/otacon/.azureus/plugins/bdcc/status.properties (Permission denied)


You've posted this other forums two, try keep it specific.

[http://forums.hexus.net/showthread.php?t=107131](http://forums.hexus.net/showthread.php?t=107131)

along with pretty much every other thread you post here.
*snip*

---

### Post by keef247 on 2007-05-09
nope its now coming up with this.
```
firefdave@mypc:~$ firefox
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
java.io.FileNotFoundException: /home/dave/.azureus/plugins/bdcc/status.properties (Permission denied)
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

### Post by synd7 on 2007-05-09
did you first run azureus as root? that could cause the permission problem

Try just deleting the .azureus folder, then run azureus as your user, this will recreate the folder with proper permissions (probably :) )

---

### Post by ikonia on 2007-05-09
Read what I said

the error is in clear text - and still is

> 
java.io.FileNotFoundException: /home/dave/.azureus/plugins/bdcc/status.properties (Permission denied)


look at the permissions on that directory.

Instead of flaming me for giving you sound advice and making myself "look good" because I don't know the real answer etc etc, take a look at what I actually posted and you'll see  - its the correct advice.

synd7 - you made a good point, but the fact that its running in his home dir suggests to me he didn't run it as root although I'm not sure how sudo would have delt with this.

---

### Post by freebird54 on 2007-05-09
Doesn't using sudo instead of gksudo where appropriate (graphical progs) lead to this sort of permissions snafu?  Haven't done it yet - but I will :)

---

### Post by ikonia on 2007-05-09
potentially, yes. 

The fact that its running in his own home dir suggests its using his environment variables so would not have been run as root, but I'm not clear if sudo will execute the command using root permissions and the users own environment variables, or if it does the equivilant of a an su - "run command" exit although in a more internal process.

Even so resolving the permissions on the home dir as I've said twice to him should at least clear up that error and either fix it or remove the masking of another error.

could also remove the plugin from the firefox plugin dir to startup fixfox without the plugin to prove it is this causing the problem, but its probably not worth it as the error log is pretty blunt at pointing to an error.

---

### Post by keef247 on 2007-05-09
so what should i do now?well comfused:S
whats the solution?

---

### Post by ikonia on 2007-05-09
I've said in two other posts.
> 
java.io.FileNotFoundException: /home/dave/.azureus/plugins/bdcc/status.properties (Permission denied)


the user launching azuresus wants to read at least - maybe even write to the directory 
/home/dave/.azureus/plugins/bdcc and at least wants to be able to read the status.properties file.

Check the permissions on these files and directories make sure they are at least readable by the user launching firefox/azuresus.

Change the permissions to something readable if they are not already and then you can remove that error and it will either work or give you another error to fix.

Incidentally, I love the way you accused me of not knowing anything, used offensive and abusive language towards me when I was just telling you answer all along, and now you come asking for more help without even acknowleding that you where a bit out of line or "sorry".

Great attitude, please help - then abuse, then realise you need more help so pretend it didn't happen.

---

### Post by keef247 on 2007-05-09
don't flatter yourself sunshine. i wasn't asking you i was asking the mario avator guy actually:D
hence why i messaged him(Y)

---

### Post by ikonia on 2007-05-09
Very dissapointing, 

he's given you the correct chown command, the errors been explained to you crystal clear on multiple occasions, you've been rude and offensive and had to have a moderator edit your thread to remove the bad and offensive language, people are still willing to help you and your not even gracious enough to say "thanks" or "sorry".

Very dissapointing.

---

