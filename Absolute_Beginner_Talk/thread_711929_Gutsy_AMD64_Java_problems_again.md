---
title: "Gutsy AMD64 Java problems again"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by rednick on 2008-03-01
I'm trying to install Mercury Messenger with little success.
It installs OK but will not run from the Applications menu.

I tried running it in terminal:

> ****@gnu-linux:~$ mercury
- Adding Compiz/beryl compatibility mode.
01.03.2008 12:12:43 Mercury/1.9 [20071020]
01.03.2008 12:12:43 Resource Type > General
01.03.2008 12:12:43 Locations > Loading...
01.03.2008 12:12:43 Locations > Loaded OK.
01.03.2008 12:12:43 Main > Loading Global Settings...
01.03.2008 12:12:43 Main > Loading Splash Screen...
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b9660b0be11, pid=6797, tid=1074792784
#
# Java VM: IcedTea 64-Bit Server VM (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5c9e11]
#
# An error report file with more information is saved as:
# /tmp/hs_err_pid6797.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
/usr/bin/mercury: line 43:  6797 Aborted                 (core dumped) java -Djava.library.path=jni:jni/jmf -Xmx512m -classpath $classpath com.dMSN.Main $*
****@gnu-linux:~$ 

Taking advice I found elsewhere in the forum I installed the Sun packages sun-java6-bin and sun-java6-jre.  Tried again, same result.

So I uninstalled the icedtea packages and tried again:
> bash: javs: command not found
The following packages contain the program Java
cacao

So I installed cacao and still get the same error.

Can anyone give me a pointer please?

---

### Post by rednick on 2008-03-01
I hate bumping posts but as the newbies forum is so busy...

---

### Post by kool_kat_os on 2008-03-01
for some reason i feel like this year this place is a little less active...or maybe its just me

---

