---
title: "Installing deb files"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by Oki on 2007-01-15
Question 1:
Lets say I want to install a *.deb file. On the site where I downloaded the file, it stands that you also need two other package(dependencies). If I install those two, perhaps I found them in synaptic, can I then safely install the *.deb file? 

Question 2:
If "yes", then I don't understand why Dapper Drake only has (example) Firefox 1.5, while Edgy has Firefox 2.0. Couldn't I just download the deb file for Firefox 2.0 and install it when running Dapper? If "yes", why arnt they just adding FF 2.0 for apitude? Or it is somwhat risky cus different kernls?

Question 3:
Perhaps another dumb question; but why are some distros using rpm files, and others deb files. Wouldn't it be much better if they only used one? 

Two simple Kbuntu questions: 
Could you please tell me how to:
Witch keys to shift between the virtual desktops in Kbuntu(KDE)?
What is the program under Kubuntu that dos the same as Alacarte Menu Editor in Ubuntu. 

Thank you very much:-D

---

### Post by bodhi.zazen on 2007-01-15
> **Oki said:**
> Question 1:
Lets say I want to install a *.deb file. On the site where I downloaded the file, it stands that you also need two other package(dependencies). If I install those two, perhaps I found them in synaptic, can I then safely install the *.deb file? 

sudo dpkg -i name_of_package.deb

---

### Post by kane77 on 2007-01-15
> **Oki said:**
> Question 1:
Lets say I want to install a *.deb file. On the site where I downloaded the file, it stands that you also need two other package(dependencies). If I install those two, perhaps I found them in synaptic, can I then safely install the *.deb file? yes you can..

> **Oki said:**
> 
Question 2:
If "yes", then I don't understand why Dapper Drake only has (example) Firefox 1.5, while Edgy has Firefox 2.0. Couldn't I just download the deb file for Firefox 2.0 and install it when running Dapper? If "yes", why arnt they just adding FF 2.0 for apitude? Or it is somwhat risky cus different kernls?I've been wondering about the same thing... don't think it's a kernel issue.. and it happens that packages get backported... it only takes a bit more time...

> **Oki said:**
> Question 3:
Perhaps another dumb question; but why are some distros using rpm files, and others deb files. Wouldn't it be much better if they only used one? 
it's a problem that has to do something with the history of modern linux... there were Debian - .deb  and Redhat .rpm (and Slackware with no PM)... it would definitely be great if every linux distro would be binary compatible with each other... but because of great diversity it's impossible... not even debian and ubuntu are 100% binary compatible... you can get away with most of the packages but it's advised not to mix and match debian and ubuntu archives...

> **Oki said:**
> Two simple Kbuntu questions: 
Could you please tell me how to:
Witch keys to shift between the virtual desktops in Kbuntu(KDE)?
What is the program under Kubuntu that dos the same as Alacarte Menu Editor in Ubuntu. 

Thank you very much:-DI don't use kde so I'll leave those questions for others :D (doesnt the ctrl+alt+arrows work for switching desktops?)

---

### Post by K.Mandla on 2007-01-15
> **Oki said:**
> Question 1:
Lets say I want to install a *.deb file. On the site where I downloaded the file, it stands that you also need two other package(dependencies). If I install those two, perhaps I found them in synaptic, can I then safely install the *.deb file? 
Yes, so long as safely means "without error." If you're talking about the safety of the original .deb file, then that will depend on how "safe" that package is for your machine.

> **Oki said:**
> Question 2:
If "yes", then I don't understand why Dapper Drake only has (example) Firefox 1.5, while Edgy has Firefox 2.0. Couldn't I just download the deb file for Firefox 2.0 and install it when running Dapper? If "yes", why arnt they just adding FF 2.0 for apitude? Or it is somwhat risky cus different kernls?
Possibly, but that will depend on what dependencies FF2.0 has, and if the versions of those packages are met under Dapper. If Dapper's versions are too early, then FF2.0 might not install. 

> **Oki said:**
> Question 3:
Perhaps another dumb question; but why are some distros using rpm files, and others deb files. Wouldn't it be much better if they only used one? Everybody's got their own way of doing things! :rolleyes: #-o 

> **Oki said:**
> Thank you very much:-D
You're welcome very much! :D

---

### Post by peabody on 2007-01-15
> **Oki said:**
> Question 1:
Lets say I want to install a *.deb file. On the site where I downloaded the file, it stands that you also need two other package(dependencies). If I install those two, perhaps I found them in synaptic, can I then safely install the *.deb file?


Typically yes, provided the package maintainer has done their homework correctly and has properly listed dependencies.

> 
Question 2:
If "yes", then I don't understand why Dapper Drake only has (example) Firefox 1.5, while Edgy has Firefox 2.0. Couldn't I just download the deb file for Firefox 2.0 and install it when running Dapper? If "yes", why arnt they just adding FF 2.0 for apitude? Or it is somwhat risky cus different kernls?


A short answer?  Depedencies cascade.  Not always, but it could be that running firefox 2.0 requires library X to go from version 1 to version 2, which would be fine but this breaks compatibility with program Y.  Backports is a project that specifically deals with these sorts of problems.

> 
Question 3:
Perhaps another dumb question; but why are some distros using rpm files, and others deb files. Wouldn't it be much better if they only used one? 


It'd be nice but the two formats are around for historical reasons and there will probably never be a consalidation of the two formats.  They both have their strengths and weaknesses.  Now package management in general...there's a project called smart which acts as a front end to all the packages and dependencies out there which is aiming to fix the problem for the end user and I've heard great things about it, but have not used it myself.

> 
Two simple Kbuntu questions: 
Could you please tell me how to:
Witch keys to shift between the virtual desktops in Kbuntu(KDE)?
What is the program under Kubuntu that dos the same as Alacarte Menu Editor in Ubuntu. 


Sorry, haven't used KDE in a blue moon, hopefully someone else can chime in.
> 
Thank you very much:-D

You're welcome.

---

### Post by Oki on 2007-01-15
I googled for "Smart" and found:

Mark S.; "We want to focus the collective brainpower of the community on features and bugs, not on packaging. "http://www.markshuttleworth.com/archives/66

And here is the homepage for smart; [http://labix.org/smart](http://labix.org/smart) 

Sounds interesting :-) 

Thanks again all!

---

