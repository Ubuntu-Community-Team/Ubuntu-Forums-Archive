---
title: "How to make synaptic/apt working without Internet"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by cadcrazy on 2008-01-06
No apt-on-cd, no dpkg but i want to make the Synaptic/Apt working to install the .deb packages offline. can anyone plz help me how to enable it  on a system having no internet connection.

---

### Post by cyclingman on 2008-01-06
I don't know if this is what you mean, but in Synaptic, go to; Settings>Repositories, then tick the "CDrom..." box at the bottem.

---

### Post by thelatinist on 2008-01-06
The above is correct, but be aware that you will only be able to install the packages that are included on the CD.  There are *many* packages in the repositories that are not on the CD, including everything in the universe and multiverse repositories.  To get those there is nothing for it but to connect to the Internet.

---

### Post by cadcrazy on 2008-01-06
No this is for my friends pc. All packages are backed up and copied to /var/cache/apt/archives
but as you know i can't install them just by " sudo apt-get ------ " . This is because to enable synaptic/apt for first time you need to connect to inernet, update list, install some package. Then only we can get it working. 

But i want to know to make it work without connecting to internet. I m struggling to get some solution. Plz help

---

### Post by PeterJS on 2008-01-06
> **cadcrazy said:**
> No apt-on-cd, no dpkg but i want to make the Synaptic/Apt working to install the .deb packages offline. can anyone plz help me how to enable it  on a system having no internet connection.

That's really not possible. Apt needs a source of source of some sort. How is it supposed to install new software if it doesn't have some where to get it? Your options are pretty much online and CD/DVD, and if you rule both those out that really doesn't leave you much to work with.

I guess you could get a machine with lots of disk space to spare connect it to the net build an apt mirror (takes several gigabytes at least 6) and then use it a local mirror with out an internet connection. The problem with this approach is that it's frozen in time, you'll never get any updates newer than when you took the snapshot, and it requires having a spare machine to put the mirror on.

EDIT: I guess the apt cache is a viable option, why didn't I think of that. Now how to make it work...

---

### Post by mcduck on 2008-01-06
Apart from CD repositories apt-get (and Synaptic, as it is just a graphical frontend for apt-get) doesn't work without internet connection. It's not supposed to, as it's main purpose is to handle downloading and installing of packages from Internet repositories. Trying to make them work without Internet is kind of like trying to make Firefox browse the web without  having  Internet connection..

If you have downloaded the .deb packages yourself, you can install them either by just clicking them on your desktop, or using dpkg from command line:

"sudo dpkg -i program.deb" will install the package 'program.deb'

"sudo dpkg -i program1.deb program2.deb" will install both program1.deb and program2.deb at the same time.

"sudo dpkg -i *.deb" will install all .deb packages from the current directory. This comes handy when you have many packages, or packages that depend on each other.

So, instead of copying everything to /var/cache/apt/archives you should just put them to your home (or desktop) and then use dpkg to install them. Of course you could also run "sudo dpkg -i /var/cache/apt/archives/*.deb" but if there are other packages in the same place, or many versions of same package, this might take some time..

---

### Post by cadcrazy on 2008-01-06
As i said earlier i backed up all the packages from my pc and copied them to my friends pc (/var/cache/apt/archives). Now i want to install it by issuing say "sudo apt-get install vlc" not by dpkg command. The question is of not just installing the package but strictly by apt/synaptic.

I know its a bit difficult but don't say that is not possible.Nothing is impossible

---

### Post by PeterJS on 2008-01-06
Is there a reason you're so adamantly opposed to dkpg? and/or couldn't point nautilus at the apt cache and use gdebi to install them?

---

### Post by cadcrazy on 2008-01-06
The reason is that many say it isn't possible. I say why it is not possible. If you don't know that s the other thing.

---

### Post by PeterJS on 2008-01-06
Good enough reason. I think the piece that you're missing is the package listing that apt-get update retrieves/generates. This tells apt what versions are available, without this I don't think apt will know what version to try and get from the cache.

---

### Post by thelatinist on 2008-01-06
Use the tools that work for the job.  You're trying to use package managers that use repositories to install local files.

---

### Post by mcduck on 2008-01-06
> **cadcrazy said:**
> The reason is that many say it isn't possible. I say why it is not possible. If you don't know that s the other thing.
It's not possible because apt-get only works with repositories, and it needs to get a index file of available packages from the repository before it knows what packages you have available.

So you either need to connect to some Internet repository, or use apt-on-cd to create a CD repository.

Apt-get was made to work with repositories, not to install local packages, as there already is a tool for installing local packages (dpkg).

---

### Post by cadcrazy on 2008-01-06
But what the hell happen to apt/synaptic after i install one package from internet. Then if i copy my previously backed up packages to /var/cache/apt/archives and swich off my net connection, then it is able to recognise packages from the hell (/var/cache/apt/archives) and able to install them. 
That means some system setting is changed if i install one package from internet. And my question is can't i change that hell setting manually to do the same thing

---

### Post by thelatinist on 2008-01-06
> **cadcrazy said:**
> But what the hell happen to apt/synaptic after i install one package from internet. Then if i copy my previously backed up packages to /var/cache/apt/archives and swich off my net connection, then it is able to recognise packages from the hell (/var/cache/apt/archives) and able to install them. 
That means some system setting is changed if i install one package from internet. And my question is can't i change that hell setting manually to do the same thing

As was explained above, it's not a setting.  It's the repositories list.  When you connect to the internet, it downloads lists of files available in the repositories so it can install them.  When you later use apt-get, before downloading the files from the repositories it will check to see if there is an up-to-date local copy so it doesn't have to use internet resources.  This does not change the fact that the application is not intended to do what you are trying to do with it, and you are wasting your time and ours trying to figure out how to hammer a nail in with a screwdriver.

---

### Post by brianC on 2008-01-06
This page might help
[http://ubuntuforums.org/showthread.php?t=572819](http://ubuntuforums.org/showthread.php?t=572819)

---

### Post by cadcrazy on 2008-01-06
Buddy that repositary list is only needed if you want to install packages from online repo. What apt does is builds a dependency tree and for that thing it don't need any net connection to see that any perticular deb packages has that dependencies. If all dependencies are satisfied it installs the package(s) from local repo as well.

Again I must say it is very much possible. There is a trick to do it. But unfortunately i am not able to find it.
If i have never seen America that doen't mean America doesn't exists on this earth

---

### Post by cadcrazy on 2008-01-06
> **brianC said:**
> This page might help
[http://ubuntuforums.org/showthread.php?t=572819](http://ubuntuforums.org/showthread.php?t=572819)

Already know it but again it uses same dpkg command

---

### Post by mcduck on 2008-01-06
> **cadcrazy said:**
> Buddy that repositary list is only needed if you want to install packages from online repo. What apt does is builds a dependency tree and for that thing it don't need any net connection to see that any perticular deb packages has that dependencies. If all dependencies are satisfied it installs the package(s) from local repo as well.

Again I must say it is very much possible. There is a trick to do it. But unfortunately i am not able to find it.
If i have never seen America that doen't mean America doesn't exists on this earth

Yes, the repository list _is_ needed. That's where the apt-get gets all the information about the available packages, the information needed to build the dependency tree.

When you have once installed something from repositories, apt-get already has this information, and that allows it to work as long as the information is correct and all packages have the exact versions the downloaded repository index told they would have.

When the repositories change, you need to get the new index file. That's what is downloaded when you run 'sudo apt-get update' or click the update-button in Synaptic.

The reason why you may be able to install packages that are in apt's cache is that they were already mentioned in the repository indexes, and so apt-get knows about them already. And as apt-get checks it's cached files before downloading anything from the internet, you are even able to install those files when you don't have a working Internet connection.

Local repository is a repository as well, and needs the index file just like any other repository needs it. Without the index apt-get has no way of knowing what files are available.

If you want to install local files, you either need to create a repository for the files (that is what apt-on-cd does) or use the correct tool (dpkg) to install the packages without a repository.

---

### Post by cadcrazy on 2008-01-06
> **mcduck said:**
> 
If you want to install local files, you either need to create a repository for the files (that is what apt-on-cd does) 

For me apt-on-cd is just copy and paste tool to and from /var/cache/apt/archives and a cd wastager :d  tool and nothing else.
Btw why i have to waste a cd everytime want to install a package. 

Can't i add local folder as repo to /var/apt/sources.list

---

### Post by mcduck on 2008-01-06
> **cadcrazy said:**
> For me apt-on-cd is just copy and paste tool to and from /var/cache/apt/archives and a cd wastager :d  tool and nothing else.
Btw why i have to waste a cd everytime want to install a package. 

Can't i add local folder as repo to /var/apt/sources.list
No, repository is more than just a folder with .deb files in it. If you create a proper local repository, you can of course add it to sources.list.

Anyway, here's a howto about creating repositories: [http://ubuntuforums.org/showthread.php?t=42862]("http://ubuntuforums.org/showthread.php?t=42862")

You don't need to waste any CD's for installing packages as long as you use the tool made for installing packages, dpkg. ;)

I still can't  understand why you want to do such a simple task the hardest possible way, using the tool made for the task you'd already have the packages installed..

---

### Post by cadcrazy on 2008-01-06
But how we are able to install the packages from apt-cache without following that procedure to add it as a local repo. That means it is already added as repo by default. And i'am not finding anything different in the above mentioned link like (some list is being downloaded from net). All it does is add some folder as local repo ( which in case of /var/cache/apt/archives is already done). 

So where is the problem ?

---

### Post by mcduck on 2008-01-06
> **cadcrazy said:**
> But how we are able to install the packages from apt-cache without following that procedure to add it as a local repo. That means it is already added as repo by default. And i'am not finding anything different in the above mentioned link like (some list is being downloaded from net). All it does is add some folder as local repo ( which in case of /var/cache/apt/archives is already done). 

So where is the problem ?
No, apt's cache directory is not a local repository. It's just a cache where apt stores files it has downloaded, so that it doesn't need to download them again if you choose to reinstall them.

Like I said already, apt-get needs the repository index files to get information about available packages and their dependencies. When you have connected to a repository, apt-get has already downloaded this information, and uses it when you are installing programs.

So you already have downloaded the index files and _that_ is what allows apt-get to install those packages. The only difference is that it doesn't actually download them from the internet because it finds them in it's own cache.

But this only works for those packages that apt-get already knows about. So you can't just copy packages to apt's cache and install them from there. Apt would never even know that those packages exist.

---

### Post by cadcrazy on 2008-01-06
Also in open Suse there is direct option for adding local folder as repo. No need to connect to need net to get that damn list. Only need backed up rpms to that folder. So i don't think there is any need of such damn list to be downloaded to install cached deb packages

---

### Post by mcduck on 2008-01-06
> **cadcrazy said:**
> Also in open Suse there is direct option for adding local folder as repo. No need to connect to need net to get that damn list. Only need backed up rpms to that folder. So i don't think there is any need of such damn list to be downloaded to install cached deb packages
OpenSUSE is different Linux distribution, and uses different type of packages and different package manager.

The simple fact is that apt-get _does_ need the repository indexes to tell it about available packages, and there is nothing you can do about it. Either create a repository that has such a file, or use dpkg to install the packages.

---

### Post by cadcrazy on 2008-01-06
Suppose i want to install vlc.deb. It has [COLOR="Blue"]x1[/COLOR] and [COLOR="Blue"]x2[/COLOR] dependencies. [COLOR="Blue"]X1[/COLOR] further has [COLOR="Blue"]x1.1[/COLOR] and[COLOR="Blue"] x1.2[/COLOR] dependencies. 

So the install seq may be like this. Install x1.1 & x1.2 , x1, x2 and finally vlc. And for your kind info this dependency info lies very much inside the .deb package file not on your damn  internet list. For your proof if we double click on vlc.deb file we are prompted  x1 dependency not satisfied. Do you think that gdeb package installer connected to net to find that vlc.deb package need x1 dependency . I must say :lolflag: 

Ok next i double click on x1 to install it first before vlc and it complaints about missing x1.1 . then i install X1.1 . Now it'll complaint about x1.2.  and so on

What apt does is just automate this process by building dependency tree after looking inside each .deb file ( not from damn list downloaded from net) and if all dependencies are satisfied it installs all the packages with correct sequence automatically.

Now tell me what is the requirement of that damn list and internet . it is the simple logic. And this is irritating thing put in by damn ubuntu developers to irritate users with no net connection and nothing else.

i think[SIZE="3"][COLOR="Blue"] ubuntu is not for human Beings[/COLOR][/SIZE] its is only for Netizens. remove this quote ubuntu is for human beings.

If Open Suse can do it than why not Ubuntu. I still can't digest it is impossible. logically it is possible. But if Ubuntu community want me to bang my head thats the another thing

---

### Post by mcduck on 2008-01-06
> **cadcrazy said:**
> Suppose i want to install vlc.deb. It has [COLOR="Blue"]x1[/COLOR] and [COLOR="Blue"]x2[/COLOR] dependencies. [COLOR="Blue"]X1[/COLOR] further has [COLOR="Blue"]x1.1[/COLOR] and[COLOR="Blue"] x1.2[/COLOR] dependencies. 

So the install seq may be like this. Install x1.1 & x1.2 , x1, x2 and finally vlc. And for your kind info this dependency info lies very much inside the .deb package file not on your damn  internet list. For your proff if we double click on vlc.deb file we are prompted  x1 dependency not satisfied. Do you think that gdeb package installer connected to net to find that vlc.deb package need x1 dependency . I must say :lolflag: 

Ok next i double click on x1 to install it first before vlc and it complaints about missing x1.1 . then i install X1.1 . Now it'll complaint about x1.2.  and so on

What apt does is just automate this process by building dependency tree after looking inside each .deb file ( not from damn list downloaded from net) and if all dependencies are satisfied it installs all the packages with correct sequence automatically.

Now tell me what is the requirement of that damn list and internet . it is the simly logic. And this is irritating thing put in by damn ubuntu developers to irritate users with no net connection and nothing else.
Yes, the dependency information is included in the .deb packages. But it's also in the repository index file so that every time you want to install something from the repository you don't need to actually read through all the files to get their dependencies. So while dpkg uses the dependency information included in the package itself, apt-get uses the repository index as that's more practical when working with internet repositories (which are what apt-get is for).

> **cadcrazy said:**
> 
i think[SIZE="3"][COLOR="Blue"] ubuntu is not for human Beings[/COLOR][/SIZE] its is only for Netizens. remove this quote ubuntu is for human beings.
As mentioned numerous times in this thread, you don't need Internet connection to install the packages. You only need to use the tool that is made for installing packages that you already have downloaded. That tool is dpkg.

> **cadcrazy said:**
> 
If Open Suse can do it than why not Ubuntu. I still can't digest it is impossible. logically it is possible. But if Ubuntu community want me to bang my head thats the another thing
Like I already said, OPenSUSE uses different packages, and different package manager that works in a different way. There is absolutely no reason for apt-get to be able to install local packages because there is another tool for that task.

Banging your head on this thing is your own choice. We have already explained to you how to install your packages. And I even gave you instructions to do it the hard way, which you for some reason insist on doing.

---

### Post by cadcrazy on 2008-01-06
Ok apt need repo index right. See this [method]("http://ubuntuforums.org/showpost.php?p=219743&postcount=1") .Where is the command to download that index files. 
Also theres nothing mention like copying that index files to another system which has no net connection

---

### Post by mcduck on 2008-01-06
> **cadcrazy said:**
> Ok apt need repo index right. See this [method]("http://ubuntuforums.org/showthread.php?t=42862") .Where is the command to download that index files. 
Also theres nothing mention like copying that index files to another system which has no net connection
Since that howto is about _creating_ a repository, there of course is no need to download any index file. Actually that wouldn't even be possible since you would never be able to find a index file that has exactly the packages you put into your own repository.

Instead that instruction tells you how to create the index, using dpkg-scanpackages to read the information from the packages and then write it into the index. (Packages.gz and Sources.gz)

So in that howto the index file is not downloaded, it's created. :)

THen, when you _use_ the repository, apt-get downloads the index file to find out what packages the repository has, and to get information about those packages.

Since you don't seem to believe what I'm telling you about how apt works, here's what Wikipedia says about it:> 
APT relies on the concept of repositories in order to find software and resolve dependencies. For apt, a repository is a directory containing packages along with an index file. The Debian project keeps a central repository of over 19,000 software packages ready for download and installation.

For extra packages, any number of additional repositories can be added to APT's sources.list configuration file and then be queried by APT. Once a package repository has been specified (like during the system installation), packages in that repository can be installed without specifying a source.
[http://en.wikipedia.org/wiki/Advanced_Packaging_Tool]("http://en.wikipedia.org/wiki/Advanced_Packaging_Tool")

---

### Post by cadcrazy on 2008-01-06
Ok thanks for clearing my doubts. its not the question of beleiving you or not . 
But the Ubuntu Developers should have added an option to install local folder as a repo by default through GUI or there must be some gdebi like version of apt ( to use deb file info not repo index). And no one suggested this feature to be included in it ????

Can i suggest this feature to developers ???

---

### Post by mcduck on 2008-01-06
> **cadcrazy said:**
> Ok thanks for clearing my doubts. its not the question of beleiving you or not . 
But the Ubuntu Developers should have added an option to install local folder as a repo by default through GUI or there must be some gdebi like version of apt ( to use deb file info not repo index). And no one suggested this feature to be included in it ????

Can i suggest this feature to developers ???
Of course you can suggest that to Synaptic's developers, but since there already are both command-line and graphical tools for installing local packages (dpkg and gdebi) it's quite unlikely that they would add such a feature to Synaptic.

---

### Post by cadcrazy on 2008-01-06
but dpkg force install the package whether or not any dependency satisfied. Nothing can match apt. It install everything properly. Thats the thing i want not the broken packages and instability as in case of dpkg.

---

### Post by cadcrazy on 2008-01-06
I wonder what is the benefit of downloading that indexes if the dependencies info is very much inside the deb file. i do't see any performance benefit if i update my packages everyday.

---

### Post by mcduck on 2008-01-06
No, dpkg doesn't force install anything as long as you don't tell it to do so by using the -f option. Actually apt-get (and thus also Synaptic) uses dpkg to handle the actual installing of packages.

The benefit from having a index files for repositories is simple; it allows apt to get information about all the packages without actually downloading them.

If there wasn't such a file you would have to download the package to find out what it's dependencies are, and then download them, find out what their dependencies are, download them and so on (not to mention that apt wouldn't know what packages are actually available, so it would have to read through all files in the repositories to get that information).

Or the other way would be that the repository server would figure out what packages you need, but that would be pretty hard since the server wouldn't know what packages you have installed. Not to mention the enormous load on the servers if instead of just serving files they would also need to read through loads of packages and figure out what packages every Ubuntu user needs..

So instead of these options you just download a single file from the repository, and now apt knows about all available packages, and has all the information it needs to figure out what packages you need to install. So it only has to ask the server for the actual package files. And, best of all, the information is now on your own computer, so there is no need for any network communication between your computer and the server just to get information about packages and find out what packages you need to get to install some program. THat gives you a pretty nice performance benefit even on a high-speed network connection, not to mention those still using a modem..

(Updating your package list more often doesn't give any performance benefits, it gives you up-to-date information about available packages. IF the information is outdated, apt-get might not be able to find the packages you are looking for, or it might install older versions of packagesas it doesn't know about the new version)

---

### Post by cadcrazy on 2008-01-06
> **mcduck said:**
> 
(Updating your package list more often doesn't give any performance benefits, it gives you up-to-date information about available packages. IF the information is outdated, apt-get might not be able to find the packages you are looking for, or it might install older versions of packagesas it doesn't know about the new version)
I am not talking about list but abt the daily update through update manager.

---

### Post by cadcrazy on 2008-01-06
> **mcduck said:**
> No, dpkg doesn't force install anything as long as you don't tell it to do so by using the -f option. 

If i use "dpkg -i *.deb" it'll install the packages whether or not all dependencies satisfied. So as a result i may get broken packages. Also can't i download and copy that index file to my friends system manually. Now i'am asking this all out of curiosity.

---

### Post by mcduck on 2008-01-06
> **cadcrazy said:**
> If i use "dpkg -i *.deb" it'll install the packages whether or not all dependencies satisfied. So as a result i may get broken packages. Also can't i download and copy that index file to my friends system manually. Now i'am asking this all out of curiosity.
It should not, and it doesn't do that for me. If  the dependencies can't be satisfied it will tell that and abort the installation.

I don't know why it doesn't work correctly for you, but try this: "dpkg -i --no-force-all *.deb". That would specifically tell dpkg to not force anything.

It might be possible to just manually download the index files from repositories, but I don't know how to get apt-get to recognize them, I've never seen any reason to do that as it's much easier to just use dpkg to install local packages.

---

### Post by mcduck on 2008-01-06
> **cadcrazy said:**
> I am not talking about list but abt the daily update through update manager.
I don't understand what you mean.

The update manager does many things, it downloads the index files, compare them to your installed packages and then figures out if there are new versions of any packages you have. Then it lists those possible updates to you and allows you to install them.

So it combines 2 CLI commands, 'sudo apt-get update' (to get the new index files and update the information about available packages) and 'sudo apt-get upgrade' (to download and install all available new package versions).

The update manager needs the repository index just for the same reasons apt-get needs them. It's just another frontend for apt-get, made to be a simple tool for updates (compared to Synaptic, which is a full-featured frontend to handle all package management features of apt-get).

---

### Post by cadcrazy on 2008-01-06
The main reason i was doing away with dpkg is the prob of force install. Will give this commnand a try.
Will it give missing dependency if any ?

---

### Post by mcduck on 2008-01-06
> **cadcrazy said:**
> The main reason i was doing away with dpkg is the prob of force install. Will give this commnand a try.
Will it give missing dependency if any ?

It should tell you if any dependencies are missing and then abort installing those packages with dependency problems. But that's what dpkg should do anyway.. I've never actually tried that command myself, as it's just tellling dpkg to do what it should do by default anyway. But I hope it works for you.

The downside of that command is that it will not allow you to downgrade a package (install older version than what you already have). So you could also try "sudo dpkg --no-force-depends -i *.deb".

I'm still amazed that dpkg isn't working correctly for you, it really should not force installing anything by default.

---

### Post by cadcrazy on 2008-01-06
But it does.It is discussed many times here that use sudo apt-get install -f command after installing packages with dpkg to fix the broken packages.

Could you plz tell me link to  use dpkg in different ways

---

### Post by mcduck on 2008-01-06
> **cadcrazy said:**
> But it does.It is discussed many times here that use sudo apt-get install -f command after installing packages with dpkg to fix the broken packages.

Could you plz tell me link to  use dpkg in different ways
Maybe the --force option is enabled by default in Ubuntu for some reason. I remember hearing that Debian unstable has it enabled by default, and as Ubuntu is pretty much related to that it could be that we have inherited that setting from there. It just makes me wonder why dpkg doesn't force anything on any of my machines..

Anyway, try the command I gave you, even if the --force is enabled by default that should disable it.

Pretty much all information about different options for dpkg can be found simply by running 'man dpkg'. Same works for all other programs. If that doesn't give the information I'm looking for I usually consult Google ;)

---

### Post by mcduck on 2008-01-06
I just remebered that you can also use the --simulate option with dpkg to check if everything would work correctly, without actually doing any changes to your system.

I also noticed that Synaptic now has option "Add Downloaded Packages" in the File-menu. While that seems to be made for installing packages you have downloaded with the "Generate package download script"-option it might work for installing .deb packages downloaded in other ways as well..

---

### Post by thelatinist on 2008-01-06
If your problem was with dpkg forcing install, why on earth didn't you ask how to prevent it from forcing in the first place?  I'm sorry if I'm a bit impatient, but this is ridiculous.  apt-get is for repositories, dpkg is for local files.  Get over it.

---

