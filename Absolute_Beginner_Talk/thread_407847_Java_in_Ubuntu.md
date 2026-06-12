---
title: "Java in Ubuntu"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by mojo123 on 2007-04-12
I need help with installing java on ubuntu, people say i need multiverse where can i find that and, when i go to add and remove programs and i try to add java it sais application might not support ur system architecture

---

### Post by aysiu on 2007-04-12
You can enable Multiverse by following [these instructions](http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories) or [these instructions](http://www.psychocats.net/ubuntu/sources).

Ordinarily, you can install Java by following [these instructions](https://help.ubuntu.com/community/Java).

What is your system architecture, though? PowerPC? AMD64?

---

### Post by rbprogrammer on 2007-04-12
i always install java straight from [http://java.sun.com/]("http://java.sun.com/") ..

its supposed to be more up to date

 .. but there is a lot that is available.... 

what do you want the java to do? is it for development (ie. JDK), or just run java programs/applets (ie. JRE) ?

---

### Post by compmodder26 on 2007-04-12
Go into System->Administration->Synaptic Package Manager.  In Synaptic, select Settings->Repositories.  A new window will appear.  Place a checkbox next to "Software restricted by copyright or legal issues (multiverse)", then click close.  Click "Reload".  After it finishes, click "Search".  In the search box, search for the term "sun".  A new list of packages should appear.  In that list, you should see the sun java packages.

---

### Post by gh0st on 2007-04-12
You should check out Easy Ubuntu, it takes all the pain out of getting things like Java sorted :)

[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

There are pretty good instructions on the site, it should sort you out. If you want to add the Universe to your sources you can do it from the menu - System / Administration / Software Sources

There should be a load of tick boxes on the tab that pops up when you open the window for all the various different repositories. There should be one for Universe.

Good luck :)

EDIT: About 5 people replied while I was typing this. Damn you fast typers ;) :)

---

### Post by aysiu on 2007-04-12
There are, on the page I linked to earlier--the last link, special instructions for [AMD64](https://help.ubuntu.com/community/Java#head-6524a0c56845e40dccd32676dad42830325e5707) and [PowerPC](https://help.ubuntu.com/community/Java#head-81c3789bc76872336f69a7af90d1759ef38eeb64), neither of which can use the Sun Java plugin. You have to use Blackdown instead.

---

### Post by mojo123 on 2007-04-12
i just wanted java sso i can use frostwire btw i put a check on everything just in case and when i try to install java from add and remove i still cant open frotstwire

---

### Post by aysiu on 2007-04-12
> **mojo123 said:**
> i just wanted java sso i can use frostwire btw i put a check on everything just in case and when i try to install java from add and remove i still cant open frotstwire
What do you mean by "i put a check on everything"? Follow the instructions to install Java.

What system architecture are you using? Do you not know? If you don't know, we can help you figure it out.

---

### Post by mojo123 on 2007-04-12
im sorry but i dont know sorry if im waisting ur time

---

### Post by aysiu on 2007-04-12
You're not wasting anybody's time. Just explain *exactly* what you've tried. 

We also do need to know what system architecture you're using. Either say what it is, or say you don't know, and we'll work from there.

---

### Post by mojo123 on 2007-04-12
im sorry but i dont know

---

### Post by mojo123 on 2007-04-12
I tried enabling all of the universs and im installing some java packages on synamptic

---

### Post by aysiu on 2007-04-12
Okay. Let's start with what architecture you have, then.

Go to [the terminal](http://www.psychocats.net/ubuntu/terminal) (if you don't know where that is, click on [this link](http://www.psychocats.net/ubuntu/terminal) and paste in this command ```
uname -m
``` You can paste into the terminal by right-clicking and selecting **Paste**

Whatever the terminal says back to you, highlight that with your mouse, right-click, select copy, and then paste back into this thread.

---

### Post by mojo123 on 2007-04-12
i686 btw thank u so much for helping linux is the best

---

### Post by aysiu on 2007-04-12
i686. Shouldn't have any system architecture problems with Sun Java, then.

You said you have Universe enabled. Make sure that you have Multiverse enabled. That's what you really need for Java.

[These point-and-click instructions for enabling Multiverse](http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories) should help you do that. If you prefer to copy and paste a text file, you can follow [these instructions](http://www.psychocats.net/ubuntu/sources).

Once you have Multiverse enabled, we'll move to the next step.

---

### Post by mojo123 on 2007-04-12
ok i did AFTER I REALODED i got this error W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_multiverse_binary-i386_Packages)

---

### Post by aysiu on 2007-04-12
Well, it looks as if you have some duplicate sources.

A source is basically a place that stores software for you to install.

Can you go back to Settings > Repositories and see if you have two of the same repositories checked off? (You're looking particularly for dapper-security universe and dapper-security multiverse). Uncheck **one** of **each**. Then click *Reload* again.

---

### Post by mojo123 on 2007-04-12
ok i fixed it

---

### Post by aysiu on 2007-04-12
> **mojo123 said:**
> ok i fixed it
Great.

So click *Search* in Synaptic and search for *sun-java5-jdk*

Right-click that package and select *Mark for Installation*.

Then click *Apply*, and answer all the prompts.

When you're done, close Synaptic.

---

