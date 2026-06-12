---
title: "Add Applications vs Synaptic Package Manager. The Differences?"
date: 2005-10-21
forum: Absolute Beginner Talk
---

### Post by Darrin on 2005-10-21
I installed an app through add applications, but removing it through that left files behind. I then had to uninstall it through Snaptic Package manager. 

What are the differences between the two? What is the proper way I should be installing and uninstalling applications? Im confused between the two. :confused:

---

### Post by Kyral on 2005-10-21
Welcome to the APT Frontend Chain.

You see, Add Applications is a Frontend (thing that is supposed to make using the previous thing easier) to Synaptic, which in turn is a frontend to the command line Aptitude, which in turn is a frontend to Apt-Get, which in turn is a frontend (of sorts) to dselect, which in turn is a frontend to dpkg, which can be considered a frontend to sourceballs.

Basically you are all good as long as you are installing them from Ubuntu Repositories :D

---

### Post by Darrin on 2005-10-21
It seems that it is easier to install using add application because everything is more organized into categories and easier to find. But uninstalling should be done in synaptic if you want all the traces to be removed. Is this correct?

---

### Post by Kyral on 2005-10-21
I honestly don't know. I use the command line apt-get :D

---

### Post by UbuWu on 2005-10-21
Add applications is the easiest way to install software, it lists only desktop programs and not libraries etc. which an end user usually doesn't care about. Installing a program using either one does the same thing. For removing programs, in synaptic it is possible to also remove all configuration files etc. that have been created by the program. The add applications program doesn't do this by default.

Also programs that are installed usually have dependencies (packages (libraries/other programs) that also need to be installed to run the program) which are left behind when a program is removed. It is possible to remove them using synaptic, but you need to know what to remove. There are some programs that automate this process (e.g. debfoster, deborphan). There is also work planned to have this done automatically in future ubuntu versions.

---

### Post by drummer on 2005-10-21
you can also search for packages in synaptic.. there are categories, there's just so many packages in them.

When you uninstalled through Add Applications, it probably did the equivalent of doing a 'Remove' in synaptic. This leaves config files behind and to get rid of these you need to do a 'remove completely', which purges the config files as well.

---

### Post by Darrin on 2005-10-21
[QUOTE=UbuWu] There are some programs that automate this process (e.g. debfoster, deborphan). There is also work planned to have this done automatically in future ubuntu versions.[/QUOTE]
That will be great when that gets released.

---

