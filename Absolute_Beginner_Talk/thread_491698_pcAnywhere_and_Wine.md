---
title: "pcAnywhere and Wine??"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by steven_vo on 2007-07-03
Is it real ?
I have a look at

**[http://appdb.winehq.org/appview.php?iAppId=917](http://appdb.winehq.org/appview.php?iAppId=917)**

Can you explain to me if pcAnywhere can run on Ubuntu Feisty 7.04 with Wine?
Which version for pcAnywhere and Wine i can use ?

---

### Post by enopepsoo on 2007-07-03
I would bet on a newer version.  I can't honestly think it would work though.

Why not use Hamachi and VNC, or something like that?  

SSH even?   You can play bsd games over SSH.

---

### Post by VorDesigns on 2007-07-10
pcAnywhere's older versions, 10 and 10.5 and maybe the newer versions have a Remote Host which worked at least with SUSE Linux distributions, you could install the host from a Win workstation and then take control of the Linux host.  Not as graceful as the Win installation but viable.  The down side was that the host would uninstall at reboot.  I never took the time to figure out how to get it to run as a daemon post gui load.
pcAnywhere also has a WebRemote, again, at least with the older versions that will run in a browser that has the Sun Java plug in.
I just got this running by adding the following to my installation:
```
apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

```
You will need to add sudo if you don't run interactive root sessions.

to If you have a pcAnywhere host running somewhere and the java plugin, you could try the web client via this link [pcAnywhere Web Remote 1.0]("http://www.vordesigns.com/pca").
You will need a client running for the Remote Host install for Linux to be a host.
None of the above requires Wine to run.

The down side is that you don't get file transfer and at least for the Dapper desktop, you need to change the ctrl-alt-d hotkey to do nothing so that you can log into a locked Win system.  the Web tfs is buggy and the keyboard may become unresponsive on the host unless you send the ctrl-alt-del via the ctrl-alt-d keyboard combo

---

