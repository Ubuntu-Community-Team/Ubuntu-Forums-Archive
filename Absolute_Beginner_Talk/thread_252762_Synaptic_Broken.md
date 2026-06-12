---
title: "Synaptic Broken"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-09-07
My Synaptic is broken.

This happend after I removed Openoffice manually from Synaptic.

For an example if I try to apt-get something I get this error.

> aktiwers@HAL:~$ sudo apt-get install supertux
Password:
Reading package lists... Done
Building dependency tree... Done
E: The package openoffice.org-core05u needs to be reinstalled, but I can't find an archive for it.
aktiwers@HAL:~$

This error shows up what ever I try to do with apt-get or aptitude. 

I also did a "sudo aptitude upgrade" and "sudo apt-get upgrade" and also "sudo aptitude update" and "sudo apt-get update"

But that gives me this error:
> 
aktiwers@HAL:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be upgraded:
  compiz-core compiz-plugins csm imagemagick libmagick9 libmysqlclient15off
  libssl0.9.8 libxfont1 mysql-common openssl
10 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 391kB will be used.
Do you want to continue? [Y/n/?] y
E: I wasn't able to locate a file for the openoffice.org-core05u package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?
aktiwers@HAL:~$

and the sudo apt-get update goes well.

I cant even upen Synaptic. It just opens and closes again right after.

I really appriciate any help, as my computer was running perfect before this, and I would really hate to reinstall.

Thanks!

---

### Post by wieman01 on 2006-09-07
A useful link:

[http://www.ubuntuforums.org/showthread.php?t=186672]("http://www.ubuntuforums.org/showthread.php?t=186672")

---

### Post by aktiwers on 2006-09-08
Thanks Wieman01, but did you read my post currectly? 
I cant find anything in there, that could help me?

As I said, I removed openoffice manually from Synaptic, and after that it gives me all the errors posted above.

Does anyone have any idea what to do?

---

### Post by catlett on 2006-09-08
Hi Atkiwers,

This is a 'theory' idea. I do not know for certain if it will work but try
```
sudo dpkg --force-remove-reinstreq openoffice.org-core05u
```This is the reqasoning behind the command. This is a snippet from the dpkg man page
```
 remove-reinstreq: Remove a package, even if  it’s  broken
              and  marked  to  require  reinstallation.   This may, for
              example, cause parts of the package to remain on the sys&#8208;
              tem, which will then be forgotten by dpkg.
```
as well as the entire command prefix listed above

```
       reinst-required
              A package marked reinst-required is broken  and  requires  rein&#8208;
              stallation. These packages cannot be removed, unless forced with
              option [COLOR="Red"]--force-remove-reinstreq[/COLOR].
```Good luck. I'm off to work.

regards, catlett

---

### Post by aktiwers on 2006-09-08
Thanks Catlett.

When I use the command it gives me this:
> 
aktiwers@HAL:~$ sudo dpkg --force-remove-reinstreq openoffice.org-core05u
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
aktiwers@HAL:~$

Is something missing in the command?

---

### Post by wieman01 on 2006-09-08
Well... not sure if this one helps. I am using a tool called **"gtkorphan"** to remove broken packages & resolve broken dependencies. You find it in the repositories and may give it a try. Great tool!

---

### Post by aktiwers on 2006-09-08
> **wieman01 said:**
> Well... not sure if this one helps. I am using a tool called **"gtkorphan"** to remove broken packages & resolve broken dependencies. You find it in the repositories and may give it a try. Great tool!

But my Synaptic is broken, and so is apt-get. I cant apt-get or aptitude anything. I keep getting this error.

Anyone know why my try in the above post, ended wrong?

---

### Post by wieman01 on 2006-09-08
Alright, I got it. You can download the Debian package for gtkorphan from here:

[http://ftp.debian.org/debian/pool/main/g/gtkorphan/gtkorphan_0.4.1-1_all.deb]("http://ftp.debian.org/debian/pool/main/g/gtkorphan/gtkorphan_0.4.1-1_all.deb")

Currently the Debian server is down, so I cannot attach it here. If this tool does not work I am at my wit's end.

---

### Post by jimbren on 2006-09-08
I had a similar issue a long time back, and I was able to fix it fairly easily.

Here's what I did.
```
sudo apt-get clean
```
This cleans out your repository list...not sure if it is absolutely necessary, but that's what I did.

After that, I did this:
```
sudo apt-get update
```
followed by:
```
sudo apt-get -f install
```

---

### Post by wieman01 on 2006-09-08
I found the Debian file for "gtkorphan". Simply unzip it and install it. It's worth a try.

---

### Post by aktiwers on 2006-09-08
> **wieman01 said:**
> I found the Debian file for "gtkorphan". Simply unzip it and install it. It's worth a try.

Thanks all for your replys.

Jimbren:
I tryid what you said. And all goes fine untill.

> aktiwers@HAL:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
E: The package openoffice.org-core05u needs to be reinstalled, but I can't find an archive for it.
aktiwers@HAL:~$

Wieman01:
Thanks a lot for the zip. Sorry for being ignorant, but after installing, where can I open the program? It does not show up in my menu, and dont open when I type  in terminal.

> aktiwers@HAL:~$ gtkorphan
bash: gtkorphan: command not found
aktiwers@HAL:~$ gtkorphan
bash: gtkorphan: command not found
aktiwers@HAL:~$ gtkorphan_0.4.1-1
bash: gtkorphan_0.4.1-1: command not found
aktiwers@HAL:~$ GtkOrphan
bash: GtkOrphan: command not found
aktiwers@HAL:~$

---

### Post by catlett on 2006-09-08
Hi Atkiwers,
I do not know if you are still trying to install gtkorphan but I unzipped and uplopaded it for you. Just hit the link and it will take you to the file sharing site. Then download. You should get an option to open and install it with g-debi package installer.
[http://www.gigasize.com/get.php/45136/gtkorphan_0.4.1-1_all.deb](http://www.gigasize.com/get.php/45136/gtkorphan_0.4.1-1_all.deb)

---

### Post by wieman01 on 2006-09-08
Excellent, Catlett. They would not let me upload *.deb files here, that's why I had to zip it.

Aktiwers, let us know if you have a problem installing the *.deb file. But this not be a problem I guess... 
> sudo dpkg -i <file name>
Hope this works out.

---

### Post by catlett on 2006-09-08
> **wieman01 said:**
> Excellent, Catlett. They would not let me upload *.deb files here, that's why I had to zip it.

Aktiwers, let us know if you have a problem installing the *.deb file. But this not be a problem I guess... 

Hope this works out.

By the way, thanks for linking to gtkorphan. I never heard of it before. I installed and ran it. I was surprised when I had 5 orphaned packages. Anyways, great program. Thanks for posting it.

---

### Post by wieman01 on 2006-09-08
> **catlett said:**
> By the way, thanks for linking to gtkorphan. I never heard of it before. I installed and ran it. I was surprised when I had 5 orphaned packages. Anyways, great program. Thanks for posting it.

No problem. Learned about it only a short while ago myself. That's the way it goes in this forum I guess. :-)

---

### Post by aktiwers on 2006-09-09
Thanks guys. 
I first installed it with "double click" and that finsihed without errors. However, I can not find the program anywere. So I tryid to install it again through Terminal and this is what happends.
> 
aktiwers@HAL:~$ sudo dpkg -i /home/aktiwers/Desktop/gtkorphan_0.4.1-1_all.deb
Password:
Selecting previously deselected package gtkorphan.
(Reading database ...
dpkg: serious warning: files list file for package `openoffice.org-core05u' missing, assuming package has no files currently installed.
166043 files and directories currently installed.)
Unpacking gtkorphan (from .../gtkorphan_0.4.1-1_all.deb) ...
dpkg: dependency problems prevent configuration of gtkorphan:
 gtkorphan depends on deborphan (>= 1.7.17); however:
  Package deborphan is not installed.
dpkg: error processing gtkorphan (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gtkorphan
aktiwers@HAL:~$ sudo apt-get install deborphan
Reading package lists... Done
Building dependency tree... Done
E: The package openoffice.org-core05u needs to be reinstalled, but I can't find an archive for it.
aktiwers@HAL:~$

Grrrr...  

Any ideas? :)

---

### Post by wieman01 on 2006-09-09
Ok, this is a real odd case...

Have you tried downloading the OpenOffice Deb-file and reinstalling it? Perhaps that eventually resolves the broken dependencies. Just a thought.

---

### Post by aktiwers on 2006-09-09
> **wieman01 said:**
> Ok, this is a real odd case...

Have you tried downloading the OpenOffice Deb-file and reinstalling it? Perhaps that eventually resolves the broken dependencies. Just a thought.

Yes I have tried that too. Acctually I made another post about this problem, but nobody seamed to be able to help.
[http://www.ubuntuforums.org/showthread.php?t=251335](http://www.ubuntuforums.org/showthread.php?t=251335)

Look at the screenshot, what happends when I try to install a deb from Openoffice.

---

### Post by aktiwers on 2006-09-09
Okey I downloaded  deborphan manually and installed it.
Now gtkorphan works. 

However, openoffice does not show up on the list?
I guess this wont help me then or?

What should I do?

---

### Post by aktiwers on 2006-09-10
Bumb

---

### Post by basilwatson on 2006-09-10
No its not your end its the server, I did a re install and I cannot load anything either with the terminal or synaptic

I have just triede a fresh reinstall AGAIN ,,and Bumps crashes 1/2 way through 

SOOOO I reckon that its the server ..imho

Stephen

---

### Post by wieman01 on 2006-09-10
> **aktiwers said:**
> Okey I downloaded  deborphan manually and installed it.
Now gtkorphan works. 

However, openoffice does not show up on the list?
I guess this wont help me then or?

What should I do?

Sorry, I have not seen your post until now. I attached a screenshot of my GTKOrphan. Basically what you should do is check the option **"Show all orphan packages, not only those in the libs section"** (left lower corner) on the **"Orphaned packages"** tab, then search for **"openoffice.org"**, right-click, and finally select **"Select for removal"**.

Can you try?

---

### Post by wieman01 on 2006-09-10
> **basilwatson said:**
> No its not your end its the server, I did a re install and I cannot load anything either with the terminal or synaptic

I have just triede a fresh reinstall AGAIN ,,and Bumps crashes 1/2 way through 

SOOOO I reckon that its the server ..imho

Stephen

I don't think so...

---

### Post by basilwatson on 2006-09-10
worked yesteday nite, I installed fresh ..(this laptop is the test rig)... same computer, disk ..2 fresh installstoday ,, and no synaptic???

Have I worn out the cd??

Stephen
I can install from anysite such as firefox, but anything else cant find package

---

### Post by wieman01 on 2006-09-10
> **basilwatson said:**
> worked yesteday nite, I installed fresh ..(this laptop is the test rig)... same computer, disk ..2 fresh installstoday ,, and no synaptic???

Have I worn out the cd??

Stephen
I can install from anysite such as firefox, but anything else cant find package

Are you or am I on the wrong page?

---

### Post by basilwatson on 2006-09-10
Dont know , what i do know is that my Synaptic isnt working, and there are a few others with the same problem posting  now 
Seems a bit odd thats all 

stephen

---

### Post by aktiwers on 2006-09-10
Wieman01 I just removed anything from the list that had something to do with Openoffice. Sadly this didnt fix the problem. When I try to sudo apt-get install a random thing, the same problem shows up:
> 
aktiwers@HAL:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
E: The package openoffice.org-core05u needs to be reinstalled, but I can't find an archive for it.
aktiwers@HAL:~$ 
or 
> 
aktiwers@HAL:~$ sudo apt-get install supertux
Reading package lists... Done
Building dependency tree... Done
E: The package openoffice.org-core05u needs to be reinstalled, but I can't find an archive for it.
aktiwers@HAL:~$
Damn this is killing me. :)
What can be wrong here? And how can one package brake up the whole synaptic?

---

### Post by wieman01 on 2006-09-10
My VERY last idea. ;-) Just another thought.

Apparently "aptitude" is looking for the debian package of open-office but cannot find it. What happens if you place the exact same package (if necessary rename the package file of open-office so that it matches the requested on2) in this folder: **var/cache/apt/archives/**

Aptitude should then be able to find when you run it and perhaps resolve the broken dependencies. You get what I mean?

---

### Post by aktiwers on 2006-09-10
> **wieman01 said:**
> My VERY last idea. ;-) Just another thought.

Apparently "aptitude" is looking for the debian package of open-office but cannot find it. What happens if you place the exact same package (if necessary rename the package file of open-office so that it matches the requested on2) in this folder: **var/cache/apt/archives/**

Aptitude should then be able to find when you run it and perhaps resolve the broken dependencies. You get what I mean?

Yes I get what you mean. Are you sure the location is currect? In my **var/cache/apt/archives/ **there is no files (wich I for some reason expected). But anyways, I tried what you said, but without luck :(

View Screenshot below.

---

### Post by wieman01 on 2006-09-10
> **aktiwers said:**
> Yes I get what you mean. Are you sure the location is currect? In my **var/cache/apt/archives/ **there is no files (wich I for some reason expected). But anyways, I tried what you said, but without luck :(

View Screenshot below.

Damnit... Yes, the location is definitely correct (mine contains all debian archives that I had installed at some point). Now the last thing we could try is to put all open-office related files that there are in the same directory/folder and see if "aptitude" recognizes them when updating. Perhaps renaming the files was the wrong suggestion.

Can you try again? The screenshot shows all the packages that Synaptic has installed on my PC.

Actually I am surprised your archive folder is empty. But anyway...

---

### Post by wieman01 on 2006-09-10
Also... Can you search your computer for debian files? Perhaps your version stores the archives somewhere else??? Would be strange thought, but it's worth a shot. Then apply the same procedure.

---

### Post by wieman01 on 2006-09-10
Hey Aktiwers, 

Interesting stuff here as well. Found it a minute ago:

[http://ubuntuforums.org/showthread.php?t=253912&highlight=synaptic+broken]("http://ubuntuforums.org/showthread.php?t=253912&highlight=synaptic+broken")

If I cannot help, perhaps these guys can...

---

### Post by Ramses de Norre on 2006-09-10
Have you tried installing openoffice.org-core01 with dpkg and if that works the next packages untill openoffice.org-core05?

---

### Post by aktiwers on 2006-09-10
First thanks a lot for all the support, I really appriciate it.

Okey, I tryid installing the core01 but it says it depends on the other core packages. And the say the same. Have a look:
> 
aktiwers@HAL:~/Desktop/DEBS$ sudo dpkg -i /home/aktiwers/Desktop/DEBS/openoffice.org-core01_2.0.3-7_i386.deb
(Reading database ...
dpkg: serious warning: files list file for package `openoffice.org-core05u' missing, assuming package has no files currently installed.
149798 files and directories currently installed.)
Preparing to replace openoffice.org-core01 2.0.3-7 (using .../openoffice.org-core01_2.0.3-7_i386.deb) ...
Unpacking replacement openoffice.org-core01 ...
dpkg: dependency problems prevent configuration of openoffice.org-core01:
 openoffice.org-core01 depends on openoffice.org-core02; however:
  Package openoffice.org-core02 is not installed.
 openoffice.org-core01 depends on openoffice.org-core03; however:
  Package openoffice.org-core03 is not installed.
 openoffice.org-core01 depends on openoffice.org-core04; however:
  Package openoffice.org-core04 is not installed.
 openoffice.org-core01 depends on openoffice.org-core05; however:
  Package openoffice.org-core05 is not installed.
 openoffice.org-core01 depends on openoffice.org-core06; however:
  Package openoffice.org-core06 is not installed.
 openoffice.org-core01 depends on openoffice.org-core07; however:
  Package openoffice.org-core07 is not installed.
 openoffice.org-core01 depends on openoffice.org-core08; however:
  Package openoffice.org-core08 is not installed.
dpkg: error processing openoffice.org-core01 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openoffice.org-core01
aktiwers@HAL:~/Desktop/DEBS$ sudo dpkg -i /home/aktiwers/Desktop/DEBS/openoffice.org-core08_2.0.3-7_i386.deb
Selecting previously deselected package openoffice.org-core08.
(Reading database ...
dpkg: serious warning: files list file for package `openoffice.org-core05u' missing, assuming package has no files currently installed.
149798 files and directories currently installed.)
Unpacking openoffice.org-core08 (from .../openoffice.org-core08_2.0.3-7_i386.deb) ...
dpkg: dependency problems prevent configuration of openoffice.org-core08:
 openoffice.org-core08 depends on openoffice.org-core01; however:
  Package openoffice.org-core01 is not configured yet.
dpkg: error processing openoffice.org-core08 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openoffice.org-core08
aktiwers@HAL:~/Desktop/DEBS$ 
??

EDIT:
Also Wieman01, I searched for .deb files and all that turned up, was all the .debs I manually downloaded from Openoffice.

---

### Post by catlett on 2006-09-10
Just for the heck of it, have you been trying aptitude as well as apt-get. Aptitude has solved alot of my dependencies and broken packages. If you only used apt-get try
```
sudo aptitude update
``` 
```
sudo aptitude upgrade
```
Also just type ```
aptitude 
```it brings up a graphical front end in the terminal kind of like nano with text documents. It has alot of powerful features although I am not very comfortable with them. When I firstr installed a debian system and I was using aptitude this way I uninstalled my entire system without reakising it.:D 
Also ```
dselect
``` has the same type of thing. Hopefully one of them will do something

---

### Post by aktiwers on 2006-09-12
> **catlett said:**
> Just for the heck of it, have you been trying aptitude as well as apt-get. Aptitude has solved alot of my dependencies and broken packages. If you only used apt-get try
```
sudo aptitude update
``` 
```
sudo aptitude upgrade
``` Also just type ```
aptitude 
```it brings up a graphical front end in the terminal kind of like nano with text documents. It has alot of powerful features although I am not very comfortable with them. When I firstr installed a debian system and I was using aptitude this way I uninstalled my entire system without reakising it.:D 
Also ```
dselect
``` has the same type of thing. Hopefully one of them will do something

I have been messing around with this now, the past 2 days. It seams like I always get back to the same error. The one about the Openoffice-core05 thing..  

Hmm I guess I will have to reinstall to fix this?

---

### Post by wieman01 on 2006-09-12
Sorry to hear this is such a hassle. But I have run out of ideas... Honestly.

---

### Post by catlett on 2006-09-13
Hi Aktiwers,
I don't know if you just reinstalled or if you are still trying. I was in another post and someone offered a command for removal that was similar to the earlier command I offered but it was a little different. Maybe the new wording will help. Anyways, here is the new way I found to enter the reinstall required command
```
sudo dpkg --remove --force-remove-reinstreq openoffice.org-core05u
```I do not know if it will make a difference buit I figured I would post it.

---

### Post by aktiwers on 2006-09-15
> **catlett said:**
> Hi Aktiwers,
I don't know if you just reinstalled or if you are still trying. I was in another post and someone offered a command for removal that was similar to the earlier command I offered but it was a little different. Maybe the new wording will help. Anyways, here is the new way I found to enter the reinstall required command
```
sudo dpkg --remove --force-remove-reinstreq openoffice.org-core05u
```I do not know if it will make a difference buit I figured I would post it.

Thanks catlett.
Your right, I didnt give up yet. I just cant get myself to reinstall. Everything is running great, exept of this (huge) problem.

I tryid what you said, this is what it says:

> aktiwers@HAL:~$ sudo dpkg --remove --force-remove-reinstreq openoffice.org-core05u
Password:
dpkg - warning: ignoring request to remove openoffice.org-core05u which isn't installed.
aktiwers@HAL:~$ 

](*,)

---

### Post by aktiwers on 2006-09-15
The Problem is SOLVED!
The sad thing is, I cant tell how?!?

All I did was a 
> 
sudo apt-get upgrade

which I have done a 10000 times before, with errors. This time, it starting installing all the updates I havent been able to install for weeks.  

Well now it all works great again! Thank god I didnt reinstall! :D

Thanks a lot guys for all the support, it was really helpful!
I really appriciate it!

---

### Post by wieman01 on 2006-09-15
Helpful and yet in vain... ;-) Although this thread should be marked "sticky". Lots of useful information in a nutshell.

---

### Post by catlett on 2006-09-15
> **aktiwers said:**
> The Problem is SOLVED!
The sad thing is, I cant tell how?!?

All I did was a 


which I have done a 10000 times before, with errors. This time, it starting installing all the updates I havent been able to install for weeks.  

Well now it all works great again! Thank god I didnt reinstall! :D

Thanks a lot guys for all the support, it was really helpful!
I really appriciate it!

Hey, take the win any way you can. Although it would be nice to know the actual remedy for the situation, let's not look a gift horse in the mouth.:D  Thanks for posting and letting us know how things turned out. Take care.

---

