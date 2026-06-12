---
title: "Automatix"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by GLSmyth on 2007-07-01
Quote:
Originally Posted by Nyxess View Post
i couldnt figure out how to install java last night, but someone pointed me to a program called Automatix. It gives you a list of programs/drivers/utilities/plug-ins and all that fun stuff you can get.

[http://www.getautomatix.com/](http://www.getautomatix.com/)

its really easy to install java from this program, if you still couldnt figure it out =)

---

I installed the package, but when I click on it, it doesn't open in a window (I'm assuming that it is supposed to). Is there something else I need to do to get the program to run?

Cheers -

george

---

### Post by HotShotDJ on 2007-07-01
I don't quite follow.  Why did you need to install Automatix to [get Java]("https://help.ubuntu.com/7.04/programming/C/java.html")? What are you clicking on that won't run?

---

### Post by wolfen69 on 2007-07-01
uninstall then reinstall.

---

### Post by starcraft.man on 2007-07-01
I won't comment on the Automatix bit, some users like it, I don't. Do what you most like. I do know you absolutely don't "need" Automatix to install Java.

Ubuntu has a perfectly functional GUI installer.

First off, you need to add software repositories. [This will explain how that can be done very quickly]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories"), its sources list works just fine.

Terminal can be found at Applications > Accessories > Terminal.

Then, after following all of those steps (please read carefully, if you don't understand ask and we will answer) then proceed to install Java.

Open up Synaptic (the package installer for Ubuntu, System > Administration > Synaptic Package Manager) then push search and type in "java".

A list of results will appear, the packages (scroll to find them) you want are: 

```
sun-java6-jre sun-java6-plugin sun-java6-fonts
```

If you want the plugin for firefox please search for this:

```
j2re1.4-mozilla-plugin 
```

[URL="http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_J2SE_Runtime_Environment_.28JRE.29_v6.0_with_Plug-in_for_Mozilla_Firefox"]
Link for how to install from terminal.[/URL]

Now to understand what you just did, I'll give a little explanation. Software is stored in repositories (in reality they are servers that are publicly usable by Ubuntu users). Keys are used to authenticate and secure the exchange, you added a key when you added medibuntu, if you add more sources later to the list you will also need keys (few repositories keep them in the open). Synaptic is a package manager (packages are how software is distributed in Ubuntu, unlike windows you don't need to get a CD with exes) and by adding the sources to the list you told it there are other servers it can pull packages from, then you search available packages for Java and added the ones you wanted. The terminal is also an option, it is another means, but does the same as synaptic.

[This site will give you instructions for installing. ]("http://ubuntuguide.org/wiki/Ubuntu:Feisty")[This one covers basics.]("http://www.psychocats.net/ubuntu/") [This one explains more terminal.]("http://www.linuxcommand.org/")

One foot note, doing the above will make Automatix inoperable (the replacing sources list). Reinstall Automatix to get that working again (wasn't working anyway), if you want it that is. I don't recommend to people, but its their machine and their choice.

If there are any questions, feel free to ask. :)

---

