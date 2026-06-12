---
title: "Installing Wiki"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by cindylivengood on 2008-04-18
Hi.  Thanks to some really great people who helped me get this far I am ready to install the wiki program.  However, I notice that it comes with an older version of apache and mysql.  When it asks to proceed, I chose no.  If I choose yes, will it overwrite newer versions of those files or bypass them?

---

### Post by RealPSL on 2008-04-19
Why not just install mediawiki directly from the Ubuntu repository so get all the components that ship with Ubuntu. You can use ```
aptitude install mediawiki
``` from a command prompt. Or you can search mediawiki in synaptic. It will then install all the components needed. These might not be the cutting edge releases but you will be current at least to the releases packaged with Ubuntu and those are generally current at least to 6 months.

---

### Post by cindylivengood on 2008-04-19
Ok.  I didn't know it was in there.  Actually, I didn't know there was a repository for people like me to use.  Humm... now I have to go on an Ubuntu treasure hunt. Thanks!!
Ok, so now I show my noobieness.  How does one find out what's in the repository?

---

### Post by RealPSL on 2008-04-20
Synatic will list everything in the repository. You can also use it to search. If you want to use command line ```
aptitude search package_name
``` will work.

---

### Post by cindylivengood on 2008-04-21
awsome.  you guys rule!

---

### Post by cindylivengood on 2008-04-21
I am in the middle of installing mediawiki and it wants to change media to a disc I left at home.  How do I bypass the process of always putting in the disk?  Also, how do I stop the process I am in the middle of?  

Thank you!

---

### Post by ugm6hr on 2008-04-21
> **cindylivengood said:**
> I am in the middle of installing mediawiki and it wants to change media to a disc I left at home.  How do I bypass the process of always putting in the disk?  !

Remove the CD from your repo list (in Software sources).

---

### Post by akiratheoni on 2008-04-21
> **cindylivengood said:**
> I am in the middle of installing mediawiki and it wants to change media to a disc I left at home.  How do I bypass the process of always putting in the disk?  Also, how do I stop the process I am in the middle of?  

Thank you!

I'm not on Ubuntu right now so bear with me, the wording might be wrong.

Fire up the Synaptic Package Manager (System -> Administration -> Synaptic)
Type your password when it prompts you to.

Settings -> Repositories

Then uncheck the white box that says something about the Gutsy Gibbon CD-ROM.

I'm not sure what it says... like I said, I'm not using Ubuntu. But it should be similar to that.

---

### Post by cindylivengood on 2008-04-22
I have the mediawiki installed.  Now I need to know how to access and manage it.  If I can learn how to do a few of the basic stuff, I should be able to figure out more stuff.

I thought I ought to be able to use my firefox to open an html file or something.

Thank you!

---

### Post by cindylivengood on 2008-04-22
> **akiratheoni said:**
> I'm not on Ubuntu right now so bear with me, the wording might be wrong.

Fire up the Synaptic Package Manager (System -> Administration -> Synaptic)
Type your password when it prompts you to.

Settings -> Repositories

Then uncheck the white box that says something about the Gutsy Gibbon CD-ROM.

I'm not sure what it says... like I said, I'm not using Ubuntu. But it should be similar to that.

Thanks!  That fixed that problem.  Now if I can get started working on it :)

---

### Post by RealPSL on 2008-04-23
You probably want to review this material now that you are past the installation

[http://www.mediawiki.org/wiki/Manual:Config_script]("http://www.mediawiki.org/wiki/Manual:Config_script")

---

### Post by cindylivengood on 2008-04-24
I have to admit, I am getting quite overwhelmed with the various things I have to do to get the wiki going.  Quite frankly, I don't know where to start.  I have to do stuff with mysql, php and apache as well as the wiki program.  Unfortunately, I don't know which program to mess with first.  If I knew where to start and in what order, that might help.

I got the wiki program from Ubuntu, so it should be at least that far.

---

