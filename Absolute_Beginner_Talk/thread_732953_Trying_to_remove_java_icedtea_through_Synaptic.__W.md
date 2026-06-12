---
title: "Trying to remove java icedtea through Synaptic.  Will it ruin Open Office?"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by thane1 on 2008-03-23
Trying to remove IcedTea-java7-jre through Synaptic, as my 64bit Ubuntu Gutsy system is giving error msgs, when I try to run a java-dependent prog.  Error msgs say the IcedTea is at fault.  Was using Sun-java6-jre before with no problems.  Cannot remember exactly how I came to put the IcedTea on my machine as well, whether it was through Synaptic or another route.  Anyway it shows up in Synaptic, but when I try to remove it I get a "Mark Additional Required Changes?" prompt, which states Open Office progs are going to be affected.  Is this going to mess up my Open Office if I proceed?  I've removed the SunJava6 already and wanted to remove the IcedTea, then reinstall the SunJava6.  I don't use Evolution, but Synaptic says OpenOffice.Org,  OpenOffice.org-base, OpenOffice.org-Evolution and OpenOffice.org-java-common will be affected.  The actual java prog I'm trying to remove by the way is   IcedTea 64-Bit Server VM (1.7.0-b21) for linux-amd64 JRE (1.7.0-b21).  Thanks

---

### Post by ghost_ryder35 on 2008-03-23
> **thane1 said:**
> Trying to remove IcedTea-java7-jre through Synaptic, as my 64bit Ubuntu Gutsy system is giving error msgs, when I try to run a java-dependent prog.  Error msgs say the IcedTea is at fault.  Was using Sun-java6-jre before with no problems.  Cannot remember exactly how I came to put the IcedTea on my machine as well, whether it was through Synaptic or another route.  Anyway it shows up in Synaptic, but when I try to remove it I get a "Mark Additional Required Changes?" prompt, which states Open Office progs are going to be affected.  Is this going to mess up my Open Office if I proceed?  I've removed the SunJava6 already and wanted to remove the IcedTea, then reinstall the SunJava6.  I don't use Evolution, but Synaptic says OpenOffice.Org,  OpenOffice.org-base, OpenOffice.org-Evolution and OpenOffice.org-java-common will be affected.  The actual java prog I'm trying to remove by the way is   IcedTea 64-Bit Server VM (1.7.0-b21) for linux-amd64 JRE (1.7.0-b21).  Thanks
Open Office is java based so you must have a java program installed to use it.  You can remove IcedTea and install Sun and you will not have any problems.

---

### Post by spiderbatdad on 2008-03-23
To fix your icedtea:

install icedtea-gcjwebplugin_1.0-0ubuntu3
If you are having trouble with ff3 browser and java,
then create a  symlink:
```
$ sudo sed -i 's/XINERAMA/FAKEEXTN/g' /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/xawt/libmawt.so
$ cd /usr/lib/firefox-addons/plugins/
$ sudo ln -s /etc/alternatives/firefox-3.0-javaplugin.so
```

[https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/173966](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/173966)

---

### Post by thane1 on 2008-03-23
Thanks for the replies.  Unfortunately there's no joy yet.  What I've done so far:  Removed SunJava6 and also removed the IcedTea7.  Reinstalled SunJava6 (jre).  Still got error msgs including the Gutsy instl'n doesn't seem happy without the IcedTea installed judging by various error msgs.  So I've done a reinstall of IcedTea jre.  Still wouldn't work as installed.  Tried next to sudo apt-get install the icedtea-gcjwebplugin_1.0-0ubuntu3 program.  Not findable through apt-get install.  Back to synaptic where in the description for icedtea-java7-plugin the description says java plugin based on OpenJDK  and gcjwebplugin.  I've installed that program now and still have the same error message, when I try to run java progs.  The error output from Terminal is below.  I did a search for libjvm through Synaptic to see if it was an installable/installed lib file with no success.  Any ideas?  Thanks

#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002acc60a2ce11, pid=6655, tid=1074792784
#
# Java VM: IcedTea 64-Bit Server VM (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5c9e11]

---

### Post by thane1 on 2008-03-23
Still no luck with this.  However I have found a couple of references by googling to linking the path to an unrecognized libjvm.so through a conf file.  Quite frankly trying to follow these threads though, these people are running servers, one is on RedHat, etc and they are way beyond my knowledgebase and I've no idea, what their solutions are referring to.  Some of the directories they're quoting aren't on my Ubuntu system, etc.  Has anyone had experience with linking this libjvm.so file to whatever might cure this problem on an Ubuntu Gutsy 64bit system?  I think the file it has to be linked to or to have a path set to is /etc/ld.so.conf.d (but I can see myself really messing up here, if I go at it without more knowledge).  My ld.so.conf.d directory has 2 files in it - libc.conf and x86_64-linux-gnu.  The gnu file looks like a dead end in this case.  The libc.conf contents are: 
# libc default configuration
/usr/local/lib

There's no reference to libjvm.so here.  Am I onto something here?  Thanks

p.s. - don't like editing my posts after posting.  But have just found my /etc/ld.so.conf file (must be blind).  Its contents are   include /etc/ld.so.conf.d/*.conf  (still not much farther ahead, but might make a bit more sense)

---

