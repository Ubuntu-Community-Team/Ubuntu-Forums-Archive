---
title: "Getting packages without an internet connection"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by eisenstein on 2007-08-31
I know this question keeps coming up in various guises, but after several hours of searching I still can't find the right "how to."  If someone can help me sort this out,  I'll do my best to write a clear guide for others.

The problem is: How to find and download deb packages on a windows machine that has an internet connection, and install them on an Ubuntu machine that does not have an internet connection.  The packages in question are not on the distro CD. I know how to transfer and install the .deb packages once I've got them on the windows machine.  The problem is finding all package dependencies and the locations of the corresponding .deb files in the archives.  

In my case (X11 development files) it's a complicated dependency tree.  On packages.ubuntu.com I can find the packages and their dependencies by hand, but I can't see how  to download the .deb files for each package, or find where they're located in the repositories.  It gives me an option to download the source files for each package, but trying to compile from source is just asking for more trouble.  Am I missing something here?  How can I go from package names to actual locations of .deb files in repositories?

Note: I can't use synaptic or apt-get to do this for me, because the linux machine is not connected to the internet and so can't find the  repositories where the packages are located.  Is there some web site somewhere that can generate download scripts from package names?  Or even just a list of package locations for manual download?

One idea I've read is to find a linux box that is connected to the internet, generate the download script from it, and use that to download onto the windows box.  That would work except I honestly don't know of any other linux machines around here.  Mine would be connected except I can't get the !@#$% wireless working with firefox.  But if someone wants to take pity on me, they could generate the download script from synaptic for the following packages libx11-dev and xlibs-dev (plus anything else I might be needing?)  That would solve my problem now but I think we should still come up with a clear solution that doesn't depend on this workaround.

Thanks for any help on this--

Ben

---

### Post by Irihapeti on 2007-08-31
I can sympathise. I went down this road myself, until I was able to get a (dialup) connection working in Ubuntu.

You've evidently found packages.ubuntu.com. Click on the package name that you want, which will bring up a screen that says, among other things, "download <package>". Then choose  your architecture. That will give a choice of servers to download from.

You don't say what version of Ubuntu you are using. If you are using the 2.6.20-16 kernel in feisty, gdebi package installer gives you a complete list of dependencies. With the -15 kernel, I found it will only name one missing dependency at a time and if there are several, that gets frustrating, going backwards and forwards.

I believe that someone has developed a way of managing downloads of dependencies to a Windows box, but of course I don't now remember where I saw it! (I think it was on these forums,though.)

I'd prefer to leave it to someone else to generate you a download script, because mine would show servers in NZ rather than where you are.

Hope this is of some use.

Irihapeti

---

### Post by louieb on 2007-08-31
It considered bad forum manners to create duplicate threads. If you haven't got an answer after a day or so then its ok to bump your thread by posting to it again. I put my 2 cent worth in you other thread.  
[http://ubuntuforums.org/showthread.php?t=539877](http://ubuntuforums.org/showthread.php?t=539877)

---

### Post by Irihapeti on 2007-08-31
louie:

I noticed that there were two identical messages. The times were only a few minutes apart. I put it down to mistake - hitting the send button twice or something like that. I'd rather make that assumption until I find out definitely that I'm wrong.

---

### Post by eisenstein on 2007-08-31
thanks for both solutions.  i don't know how I missed the download option on the packages.ubuntu.com site- but I see it now.

---

### Post by eisenstein on 2007-08-31
BTW, sorry about the double post.  what happened is that on the first attempt to post, I was given a login screen.  I was logged in before, but I figured maybe I had timed out.  So I logged in and was given the same Submit Reply screen.  Only later did I find out it had already posted the message the first time around.

I thought this might be a bug in the forum software, but then to reproduce it I would probably have created even more double posts.

---

### Post by bone2006 on 2007-09-01
I've had a similar situation and it was not that internet was a problem, it was that the computer was going to be located in a room that because of security internet could not be used in this room.  It's one of the downfalls I've seen.  
It's suprising to me that it has been so difficult to get somethings installed without interent.  I figured there should be plenty of labs that cannot have internet, because of security yet to find a real working solution hasn't been easy for me.  I've tried a lot of things, but never found something that worked as promised or what's a pain.  

Like if you want to install just winzip, you'd download winzip.exe and the setup would run on windows, yet with Linux I've spent hours trying to chase dependencies, which for just one application is a pain.  I honestly love linux, but it's a big negative for me.  Most people responde right away with get your internet fix or something else, because that's their solution, but there's many situations that interent might not be possible like the situation I'm in.

The solution form e was to find a distro that had almost all the packages already integrated that I would need.  I ended up going with Mepis on this computer instead of ubuntu, since there's more packages in Mepis for my needs.  I would have loved to install ubuntu and made a quick CD with just setup applications, but doesn't work that easily.

---

### Post by louieb on 2007-09-01
> **eisenstein said:**
> ...about the double post ... 
No problem. This forum gets a lot of people that a new to forums in general and some get impatient.  Saw your join date and post count.  hummm.   Anyway glad you found a way to get the packages you needed. see ya.:guitar:

---

### Post by eisenstein on 2007-09-01
> **bone2006 said:**
> Linux I've spent hours trying to chase dependencies, which for just one application is a pain.  I honestly love linux, but it's a big negative for me.  Most people responde right away with get your internet fix or something else, because that's their solution, but there's many situations that interent might not be possible like the situation I'm in.


Yeah, it's a pain.  It's a shame because the Ubuntu package manager seems like a really good way to go.  And all the info is there to automaticaly download a package and all it's dependencies onto a windows machine, then burn a cd or copy to usb drive, and then bring it up in synaptic on the linux box.  The problem is that currently the only way to get that info is through synaptic, which only works if you've got the internet connection on the linux box.

a nice solution would be for some smart person to add the synaptic functionality to the packages.ubuntu.com site- i mean just enough to select packages and download all the dependent deb files into a directory on whatever computer is connecting to the web site.  then transfer that by cd or whatever to the linux machine and install from synaptic.

---

### Post by ramjet_1953 on 2007-09-01
Slightly off-topic, but for you to really apprciate Ubuntu and Linux in general a good high-speed Internet connection is preferable.

Save up your pennies and take the plunge for ADSL, you won't regret it.

Regards,
Roger :cool:

---

### Post by capink on 2007-09-02
> **bone2006 said:**
> yet with Linux I've spent hours trying to chase dependencies, which for just one application is a pain.  

You don't need to chase dependencies. Just type:

```
sudo apt-get install packagename --print-uris
```

And it will give all dependencies together with their uris. But note that some of those uris might be old since you have not updated your apt lists with apt-get update. For those broken uris, you will have to relocate the new versions.

---

### Post by bone2006 on 2007-09-02
Thanks, is there a command instead of install just to download since I already have them on this machine?
Thanks in advance

---

### Post by capink on 2007-09-02
Take a look [here]("http://ubuntuforums.org/showpost.php?p=3218434&postcount=4"). Using this method you will have a list of uris. You can download them all at once using a download manager like flashget. Just copy and paste all the uris into the flashget download box. I hope this helps.

---

### Post by Irihapeti on 2007-09-02
For people who already have a number of .deb packages on their machine and don't want to be prompted to download them again, have a look at this link.

[https://help.ubuntu.com/community/Repositories/Personal](https://help.ubuntu.com/community/Repositories/Personal)

However, I've discovered (buried deep in the apt-get documentation), that apt-get looks for your repositories in the order that they appear in sources.list. Therefore, if you put your local repository at the end of the file, apt-get still wants to download stuff off the internet. Frustrating. I'm on 56k dialup and I don't want to be downloading stuff I already have.

So, add your local repository at the top of the list. As far as I can make out, if there's a new version out there, you'll still get told about it.

It's been working well for me for a while now. 

HTH

Irihapeti

---

