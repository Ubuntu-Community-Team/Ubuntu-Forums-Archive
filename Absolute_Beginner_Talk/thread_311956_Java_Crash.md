---
title: "Java Crash"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by moffa on 2006-12-03
I have installed sun-java5-jre as well as sun-java5-plugin.  When I try to test it at [http://www.java.com/en/download/help/testvm.xml]("http://www.java.com/en/download/help/testvm.xml")
Firefox crashes.  Running firefox from a terminal I get the following error as it crashes:

An irrecoverable stack overflow has occurred.
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb7dea32c, pid=15318, tid=2975476624
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_08-b03 mixed mode, sharing)
# Problematic frame:
# C  [libc.so.6+0x6f32c]  memcpy+0x1c
#
# An error report file with more information is saved as hs_err_pid15318.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
INTERNAL ERROR on Browser End: SendRequest: write failed. Dead VM? 32

System error?:: Broken pipe

Can anyone help?

---

### Post by Sef on 2006-12-03
The easy way to install java:

1. Open Universe and Multiverse repositories.

2. Applications > Add/Remove > Search > Sun Java 5.0

3.  (With Edgy, have the dialog box on the top right say all supported applications.)

4. (With Dapper, click on commercial applications)

5. Click on the two boxes (Sun Java 5.0 and the plug in), and click apply > then follow the directions to finish up.

---

### Post by bcom on 2006-12-03
Sef:

I followed your instructions in re installing Sun Java 5.0 and the plug-in.  Both are there just as you say.  

Prior to installing, I got a warning message that I was about to install unauthenticated software and which could allowg someone to take over the machine.

Question: is this message just warning me about the dangers of running Java or does it refer to potential problems with the downloaded files themselves?

Perhaps it is nothing to worry about at all?

(Running Edgy!)

Thanks

---

### Post by igknighted on 2006-12-03
I believe that warning is telling you that you are installing software from a non-official repo, nothing to do with the software itself.  I don't think I've ever gotten that message tho with java, so thats odd.

---

### Post by bcom on 2006-12-03
Thanks for your response.  You are probably right about it coming from an unofficial repository.

The warning message came up just during the step in which I was supposed to click Apply.

---

### Post by moffa on 2006-12-18
> **Sef said:**
> The easy way to install java:

1. Open Universe and Multiverse repositories.

2. Applications > Add/Remove > Search > Sun Java 5.0

3.  (With Edgy, have the dialog box on the top right say all supported applications.)

4. (With Dapper, click on commercial applications)

5. Click on the two boxes (Sun Java 5.0 and the plug in), and click apply > then follow the directions to finish up.

I tried that, also tried downloading Java Update 10 and running update-alternatives adding java

Nothing seems to work.  I am out of ideas

---

### Post by jvc26 on 2006-12-18
@ moffa: you could try going to the thread [http://www.ubuntuforums.org/showthread.php?t=316980](http://www.ubuntuforums.org/showthread.php?t=316980)
which could sort you out with JDK/JRE 1.6.0 I did that one this morning and it worked.
Il

---

