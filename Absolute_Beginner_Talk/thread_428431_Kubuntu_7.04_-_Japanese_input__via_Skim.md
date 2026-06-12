---
title: "Kubuntu 7.04 - Japanese input  via Skim"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by kaminix on 2007-04-30
Well... it won't work, how do I solve it?
I've installed Skim and anthy and set the toggle to ctrl+space, but still nothing happen!

---

### Post by frafu on 2007-05-01
The [following tutorial]("http://ubuntuforums.org/showthread.php?t=396135&highlight=skim") might help.

Further, I am moving this thread to the "Absolute Beginner Talk" forum, where it is more appropriate. 

Have a nice day.

---

### Post by kaminix on 2007-05-02
> **frafu said:**
> The [following tutorial]("http://ubuntuforums.org/showthread.php?t=396135&highlight=skim") might help.

Further, I am moving this thread to the "Absolute Beginner Talk" forum, where it is more appropriate. 

Have a nice day.
Yes, it worked. However, I can only get SCIM working and not SKIM :(

---

### Post by J.Blues on 2007-05-21
Hey kaminix if you still want to get skim to work instead of scim here is something that might help you:

[http://scim.sourceforge.net/skim/doc/user/en/](http://scim.sourceforge.net/skim/doc/user/en/)

it tells you what to do in order to have skim as your front end instead of scim. Skim uses scim as back end and therefore the only thing changing will be the looks of your panel. skim was designed to be used in KDE applications. basically you have to enter the command 
in terminal "scim-panel-kde -d -f" you don't have to be root for that. 
_but before trying starting skim,_ please make sure that scim-lib and scim-panel-gtk are **NOT** running; if they are, kill them: first kill scim then scim-panel-gtk as follows:
          "killall scim-launcher"
          "killall scim-panel-gtk"
after that enter "scim-panel-kde -d -f" in terminal. after this open the configure dialog (click the configure action) and go to Global Settings -> General SCIM, change these settings as followings:

              Panel Program: scim-panel-kde 
              Config Module: kconfig

These modifications are only required the first time you use skim. After this modification, scim will know you prefer skim and will use skim automatically. So all you should do to start skim and scim-lib is just

%scim -d

or

%skim -d


this information comes from: The Skim handbook at: 
[http://scim.sourceforge.net/skim/doc/user/en](http://scim.sourceforge.net/skim/doc/user/en)

Hope this helps...:popcorn:

---

