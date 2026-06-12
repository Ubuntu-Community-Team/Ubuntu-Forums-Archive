---
title: "Installing in Linux(Ubuntu) vis a vis installing in windows"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by aijazbaig1 on 2007-01-20
Hello,
I am, (as the title might have suggested) a complete newbie to Linux and Ubuntu in general. So I am getting to get the feel of ubuntu and linux. But being used to do things a certain (windows :rolleyes: ) way, i have a lot to learn.
So I first would like to clear the idea of installing new programs.

To begin with, as far as I have learned, new programs seems to be in the so called repository and the list can be seen using the add/remove functionality under the applications menu (I have a Ubuntu 6.06 release). One can select from the list by checkin the box and remove a program by uncheckin it.

But there seems to be occasions wherein I have installed certain things like for instance the real player 10 fr linux directly from the website by following the instructions and by selecting my home folder to copy the files.
I then faced problems embedding the player in firefox for streaming vids so I chkd the plugin doc for mozilla which advised me to copy two files one viz. nphelix.so to the mozilla plugins directory and another file called nphelix.xpt to the mozilla components directory.
Now i found both these files placed in a directory named mozilla in my home directory. Infact these were the only 2 files in that directory.
Secondly there was a directory called plugins but it is directly under the home directory and exists outside the mozilla directory. How does that make sense?? i mean 'normally' i would expect the mozilla plugins directory to exist as a subfolder within the mozilla directory..bt again i may be mistaken...:roll: 
I was goin crazy and i thought may be my previous installation hasn't worked the way it should or may be I specified a wrong place to copy the files and I dont know where the files are..(they weren't in the usr/local/realplayer/mozilla directory..infact there wasn't any directory by called realplayer in that path at all...)
So i installed realplayer again using the add/remove functionality and now i see that I have the executable file in the 'sound and video' portion of the applications menu.
But i still don't have the directory called realplayer in the usr/local/ path. Is it because I installed a 'single program' but not the package??..
I am going bonkers at all this... ](*,) 

So will some one simplify what installing actually means in linux. And does it effect registry values in any way like it does in windows? What is the difference between using packages for the installation and installing single application(s). 

Secondly please guide me as to how I should remove all instances of real player, I have one in which real player seems to be in my sound and video part under 'applications menu' and there seems to be a 'second instance' wherein there are three files viz. realplay(shell script), realplay.bak and realplay.bin lying in my home folder out of which the bin file is executable. I had heard tht in linux one can directly remove a program by removing the files associated with it. Is it true?

I thank you in advance for the patience with which you may have read my amateurish post but it will surely go a long way in making me switch over to linux  whole heartedly.

Hope to hear from you pretty soon, ):P 

Aijaz Baig.

---

### Post by The Joe on 2007-01-20
To completely get Real Player use Synaptic. System - Administration - Synaptic Package Manager, if I'm right it's in the Ubuntu repositories, if you can't find it you will need to activate Universe and Multiverse repositories or check [http://www.packages.ubuntu.com](http://www.packages.ubuntu.com), this has all the packages available in the repository for direct download, unfortunately I can't remember how to activate Uni/Multiverse repositories (I've lost my opportunity to use Ubuntu online for now) with Synaptic as I've only done it with Adept.

Hope I helped, and welcome to the wonderful world of Ubuntu

---

### Post by aijazbaig1 on 2007-01-20
Hello.
Well...to begin with packages.ubuntu.com doesn't seem to exist. Secondly I do see the synaptic package manager but i would still like to know more abt multiverse and universe repositories.
Furthermore, how do I clear the mess with realplayer now? I mean I would like to remove all instances of realplayer.
If u read my 1st post U would see that I have seemingly installed realplayer twice..so how do I remove them..pls have a look at that post again as I have put a lot of effort to make it as clear as possible.
I hope this helps..:cool: 

Best regards,
Aijaz Baig.

---

### Post by Sef on 2007-01-20
To get some programs you need to [enable the  universe and multivers]("https://help.ubuntu.com/community/Repositories")e repositories.

Also read [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats") for easy installing, so you can play certain music formats, download java, and more.

---

