---
title: "Azureus crashing."
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by alex-desktop79 on 2007-01-31
When I open azureus, and this has been happening since it's installation, it crashes.
Edit: Explained further. After I open it, I get to the wizard to configure Azureus. I sometimes have the time to press next after selecting English but it crashes either before or after this.

Here is the output:
> 
alex@alex-desktop:~$ azureus
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb0567d02, pid=28710, tid=3084957360
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_08-b03 mixed mode, sharing)
# Problematic frame:
# C  [libglibjni-0.4.so+0x8d02]
#
# An error report file with more information is saved as hs_err_pid28710.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)


Any ideas? Thanks.

---

### Post by alex-desktop79 on 2007-01-31
any help?

---

### Post by the_darkside_986 on 2007-01-31
Your java virtual machine is up-to-date isn't it? well, sometimes the newest version of a software is not the best...

I had trouble getting Azureus to run properly in Suse Linux; I had to leave the folder in my home directory and run it from there because running it from /usr places did not work. So maybe it is another instance of Azureus acting weird on *nix. Running it from your home may or may not help. Sounds like it is the java virtual machines fault.

---

### Post by alex-desktop79 on 2007-02-01
I installed java with Automatix.

What steps can I take/try?

---

### Post by cookfromfrozen on 2007-02-02
I had this problem after upgrading to the azureus that was just added to the repos, the 2.5.0.0-repack version.  

I downgraded back to the earlier version and it still didn't work.

```
sudo apt-get install azureus-gcj
```

fixed it for me, but now I get errors about a missing azupdater plugin.  I never used the built-in azureus updater anyway though.

---

### Post by Zer0Nin3r on 2007-02-04
Alright, I hope that I'll be able to provide some insight.  

I've been having the same problems as well.  I'm running Java 5.0, I've tried reinstalling Java and Azureus without any luck.

I've noticed that if I run Azureus from the terminal with the sudo command it seems to run just fine.  I know lame, but it works.  I'll give an update here in a bit when I complete a download.  Until then here is the output from my terminal:

> changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0x8c453d02, pid=6976, tid=3084662448
#
# Java VM: Java HotSpot(TM) Server VM (1.5.0_08-b03 mixed mode)
# Problematic frame:
# C  [libglibjni-0.4.so+0x8d02]
#
# An error report file with more information is saved as hs_err_pid6976.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)


I've submitted a but report to Sun, but couldn't find the log file for the life of it.

**update**
So, with the sudo command it worked and I was able to download and upload just fine.  I rebooted only to have Azureus crash with & without the sudo command.

**update #2**
I tried this and it ended up working for me (so far):

> **Josey said:**
> I had the same problem and here is the fix...

download the latest azureus here.
[http://azureus.sourceforge.net/index_CVS.php](http://azureus.sourceforge.net/index_CVS.php)
rename Azureus2501-B54.jar to Azureus2.jar and overwrite the old one located in /usr/share/java/

---

