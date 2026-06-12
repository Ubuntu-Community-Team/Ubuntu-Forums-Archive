---
title: "Installing Java"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by GLSmyth on 2007-06-28
A website i would like to use required Java, which apparently needs to be manually installed.   I looked in Synaptic and it selected 134 packages. Some of them are already installed but I'm not sure which one to select. In looking at the descriptions it looks like bsh should be the right one, but it is already installed. Do I just start installing packages until the program I am running works? Is there a rule of thumb for doing this?

I looked at the link to the starting guide and, as mentioned in a response, tried entering:
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

Unfortunately, the response I got was:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package sun-java6-jre

I am guessing that I need to install something before running that command but am not sure what that might be. I tried looking for sun-java6-jre in Synaptic without any luck.

Cheers -

george

---

### Post by cogadh on 2007-06-28
Click on Applications > Add/Remove, select "All available...", then search for "Ubuntu restricted extras", install it, and you will have Java.

---

### Post by p_quarles on 2007-06-28
cogadh's solution will definitely work.

If you want to install JRE (and much more!) from synaptic, though, you need to go to System >> Administration >> Software Sources and enable the multiverse repositories.

---

### Post by Nyxess on 2007-06-28
i couldnt figure out how to install java last night, but someone pointed me to a program called Automatix. It gives you a list of programs/drivers/utilities/plug-ins and all that fun stuff you can get. 

[http://www.getautomatix.com/](http://www.getautomatix.com/)

its really easy to install java from this program, if you still couldnt figure it out =)

---

### Post by GLSmyth on 2007-07-01
> **cogadh said:**
> Click on Applications > Add/Remove, select "All available...", then search for "Ubuntu restricted extras", install it, and you will have Java.

When I click on Applications - Add/Remove, I see the tab appear at the bottom, but then nothing else happens.  I assume that I should see a window open, but this is not happening.  Is these something else I need to do to get this application open?

Cheers -

george

---

### Post by GLSmyth on 2007-07-01
> **p_quarles said:**
> cogadh's solution will definitely work.

If you want to install JRE (and much more!) from synaptic, though, you need to go to System >> Administration >> Software Sources and enable the multiverse repositories.

When I go there I do not see an option titled, "Enable Multiverse Repositories."  Is it labeled something different or should I be looking elsewhere?

Cheers -

george

---

### Post by GLSmyth on 2007-07-01
> **Nyxess said:**
> i couldnt figure out how to install java last night, but someone pointed me to a program called Automatix. It gives you a list of programs/drivers/utilities/plug-ins and all that fun stuff you can get. 

[http://www.getautomatix.com/](http://www.getautomatix.com/)

its really easy to install java from this program, if you still couldnt figure it out =)

I installed the package, but when I click on it, it doesn't open in a window (I'm assuming that it is supposed to).  Is there something else I need to do to get the program to run?

Cheers -

george

---

### Post by cogadh on 2007-07-01
> **GLSmyth said:**
> When I click on Applications - Add/Remove, I see the tab appear at the bottom, but then nothing else happens.  I assume that I should see a window open, but this is not happening.  Is these something else I need to do to get this application open?

Cheers -

george
No, you just need to wait for the app to load. When you launch it, it will scan for installed and available apps. The first time you do that, it could take a while.

---

### Post by GLSmyth on 2007-07-01
> **cogadh said:**
> No, you just need to wait for the app to load. When you launch it, it will scan for installed and available apps. The first time you do that, it could take a while.

Well, it's been more than two hours since I clicked on Add/Remove and still nothing, so I assume that the program does not work. Is there anything I should do to try to get it working or am I just out of luck?

Cheers -

george

---

### Post by cogadh on 2007-07-01
Honestly, I don't know. That's one of the Ubuntu apps that has always "just worked" for me. It uses the same functions as Synaptic, does that work for you?

---

### Post by upintilldawn on 2007-07-02
all i know is i am having the same problem. I have installed java from [www.java.com](www.java.com) and i have done every thing there web site told me to do to install it to work with the browser yet it does not work for me too. i have also once installed the java from the program install program. i could see some of the java stuff but could not selcet or open any of the pages. it would shut down the browser if i tried to use the java site.

---

### Post by RomeReactor on 2007-07-02
Hi. **GLSmyth**, if you're running Feisty (Ubuntu 7.04), then open Synaptic, go to "Settings->Repositories" and on the first tab (Ubuntu Software) make sure all the cases are checked; then press the blue **Reload** button (just below "Edit" in Synaptic). After it finishes reloading the package information, search for **sun-java6** and install **sun-java6-bin, sun-java6-fonts, sun-java6-jre** and **sun-java6-plugin**. Or to install from the terminal:
```
sudo apt-get install sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
```
**upintilldawn**, if you already have java installed, try opening Firefox from the terminal:
```
firefox
```
and go to the site that's giving you trouble; if Firefox crashes, it will most likely leave messages on the terminal as to what went wrong. Sometimes that information is very useful in determining what the problem is.

---

### Post by paradoc on 2007-07-02
Another Hi, **GLSmyth** 
Launch Add/Remove (from Applications)
Enter restricted in the search bar, choose 'All available applications', with 'All' highlighted, (top of left hand menu), if no tick on 'Ubuntu restricted extras', you will be downloading Java 6 runtime, Flash 9 player, and a few popular MS fonts, when you click on APPLY.  

If APPLY is greyed out, it means you already have it installed, and 'OK' simply removes the app window leaving you possibly wondering why it didn't work!

If it was simply a faulty install or a corruption, 'Add/remove', by definition, will also remove these restricted apps (untick->Apply), and it might be worth your while to reinstall, as above.

Good Ubunting!

---

### Post by Computer-Geek on 2007-07-02
Try easyubuntu to install FLASH, JAVA and some other apps.

---

### Post by upintilldawn on 2007-07-03
> **RomeReactor said:**
> Hi. **GLSmyth**, if you're running Feisty (Ubuntu 7.04), then open Synaptic, go to "Settings->Repositories" and on the first tab (Ubuntu Software) make sure all the cases are checked; then press the blue **Reload** button (just below "Edit" in Synaptic). After it finishes reloading the package information, search for **sun-java6** and install **sun-java6-bin, sun-java6-fonts, sun-java6-jre** and **sun-java6-plugin**. Or to install from the terminal:
```
sudo apt-get install sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
```
**upintilldawn**, if you already have java installed, try opening Firefox from the terminal:
```
firefox
```
and go to the site that's giving you trouble; if Firefox crashes, it will most likely leave messages on the terminal as to what went wrong. Sometimes that information is very useful in determining what the problem is.

i tperson... ryed the sudo code did not work fore me i got this..

Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-bin is already the newest version.
sun-java6-bin set to manual installed.
sun-java6-jre is already the newest version.
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

now i installed java once withautomatix and that did not work too.

---

### Post by RomeReactor on 2007-07-03
**upintilldawn**, **sun-java6-plugin** is in **multiverse** repositories; you must first enable them (see my previous post) and then reload the package information either through Synaptic or from the command line:
```
sudo apt-get update
```
All the other packages are installed, though it seems that **sun-java6-bin** came from somewhere else.

---

### Post by ellgor on 2007-07-04
Hi.

Have found that the java application that you need is the j2re1.4(blackdown edition) which will be listed in the synaptic package manager (all repositries being enabled, click on the add button to show the extended list). There are 2 packages together, the one already mentioned and a mozilla plugin, load both. They load automatically and you will get a licence pop-up to which you will agree to ( this tells you things are going well ) these applications don't load every pop-up  etc but they do load the main applets at the site you are on, which I suspect is what you are after, hope this helps.

Regards, Ellgor.

---

### Post by GLSmyth on 2007-07-04
> **cogadh said:**
> Honestly, I don't know. That's one of the Ubuntu apps that has always "just worked" for me. It uses the same functions as Synaptic, does that work for you?

Yes, I think that Synaptic works - at least, it comes up in a window.  Then again, I was also told to Enable Multiverse Repositories within Synaptic and I do not see that option anywhere.

Cheers -

george

---

### Post by GLSmyth on 2007-07-04
> **ellgor said:**
> Hi.

Have found that the java application that you need is the j2re1.4(blackdown edition) which will be listed in the synaptic package manager (all repositries being enabled, click on the add button to show the extended list). There are 2 packages together, the one already mentioned and a mozilla plugin, load both. They load automatically and you will get a licence pop-up to which you will agree to ( this tells you things are going well ) these applications don't load every pop-up  etc but they do load the main applets at the site you are on, which I suspect is what you are after, hope this helps.

Regards, Ellgor.

I do not see j2rel.4 anywhere so I am assuming that it is in the multiverse repository (I have no idea what that means).  I was told that to enable it I need to enable multiverse repositories, but in Synaptic above "Source Code" (where I was told the option resides) I have "Proprietary devices for devices (restricted)," so perhaps this option is not available to me? I am using Ubuntu 6.10.

Cheers -

george

---

### Post by RomeReactor on 2007-07-04
**GLSmyth**, in "Synaptic->Settings->Repositories" did you check the other tabs to see if the option to enable the other repositories is there? I don't quite remember if there is a significant difference in Synaptic between Edgy and Feisty. Also, the packages that **ellgor** mentions start with **j2re1.4** (that's j2re **one-point-four**); look for them in Synaptic as **j2re**. They both should appear. This is the [Ubuntu documentation page]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html") explaining what repositories are and how to enable them. If they don't show up, another way to enable the repositories is using this [guide]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_apt-get_the_easy_way_.28Synaptic.29") (it also has a ton of useful information that can help you with other problems). If you're having trouble with using Synaptic to enable the repositories, you can also do it by opening the sources file (which contains the repositories) in Gedit, the text editor:
```
gksudo gedit /etc/apt/sources.list
```
and using [this part of the guide]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_add_extra_repositories").

---

### Post by Eggnog on 2007-07-07
Cogadh's method of installing through Applications -> Add/Remove -> Ubuntu Restricted Extras worked perfectly for me.  I love the great things I can learn around here.  If you don't want to do a search, it's near the bottom of the Others category.

---

