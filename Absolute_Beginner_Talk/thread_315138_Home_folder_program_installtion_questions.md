---
title: "Home folder/ program installtion questions"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by Cikrum on 2006-12-08
Hi, 
I have recently began using linux and of course I love it :). I also havea few basic questions that I was not able to find in the ubuntu guides and on other Newb fourm posts. One Question is a trouble shooting question. As stated in several guides I got automatix2. I tryed the command line approch with the apt-get but it since Am on 6.06 Dapper and it got be the edgy one it will not run. Then I tryed just getting the package and that works, I do get the 6.06 version but once I restart my computer it reverts back to the 6.10 version. I was wondering if their was a way to prevent that from happening. My second question is in regards to program installation as well. I was wondering how to get application that I download manually in my application menu. I recently downloaded songbird (the media player) and I can open it out of the folder its in but I can't find a way to have it under the application menu. My third and final question is in regard to my Home folder. When I try to access my home folder in terminal it says it is not there. This also happens when I try to put a application on my toolbar and run it from there. It gives me a directory doesn't exist or permission denied.
Any kelp would be greatly appreciated
Thanks, Cikrum

---

### Post by ciscosurfer on 2006-12-08
> **Cikrum said:**
> Hi, 
I have recently began using linux and of course I love it :). I also havea few basic questions that I was not able to find in the ubuntu guides and on other Newb fourm posts. One Question is a trouble shooting question. As stated in several guides I got automatix2. I tryed the command line approch with the apt-get but it since Am on 6.06 Dapper and it got be the edgy one it will not run. Then I tryed just getting the package and that works, I do get the 6.06 version but once I restart my computer it reverts back to the 6.10 version. I was wondering if their was a way to prevent that from happening. My second question is in regards to program installation as well. I was wondering how to get application that I download manually in my application menu. I recently downloaded songbird (the media player) and I can open it out of the folder its in but I can't find a way to have it under the application menu. My third and final question is in regard to my Home folder. When I try to access my home folder in terminal it says it is not there. This also happens when I try to put a application on my toolbar and run it from there. It gives me a directory doesn't exist or permission denied.
Any kelp would be greatly appreciated
Thanks, CikrumHello, Cikrum!  And Welcome to Ubuntu Forums!

I will attempt to answer your question, one by one:
[LIST=1]
[*]If you are on Dapper, you need to use the Automatix2 that is [specifically made for Dapper]("http://getautomatix.com/wiki/index.php?title=Installation#Installing_on_.28K.2CX.29Ubuntu_6.06_i386.2Camd64_.28Dapper.29")
[*]You need to make sure that the sources you have listed in your /etc/apt/sources.list file are accurate and match what the getautomatix site says in order to get Automatix2 downloaded and running.  All info regarding how to get Automatix2 working can be found at their site.
[*]You should remove all of your automatix installs (for Dapper and Edgy and try only installing the Automatix2 install for Dapper this time -- this will probably effect the appropriate change you are looking for and won't keep reverting to a version that doesn't work with he version of Ubunt you are running.
[*]You can manually set an application into your menus by going to System > Preferences > Menu Layout.  From there, it should be self-explanatory.  If you still need help with this, simply post again, and I'll be happy to walk you through it.[LIST=1]
[*]As a side note to this, if you upgrade to Edgy from Dapper, you can use the Automatix2 install for Edgy and that has an option for Songbird in its options.  It will place an icon in your menu for you.[/LIST]
[*]How are you accessing your home folder in a terminal?  When you start a terminal, by default, you are already in your home folder.  You can type **pwd **to see what your current directory is at all times.  To change to another directory, you can use the command **cd** and then **c**hange **d**irectories to wherever you'd like to go.To quickly get back to your home directory (which will look something like this: /home/username) you can use the cd command as well, from anywhere in your directory structure and it will take you right back to your home directory.  Some people will also refer to their home directory by using a tilda ( ~ ) and some will also type **cd ~** (notice the space between cd and the ~) (commands in Linux are case-sensitve).  Let's say you are in the /usr/etc directory and you want to get back "home".  You simply need to enter in cd and then press Enter and will be magically transported back to your home directory.  Type **ls** for a directory listing.
[*]There are some good links in my signature you may want to look at to get your started.
[*]If you have any other questions, please post them on the Forums and someone will be able to help you out!
[*]Have fun and hope to hear from you soon![/LIST]

---

### Post by Cikrum on 2006-12-08
Thank you very much for the help, I now understand how the command line works a bit better and I was able to get the application in the menu as well. But I still am having trouble with the Automatix2. I went Synaptic package manager and removed the automatix2 through that. I then wen to the site you recommended which is how I had done it the first time. And like the first time it downloaded the edgy version. The way I had got the 6.06 version was at the top of the page the automated way with the package manager. With this way it worked once but after the reboot it reverted to edgy. 
Thanks again for the help
Cikrum
PS. I have the the 686 version of Dapper and what is the amd64 version

---

### Post by ciscosurfer on 2006-12-08
> **Cikrum said:**
> Thank you very much for the help, I now understand how the command line works a bit better and I was able to get the application in the menu as well. But I still am having trouble with the Automatix2. I went Synaptic package manager and removed the automatix2 through that. I then wen to the site you recommended which is how I had done it the first time. And like the first time it downloaded the edgy version. The way I had got the 6.06 version was at the top of the page the automated way with the package manager. With this way it worked once but after the reboot it reverted to edgy. 
Thanks again for the help
Cikrum
PS. I have the the 686 version of Dapper and what is the amd64 versionCan you go to terminal and type in the following...you can either copy/paste the code into the terminal or do it by hand...if you do it by hand, make sure you enter it correctly (then post the output of that command back here on this thread):```
ls /var/cache/apt/archives/ | grep automatix
```

---

### Post by Cikrum on 2006-12-08
automatix2_1.1-2.2-6.10edgy%5fi386_i386.deb
automatix2bleeder_1.2-1.2-6.10edgy%5fi386_i386.deb

---

### Post by ciscosurfer on 2006-12-08
The versions you haven installed are for Edgy.  You need the Dapper versions.

You need to remove what you currently have installed, both apps, b/c they are both Edgy apps...all one line in the terminal```
sudo aptitude remove automatix2 automatix2bleeder
```Go into your /etc/apt/sources.list and delete the line you added for Automatix.

Go back to the getautomatix.com site (click the wiki or install link) and make sure you follow the instructions to install Automatix2 for Dapper ONLY...NOT for Edgy.

Setup you /etc/apt/sources.list like you did before, update, install Automatix2.  The bleeder version only works on Edgy.

---

### Post by Cikrum on 2006-12-10
Well I think this is the problem but when I try to chance the file sources.list it says I dont have permission. I try to use chmod to change the  permission on it but it said operation not permitted. I am the only account on the computer and I have full access. I cannot save over it either and I cannot delete because of the permission problem.
thx of the support 
Cikrum

---

### Post by drphilngood on 2006-12-10
> **Cikrum said:**
> Well I think this is the problem but when I try to chance the file sources.list it says I dont have permission. I try to use chmod to change the  permission on it but it said operation not permitted. I am the only account on the computer and I have full access. I cannot save over it either and I cannot delete because of the permission problem.
thx of the support 
Cikrum

Try this for Ubuntu:
```
gksudo gedit /etc/apt/sources.list
```

or this for Kubuntu
```
kdesu kwrite /etc/apt/sources.list
```

or this for Xubuntu
```
gksudo mousepad /etc/apt/sources.list
```

See here if you need more info:
[psychocats-sources]("http://www.psychocats.net/ubuntu/sources")

---

