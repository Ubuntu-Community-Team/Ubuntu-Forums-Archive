---
title: "antivirus"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by krisfrajer on 2007-05-22
is there an antivirus available for ubuntu?
If so, which one is good? Is it available from the repositories?
LAst but not least ;) how to run it from the command line.

I appreciate any comments::

---

### Post by krisfrajer on 2007-05-22
Also I want to ask if to run the antivirus do I have to run it as superuser?
How can I switch into root in the graphical mode?

---

### Post by deadgobby on 2007-05-22
Right now at this point you do not need one. Linux virus are rare compare to MS and you'll need to be logged in as root to invoke it.  Here is a link on why you do not need one.
[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)
 If you read your email and it has lets say attached file with virus. Most of them have a exe file and you cannot really open a exe file unless you use Wine windows emulator for example. Yet, you can pass on the email as a forward attachment and give a windows user the virus. Even it you open with Wine, it will go opps and that is it. No damage done.
Gobby

---

### Post by krisfrajer on 2007-05-22
thxs for that comment. I have been reading some other post and some people has also mention that... that i do not need an antivirus in linux. It happens lately my firefox broser crashes on me when checking my e-mail in hotmail. It is so weird... I was suspecting of a virus but then...  must be something else I have done.

Thxs for the link. It was helpful.

---

### Post by aysiu on 2007-05-22
Read this link, too:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

As for Firefox crashing on Hotmail, try this. Open up a [terminal](http://www.psychocats.net/ubuntu/terminal) and type ```
firefox
``` This will open up Firefox but also give you terminal output in case anything happens. When the crash occurs, highlight the errors that appear in the terminal and copy and paste them back here into this thread.

---

### Post by deadgobby on 2007-05-22
Oh the FF bug is in effect for your system. It is really bad in dapper. The reason why it crashes is due to flash player. So depending  which version Ubie you are using there is a couple of fixes. One is to install FF 2.0 and flash player 9. 
[http://ubuntuforums.org/showthread.php?t=279990](http://ubuntuforums.org/showthread.php?t=279990)
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)
 Then to really get it to shut up is flash blocker. Most flash is ads and it is very simple to install too.
[http://flashblock.mozdev.org/](http://flashblock.mozdev.org/)
 Once you install flash blocker. You get a Flash Player symbol and you click on it and it will play. 
 Here is a link to FF bug Triage.
[https://wiki.ubuntu.com/MozillaTeam/Bugs/Triage](https://wiki.ubuntu.com/MozillaTeam/Bugs/Triage)
 It is not a virus, just that darn bug that can cause the questions to why is this doing this too WTF.

Gobby

---

### Post by aysiu on 2007-05-22
Hotmail invokes Flash?

---

### Post by deadgobby on 2007-05-22
Hi aysiu,
 I had bad problems of FF crashing when I was using Dapper on this very site too. There is now flashplayer on this site. But it used to crash. No crashed no.  As you know that FF can be buggy at times.
Gobby

---

### Post by krisfrajer on 2007-05-22
Yeah, I think hotmail does invokes flash. Thanks for your comments on my problem. I have a feeling all the problem turns around flash. I have try to install it in the last few days but not luck since my architecture is not support it by the source offered in the flashplayer's home page. I will give it a try tomorrow.

---

