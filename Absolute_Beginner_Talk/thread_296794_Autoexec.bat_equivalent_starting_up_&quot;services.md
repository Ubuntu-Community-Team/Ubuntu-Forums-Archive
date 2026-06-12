---
title: "Autoexec.bat equivalent/ starting up &quot;services&quot; automatically"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by lilalfyalien on 2006-11-10
Hi,

I have tomcat running under apache, or at least I did last night! We I restarted my computer Apache automatically starts up but Tomcat doesn't. Is there an equivalent to the autoexec.bat file in Windows in Ubuntu?

How can I get Tomcat to start automatically and before Apache?

Thanks,

Lilalfyalien

---

### Post by 23meg on 2006-11-10
[http://www.ubuntuforums.org/showthread.php?t=296792](http://www.ubuntuforums.org/showthread.php?t=296792)

---

### Post by rlozano on 2006-11-10
> **lilalfyalien said:**
> Hi,

I have tomcat running under apache, or at least I did last night! We I restarted my computer Apache automatically starts up but Tomcat doesn't. Is there an equivalent to the autoexec.bat file in Windows in Ubuntu?

How can I get Tomcat to start automatically and before Apache?

Thanks,

Lilalfyalien

in preference, there is session and under the session tab there is startup. you can add and remove from there. would that help?

---

### Post by lilalfyalien on 2006-11-10
The thig is is that I have to start Tomcat before APache and I originally installed a LAMP server so Apache is starting with teh computer rather than with a session. Is there anyway I can get Tomcat to start with the computer. I think "boot/init.rd" flashes by when the computer started. Would this help at all?

---

### Post by 23meg on 2006-11-10
Figure out where Apache and Tomcat are started in your startup scripts and put Tomcat before Apache, and experiment with putting a "sleep" command after Tomcat so the start of Apache will be delayed.

---

### Post by lilalfyalien on 2006-11-11
Ok, where can I find my startup scripts?

---

### Post by 23meg on 2006-11-12
They're in /etc/init.d . These may solve your problem:

[http://mail-archives.apache.org/mod_mbox/tomcat-users/200012.mbox/%3C3.0.6.32.20001212094957.0092cd90@lyrch.cit.gu.edu.au%3E](http://mail-archives.apache.org/mod_mbox/tomcat-users/200012.mbox/%3C3.0.6.32.20001212094957.0092cd90@lyrch.cit.gu.edu.au%3E)
[http://www.raibledesigns.com/tomcat/boot-howto.html](http://www.raibledesigns.com/tomcat/boot-howto.html)

Make sure the paths presented in the solutions actually correspond to the ones in your installation. I can't give more specific help because I don't have any experience with your issue but if you do a web search for "tomcat before apache" many solutions for different installations will come up.

---

