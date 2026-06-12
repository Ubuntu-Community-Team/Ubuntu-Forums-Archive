---
title: "[SOLVED] How do I install KDE?"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by cygnis1 on 2007-09-28
I tried :sudo aptitude install kde-desktop.  It went through the installation process just fine then there was a screen in the terminal.  It looked like a warning.  At the bottom of the screen was <ok> when I pressed enter nothing happens.  Here is the screen.

You have several choices for general configuration at this point.  If     &#8593;  
 &#9474; you have your debconf priority set to 'low' or 'medium', you will be      &#9646;  
 &#9474; asked more questions later.  You can always run "dpkg-reconfigure         &#9618;  
 &#9474; --priority=low postfix" at a later point if you want to see these         &#9618;  
 &#9474; questions again.                                                          &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; No configuration - IF YOU WANT THE INSTALL TO LEAVE YOUR CONFIG ALONE,    &#9618;  
 &#9474; CHOOSE THIS OPTION.  No configuration changes will be done now:  If you   &#9618;  
 &#9474; have not already configured Postfix, your mail system will be broken and  &#9618;  
 &#9474; should not be used. You must then do the configuration yourself by        &#9618;  
 &#9474; editing /usr/share/postfix/main.cf.dist and saving your changes as        &#9618;  
 &#9474; /etc/postfix/main.cf, or by running dpkg-reconfigure Postfix.  main.cf    &#9618;  
 &#9474; will not be modified by the Postfix install process.                      &#9618;  
 &#9474;                                                                                                                                 &#9474;  
 &#9474; Internet site - mail is sent and received directly using SMTP. If your    &#8593;  
 &#9474; needs don't fit neatly into any category, you probably want to start      &#9618;  
 &#9474; with this one and then edit the config file by hand.                      &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; Internet site using smarthost - You receive Internet mail on this         &#9618;  
 &#9474; machine, either directly by SMTP or by running a utility such as          &#9618;  
 &#9474; fetchmail. Outgoing mail is sent using a smarthost. optionally with       &#9618;  
 &#9474; addresses rewritten. This is probably what you want for a dialup system.  &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; Satellite system - All mail is sent to another machine, called a "smart   &#9618;  
 &#9474; host" for delivery.  No mail is received locally.                         &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; Local delivery only - You are not on a network.  Mail for local users is  &#9646;  
 &#9474; delivered.                                                                &#8595;  
 &#9474;                                                                              
 &#9474;                                  <Ok>                            
Thanks,
Cygnis1

---

### Post by Jimmyfj on 2007-09-28
From a terminal you can run this command:

```
sudo apt-get install kde
```

This should install KDE desktop. Remember to have your install disk ready while installing this GUI.

---

### Post by bobplano on 2007-09-28
usually people install kubuntu-desktop. that is basically just like if you had kubuntu, you have all the packages it comes with. kde-core has some packages but not as many as kubuntu-desktop. kdebase is just the GUI with the necessary libraries. kde installs different packages from the kubuntu-desktop metapackage

---

### Post by Marc Hoffman on 2007-09-28
try having a look here;

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

This site is a great mine of information.

---

### Post by AndyCooll on 2007-09-28
```
sudo apt-get install kubuntu-desktop
```

That should do the job!

:cool:

---

### Post by fuscia on 2007-09-28
*sudo apt-get install kde-core*

you can always add to it and it's faster than the other options. the other options will install kdm, which you may not want.

---

### Post by GSF1200S on 2007-09-28
> **fuscia said:**
> *sudo apt-get install kde-core*

you can always add to it and it's faster than the other options. the other options will install kdm, which you may not want.

Yeah, definitely go KDE core.. Ill second that Kubuntu seems a little bloated. I guess it depends on whether or not you want the kitchen sink.

I would also suggest using aptitude when you install kde-core or kubuntu-desktop. Ex:

```
sudo aptitude install kde-core
```

This way, if you decide you dont like it, you can do a:

```
sudo aptitude remove kde-core
```

and ALL the kde libs and dependencies pulled to install it will be removed. You can do the same with apt-get, but theres additional commands you need to add so that apt tracks what it d/l's (any of you guys know those inputs). Just a thought...

Enjoy KDE! :)

---

### Post by cygnis1 on 2007-09-28
Thanks to all.  I used sudo aptitude install kubuntu desktop.  My problem is when everything is downloaded, I get a warning of some sort.  How do I configure it.  On the psycocats website it is all cut and dried, but I have yet to do anything in linux that follows the instructions.
Cygnis1

---

### Post by Malibu Illusion on 2007-09-28
> **GSF1200S said:**
> I would also suggest using aptitude when you install kde-core or kubuntu-desktop. Ex:

```
sudo aptitude install kde-core
```

This way, if you decide you dont like it, you can do a:

```
sudo aptitude remove kde-core
```

and ALL the kde libs and dependencies pulled to install it will be removed.

This accomplishes the same in Ubuntu with apt-get:

```
sudo apt-get autoremove
```

> **cygnis1 said:**
> My problem is when everything is downloaded, I get a warning of some sort.  How do I configure it.

Warning stating what?  Configure what?

Just logout of your session, then on the login screen you should see that you have the option to select the WM for the next session.  Choose KDE and you'll boot to a KDE desktop.  You can then configure it, assuming that is what you meant.

---

### Post by cygnis1 on 2007-09-28
Please see original post.  I have the "warning" posted.  It occurs in the terminal, there is an <Ok> at the bottom of the warning but it won't do anything.  That is my problem.
Cygnis1

---

### Post by Malibu Illusion on 2007-09-28
You need to press the tab key to actually select the "OK" button and hit enter for it to do anything, which I'm assuming you haven't done.

---

### Post by cygnis1 on 2007-09-28
Thanks, it is up and running now
Cygnis1

---

### Post by Malibu Illusion on 2007-09-28
Glad we were able to help.  You are encouraged to [mark your thread as solved](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads).

Take care.

---

