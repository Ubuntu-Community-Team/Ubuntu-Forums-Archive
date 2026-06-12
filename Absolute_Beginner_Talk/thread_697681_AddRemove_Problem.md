---
title: "Add/Remove Problem"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by quedonX on 2008-02-15
This may be a pretty simple question, but I'm not entirely sure.  The problem is, whenever I try to install software with either the add/remove interface, my machine tells me that I do not have a connection to the Internet.  The actual output is a window that says:
"The list of applications is not available. Click on 'Reload' to load it. To reload the list you need a working internet connection."
   Now, I obviously have a working internet connection, so something else is stopping it.  I think it might be my proxy server, so my actual question is do I need to specify proxy settings for add/remove and if so, where can I do that?

Failing that, I don't know what the problem is and any other help would be appreciated.

---

### Post by pytheas22 on 2008-02-15
Try using Synaptic, which is a more powerful GUI for package management, instead of Add/Remove.  Synaptic is under the System>Administration menu.  If it doesn't work right away, try clicking the reload button in the upper-left corner of Synaptic.

---

### Post by taurus on 2008-02-15
You need to make sure you have enable all the repos in /etc/apt/sources.list first before you attend to install any extra stuff to your machine.  So, go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and make sure you put a check mark in front of all the lines except the last one, Source code, and the Cdrom at the window below.  Close it and press Refresh.  Now, see if you can install anything else this time.

---

### Post by tech9 on 2008-02-15
> **quedonX said:**
> This may be a pretty simple question, but I'm not entirely sure.  The problem is, whenever I try to install software with either the add/remove interface, my machine tells me that I do not have a connection to the Internet.  The actual output is a window that says:
"The list of applications is not available. Click on 'Reload' to load it. To reload the list you need a working internet connection."
   Now, I obviously have a working internet connection, so something else is stopping it.  I think it might be my proxy server, so my actual question is do I need to specify proxy settings for add/remove and if so, where can I do that?

Failing that, I don't know what the problem is and any other help would be appreciated.

you may need to setup ntlmaps if you are behind a proxy server.

See this this link...

[http://ubuntuforums.org/showthread.php?t=589854](http://ubuntuforums.org/showthread.php?t=589854)


Key steps to solving this problem

After you install ntlmaps,,,

create a proxy file under /etc/apt.conf.d/

adding Acquire::http::Proxy "http://127.0.0.1:5865/";

and last but not least - SET ALL PROXY SETTINGS TO "Direct Internet Connection" FOR BOTH

System>Preference>Network Proxy and
Synatptic>Settings>Network

---

### Post by quedonX on 2008-02-19
Okay, when I set the repos, the system failed to download the package information, so that didn't help.

I installed ntlmaps, which I was surprised I could even accomplish, and tried to follow your instructions, tech, but I am unable to create a file in etc/apt/apt.conf.d/ due to permission issues.  I'm extremely new to this, so if someone could walk me through the process, that would be great.

---

### Post by quedonX on 2008-02-19
Okay, nevermind.  I found the problem.  Apparently, I entered by username for authentication wrong.  My bad.  Thanks for the help, anyway.

---

### Post by tech9 on 2008-02-20
> **quedonX said:**
> Okay, nevermind.  I found the problem.  Apparently, I entered by username for authentication wrong.  My bad.  Thanks for the help, anyway.

great, I am glad that you got it working! :) As far as the other post, you can always create/modify/delete files under the root account.

Take Care!

T9

---

