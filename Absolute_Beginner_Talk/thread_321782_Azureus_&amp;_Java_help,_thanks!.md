---
title: "Azureus &amp; Java help, thanks!"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by dmber on 2006-12-19
I'm getting this error that i haven't gotten before with Azureus:

"Tracker status: Error (You are using java 1.4.2, which is not compatible with your Azureus. Please Fix it.)"

I installed JRE from Add/Remove.  I really don't know what else to do.  

Thanks!

---

### Post by steve.horsley on 2006-12-19
Try installing sun-java5-jre package from the multiverse/universe repositories.

---

### Post by dmber on 2006-12-19
yes, thank you for the prompt response.

unfortunately, i have no idea what that means.

when i'm looking to see how to do things on howto:'s i see stuff about repositories a lot.  what does that mean?  how do i do that?

---

### Post by jvc26 on 2006-12-19
Basically a repository is an online store of data which your install can connect to (with an address from a file in /etc/apt/sources.list) and then download things from there to install with the sudo apt-get install command from terminal. Steves post means you need to install the sun-java5-jre package (the thing which enables you to use Java apps of more updated java than 1.4) from the multiverse repos which is not enabled by default. Therefore you need:

First go to:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)
to add extra repos.

Then go to automatix (which I believe has the option to install most of the Java stuff) nice and simple and does things automatically, some love it some hate it but it seems to do the trick!
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu)

Alternatively if you want to install all the java stuff yourself from the repos:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu)
JRE 5 update 10:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_JRE_v5.0_Update_10](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_JRE_v5.0_Update_10)

There is a slightly more complex method to get the very latest version of java (1.6) here but this is for the SDK (the development kit for java) but with the SDK comes the run time environment which is what your azureus is complaining about not having again this is more complex so unless you are particularly desparate for the new version stick to either the automatix route or go to the route by installing the stuff yourself heres the link anyway:
[http://www.ubuntuforums.org/showpost.php?p=1877195&postcount=15](http://www.ubuntuforums.org/showpost.php?p=1877195&postcount=15)

Hope that helps :)
Il

---

