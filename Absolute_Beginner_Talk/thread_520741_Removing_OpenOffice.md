---
title: "Removing OpenOffice"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by guguma on 2007-08-08
Can you tell me with detailed steps how to remove open office org without breaking any other thing. I am a newbie so please keep onto details. I want to keep the ubuntu-desktop but remove openoffice.org completely.

---

### Post by Inxsible on 2007-08-08
> **guguma said:**
> Can you tell me with detailed steps how to remove open office org without breaking any other thing. I am a newbie so please keep onto details. I want to [COLOR=Red]keep the ubuntu-desktop but remove openoffice.org completely.[/COLOR]

you can't !!

---

### Post by oilchangeguy on 2007-08-08
go to applications, add/remove. and you can remove it from there. locate what you don't want, un-check it, and click ok.

---

### Post by guguma on 2007-08-08
I can remove openoffice.org and ubuntu-desktop then I can install ubuntu desktop from synaptic can't I. I thought GNU\Linux was about doing what you want with your OS no matter what.

---

### Post by Inxsible on 2007-08-08
> **guguma said:**
> I can remove openoffice.org and ubuntu-desktop then I can install ubuntu desktop from synaptic can't I.

that will install openoffice again.

---

### Post by Inxsible on 2007-08-08
you can however, remove the shortcuts to openoffice and pretend that openoffice is not installed on your computer :)

---

### Post by Inxsible on 2007-08-08
> **guguma said:**
>  I thought GNU\Linux was about doing what you want with your OS no matter what.
Well, you have to take that with a grain of salt :)

why dont you get rid of ubuntu-desktop also ? its not a necessity. its a meta package that points to what other packages should be installed to give a new user all the basic software.

i have removed ubuntu-desktop too, because there were too many apps that i never used like Evolution and GAIM. I also removed openoffice that came with ubuntu because it had a few bugs in the impress so i removed it and installed a fresh copy from oo.org

---

### Post by guguma on 2007-08-08
add\remove does not let me do that. It says that other apps depend on openoffice to work so I should use the synaptic.

---

### Post by Outrunner on 2007-08-08
Don't worry about uninstalling ubuntu-desktop along with openoffice, it won't hurt your system.

---

### Post by vexorian on 2007-08-08
ubuntu-desktop is just a combo package, it means that it is something that got a bunchload of dependencies so you (re)install the whole default ubuntu by installing it.

You don't really need ubuntu-desktop after the installation finishes...

...
So what are you doing for office? Are you going to use Koffice, found out that crossover works well? Prefer light weight things like abiword, and the light weight calc software? Or you really don't need office software? Just curious...

---

### Post by guguma on 2007-08-08
I know that I have to take it with a grain of salt:). But what I am asking is a possible thing, maybe it comes with doing so many reinstallations, uninstallations etc. but I presume that it is doable.

Come on if I cannot remove openoffice without having the rest of the ubuntu-desktop it would be like you know XP with Internet Explorer and the thought makes me sick.

As an answer to the post above, I use abiword, and lightweight calc software. i really do not need much office software. I use LaTeX for writing, for taking notes gedit is fine.

---

### Post by oilchangeguy on 2007-08-08
have you read post #3?

---

### Post by guguma on 2007-08-08
Wow lightning fast replies!!!

Anyway OK I will remove openoffice with ubuntu desktop but HOW. I cannot use add\remove, and synaptic has so much entries about openoffice that I do not know which one deals with what. I am a newbie I told you, I am trying to discover and learn here. 

How will I remove OO and Ubuntu-Desktop. And do it in such a way that I will not have colossal problems due to my lack of knowledge.

Thanks

EDIT: AND I READ all the posts,  there are so many replies coming when I am just writing so there have been some complications. I am only a ''newbie'' not a stupid jerk who does not know how to read or listen.

---

### Post by Inxsible on 2007-08-08
```
sudo aptitude remove openoffice
``` that will tell you all the packages that you will need to remove and you have to accept a solution that is acceptable to you.

---

### Post by bwtranch on 2007-08-08
There are other versions of Linux that use just the CLI. Maybe you could try one of those:)

---

### Post by guguma on 2007-08-08
sudo aptitude remove openoffice only does this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find package "openoffice", and more than 40
packages contain "openoffice" in their name.
The following packages have been automatically kept back:
  beryl-core beryl-manager beryl-plugins beryl-plugins-data beryl-settings 
  beryl-settings-bindings libberyldecoration0 libberylsettings0 
  libemeraldengine0 
The following packages have been kept back:
  beryl emerald 
0 packages upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

---

### Post by Inxsible on 2007-08-08
try openoffice.org or openoffice.org-core

---

### Post by vexorian on 2007-08-08
```
sudo aptitue remove openoffice.org
```
or:

```
sudo apt remove openoffice.org-core
```

either should do it.

---

### Post by guguma on 2007-08-08
I have done as you have suggested and it worked well. 

Thanks for all the help.

---

### Post by Inxsible on 2007-08-08
> **guguma said:**
> I have done as you have suggested and it worked well. 

Thanks for all the help.Cool. Glad to help.Make sure you mark the thread as solved :)

---

### Post by poorbadger on 2008-02-17
For the archives...

1st entry should read...

```
sudo aptitude remove openoffice.org
``` (aptitude misspelled)

I ran this but was still able to launch OO - and I think it said it was going to free a couple hundred KB.

2nd entry should read...

```
sudo apt-get remove openoffice.org-core
``` (no "apt" command)

I just ran this (except w/ "purge" instead of "remove") and it freed up ~280MB

Thanks for the info!  Clarification is just for the next guy.

> **vexorian said:**
> ```
sudo aptitue remove openoffice.org
```
or:

```
sudo apt remove openoffice.org-core
```

either should do it.

---

### Post by Scut_Farkus on 2008-02-29
> **poorbadger said:**
> For the archives...

1st entry should read...

```
sudo aptitude remove openoffice.org
``` (aptitude misspelled)

I ran this but was still able to launch OO - and I think it said it was going to free a couple hundred KB.

2nd entry should read...

```
sudo apt-get remove openoffice.org-core
``` (no "apt" command)

I just ran this (except w/ "purge" instead of "remove") and it freed up ~280MB

Thanks for the info!  Clarification is just for the next guy.

Dude!
You saved me!  For some reason, when I installed Dapper, the OpenOffice app told me it couldn't run it because it didn't exist.  When I tried to upgrade I got all kinds of irritating dependency errors, so I was left with OO not running, but not being able to be upgraded, either.  I figured if I just got rid of it completely, and re-installing it would do the trick.  Since I'm new to all this, I wasn't sure how to do it.  Following your instructions worked perfectly and I appreciate the help!

---

