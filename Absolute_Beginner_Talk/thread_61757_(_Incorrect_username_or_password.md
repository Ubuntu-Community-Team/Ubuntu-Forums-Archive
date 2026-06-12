---
title: ":( Incorrect username or password"
date: 2005-09-02
forum: Absolute Beginner Talk
---

### Post by spingmis on 2005-09-02
Folks, 

Yea, am new to linux and Ubuntu is my first try. I started installing 5.04 version for Intelx86. 

While installing everything was smooth except for while typing/creating useraccounts. When i typed user accounts and passwords it always showed incorrect. So I skipped that step. 

Now after installation and everything, I see a plain screen- with Ubuntu in the middle, and below it is the USERNAME box, I do not understand why is it asking that. 
Below Username, there is language and session. I do not know how to trascend from here. Becoz whatever i type in the username and password, its reverting the same ' incorrect usrname or password. Letters must be typed in correct case' Im stuck here now :( 

I want to proceed further and learn working on Ubuntu, Please help me. My regards for all of you.

---

### Post by palsyboy on 2005-09-02
[QUOTE=spingmis]Folks, 
While installing everything was smooth except for while typing/creating useraccounts. When i typed user accounts and passwords it always showed incorrect. So I skipped that step.[/quote]
I don't have GNOME for reference right now, so I don't remember its user management program.  But if you want to add a user, in this case named Bartholomew, you can open a terminal and type:
```
sudo adduser bartholomew
sudo passwd bartholomew
sudo mkdir /home/bartholomew
sudo chown -R bartholomew /home/bartholomew/

```
> Now after installation and everything, I see a plain screen- with Ubuntu in the middle, and below it is the USERNAME box, I do not understand why is it asking that.
It's asking which user wants to log in.  If Bartholomew wants to log in, he'd type in "bartholomew" at the USERNAME prompt.

If this still fails, then it may be time to reinstall and redo the portion where you add accounts.  If you have another computer available during that time, it would help to search for that same error in these forums or at [www.google.com/linux](www.google.com/linux).  If you don't find anything to help you, type out the error you're getting.

Hopefully, someone else will stop by with more helpful information.

---

### Post by amohanty on 2005-09-02
When the system boots and prompts you to boot into a system, select the 
Uuntu..... Recovery (or something to that effect)
This will drop you into the recovery console.

There use the useradd command to add a user. the manual for useradd:
[http://www.scit.wlv.ac.uk/cgi-bin/mansec?1M+useradd](http://www.scit.wlv.ac.uk/cgi-bin/mansec?1M+useradd)

or you can use adduser:
[http://linux.com.hk/PenguinWeb/manpage.jsp?section=8&name=adduser-ng](http://linux.com.hk/PenguinWeb/manpage.jsp?section=8&name=adduser-ng)

Then you can use the passwd command to set the password for the user:
[http://linux.com.hk/PenguinWeb/manpage.jsp?section=5&name=passwd](http://linux.com.hk/PenguinWeb/manpage.jsp?section=5&name=passwd)

Then use the username and password to login.


HTH
AM

---

