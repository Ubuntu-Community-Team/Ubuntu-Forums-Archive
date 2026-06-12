---
title: "Installation problems"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by lindholm on 2006-05-06
Okay, I read the newbie link on installing software. My problem is with debian installations. All the link says is how to install a .deb package and then is says..

"That's it... well, as long as there are no dependencies."

Great. I have dependencies. The first program I tried to load is qtstalker 0.32. I can install 0.26 using the Kubuntu installation programs but I can't upgrade it even with the newest packages uploaded. So I follow the installation instructions and get told I am missing a library. I get the library and when I try to install it, I am told it conflicts with another library. Yet, when the program seems to run with the newest version. However, if I run the package manager, it decides that I am missing dependencies and uninstalls the program (I guess for my own good) and I can't seem to stop it from doing so. 

I also tried to install some other programs and I get similar problems. How do I fix this?

My rant. I have a huge hard drive. Why can't I simply install every library out there? Conversly, why don't developers have these libraries install when you run their programs? I have asked other Linux-wannabees about these problems and installing programs is the number-one pet peeve. Also, why don't developers tell you where the package installs the executable file or at least give you the option to select where to install it? 

Sorry for the rant. Wasted most of the morning trying to install simple programs. Tell me again why i am trying to switch? Sigh.

---

### Post by mostwanted on 2006-05-06
[QUOTE=lindholm]My rant. I have a huge hard drive. Why can't I simply install every library out there? Conversly, why don't developers have these libraries install when you run their programs? I have asked other Linux-wannabees about these problems and installing programs is the number-one pet peeve.[/QUOTE]

Some libraries that accomplish the same tasks conflict, there's no getting around it. In Windows you can't even install a new version of Internet Explorer or Media Player without removing the old version, so don't tell me it's something Linux-specific. That said, I have never had any such problems myself (it's removed things automatically before, but not something I need).

[QUOTE=lindholm]Also, why don't developers tell you where the package installs the executable file or at least give you the option to select where to install it? [/QUOTE]

The packages do tell you that. Take a look at this, the third point:

[http://monkeyblog.org/ubuntu/installing.html#where_did_it_go](http://monkeyblog.org/ubuntu/installing.html#where_did_it_go)

[QUOTE=lindholm]Tell me again why i am trying to switch? Sigh.[/QUOTE]

I don't know, you tell me.

---

### Post by skippy81 on 2006-05-06
Are you using a package manager to do this?  It should automatically download everything you need along with it,

I've installed tons of stuff and never once had an issue with dependencies.  It can be painful if you are downloading from another PC and copying accross of course.

Please explain the method you are using to try and install stuff.

---

### Post by lindholm on 2006-05-06
The package manager shows the newest version of qtstalker as 0.26. I updated the package manager and it still says that the newest version available is 0.26. When I go to the software development page, 0.32 is available and it is a better version. I download the .deb file and use the "sudo dpkg -i ______.deb" command-line command. I get an error message that there is a missing library. When I found the library online, I attempted to install it (it was also a .deb package) and it said that there was a conflict with a library. However, the program runs at 0.32. Great. 

The problem is that the package managers are now useless as they automatically uninstall qtstalker since there are conflicts. I can't figure out how to turn this off in the package managers. 

I also tried to install a software program not available in the package manager and I received pretty much the same error messages. As well, when I attempt to run a package manager, the program gets uninstalled, even though it will still run with errors (which I don't understand). 

On a side note, how do you get a program entered into the Ubuntu default packages? Just wondering why the qtstalker program has the older version available but not the newer version. I have not asked the developer yet. Just curious.

---

### Post by mostwanted on 2006-05-06
[QUOTE=lindholm]On a side note, how do you get a program entered into the Ubuntu default packages? Just wondering why the qtstalker program has the older version available but not the newer version. I have not asked the developer yet. Just curious.[/QUOTE]

Because Breezy is now 7 months old. The Ubuntu policy is to only upload security updates and bugfixes once the feature freeze starts (occurs a couple of weeks before a new release). There's a possibility your software is available from the backports project, but if you want new software, use Ubuntu 6.06 aka Dapper Drake which will officially be released in less than a month.

And the developer doesn't control whether his program gets to be on the Ubuntu repositories or not, it's the Ubuntu developers who build and put up packages in the repos.

edit: Sorry if I sound a little cranky, it's getting late over here :)

---

### Post by lindholm on 2006-05-06
Thanks. I was reading the developers posts and he didn't seem to know if the newest version was available in any packages. Hopefully, the developers will add the upgrades. Is there a place where users can make suggestions as to software packages? Also, will it be easy to upgrade to 6.06 when it is released or will I have to wipe everything?

Don't worry about being grumpy. I was out of sorts myself after battling with this for hours. I have used Linux off and on since 1996 and I really want to use it permanently now. Growing pains, I guess. 

Thanks for all the assistance.

---

