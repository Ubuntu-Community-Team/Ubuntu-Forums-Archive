---
title: "Marillat Repository"
date: 2005-05-31
forum: Absolute Beginner Talk
---

### Post by kozmo on 2005-05-31
What is the story with the Debian-Marillat repository?

The [Ubuntu Guide](http://www.ubuntuguide.org/#extrarepositories) lists this repository to be added to the sources.list -- without it you cannot install some of the packages listed in the Ubuntu Guide.

However, I have seen users saying not to add this repository. That it is unstable, not secure, not needed anymore, etc.

So what is the real story with the Marillat repository?

---

### Post by NewbieNik on 2005-05-31
I could be wrong, but this is how I figure it. The ubuntu guide is written by users rather than Ubuntu. Some users have created Repositories outside of the Ubuntu group to help keep some of the more obscure builds and packages alive. Some of these are not fully supported by Ubuntu or the more experienced users feel that compiling their own sources a lot more reliable.
As a new user to Ubuntu I find the Marillat depository handy, but not essential as sometimes I have more than a little problem compiling some of the packages from the source code, but I shall persist until one day, repositories will become little more than archives.
All in all I say good luck to anyone who wants to help further the Open-source user-base.

---

### Post by somuchfortheafter on 2005-05-31
i use them for my server, laptop, and now my desktop, and all are rock solidly stable so you should be fine.

---

### Post by shof2k on 2005-05-31
[QUOTE=somuchfortheafter]i use them for my server, laptop, and now my desktop, and all are rock solidly stable so you should be fine.[/QUOTE]
 Marillat is a library of 'other' useful programs that aren't in the ubuntu standard libaries.  I've never had a problem with them and the programs are useful afaik.

Good luck

---

### Post by poofyhairguy on 2005-05-31
[QUOTE=kozmo]What is the story with the Debian-Marillat repository?

The [Ubuntu Guide](http://www.ubuntuguide.org/#extrarepositories) lists this repository to be added to the sources.list -- without it you cannot install some of the packages listed in the Ubuntu Guide.

However, I have seen users saying not to add this repository. That it is unstable, not secure, not needed anymore, etc.

So what is the real story with the Marillat repository?[/QUOTE]

Hello. I'll tell you because I am the one on the crusade against it.

The use of the Debian-Marillat repo. is left over from the early days of Ubuntu when we didn't have our own repos to carry legally troubling things (especially windows media player codecs and dvd css). Since that time we have our own repo. (the backport repo) that has most of these things. The only thing that it lacks for me is the newest (version 7) acrobat reader, everything else needed from Debian-Marillat the backport repo has. If it lacks something for you, add the french repo just ot get it then take it away to avoid breakage.

Ubuntu is starting to pull away from debian and as it does the packages will become less compatible (like mandrake rpms on fedora install or what have you). I have run into problems and have had apt-get breakage because of the Debian-Marillat depending on Debian's repos being there (not Ubuntus).

With the backport repo you can dist-upgrade to new stuff without fear, with Debian-Marillat it can cause breakage. The Debian-Marillat is not needed and won't be needed in future unless backports go away (or its legally questionable files go away). Its a compatibility problem and my work to get people off the Debian-Marillat is work to allow them to upgrade their computers without fear.

there. Your answer from horse's mouth.

---

### Post by Jenda on 2005-05-31
> The ubuntu guide is written by users rather than Ubuntu.
It's actually pretty much all done by Jiyuu0.

---

### Post by jobezone on 2005-05-31
I undestood you're entire post, but this intrigued me:
> Ubuntu is starting to pull away from debian...
How can Ubuntu be starting to pull away from debian, if in 4/5 months from now they will take a snapshot of Debian sid to begin development of the release after Breezy, like they have done for every release so far?

Correction to my post: Of course the first thing they do to this snapshot of Debian is apply their custom modifications made to the previous release, but still this is very different than the case with RedHat and Mandrake, where mandrake went in a totally different direction.

---

### Post by poofyhairguy on 2005-05-31
[QUOTE=jobezone]
How can Ubuntu be starting to pull away from debian, if in 4/5 months from now they will take a snapshot of Debian sid to begin development of the release after Breezy, like they have done for every release so far?
[/QUOTE]

Good question. The answer is that Ubuntu does do some things that even Sid doesn't. For example, Sid didn't have Xorg but Hoary does. Hoary can actually get ahead on Sid or behind it- the Universe is a sync at a certain point in time but the main is heavily modified and some is carried along.

---

### Post by kozmo on 2005-06-03
[QUOTE=poofyhairguy]Hello. I'll tell you because I am the one on the crusade against it.

The use of the Debian-Marillat repo. is left over from the early days of Ubuntu when we didn't have our own repos to carry legally troubling things (especially windows media player codecs and dvd css). Since that time we have our own repo. (the backport repo) that has most of these things. The only thing that it lacks is the newest (version 7) acrobat reader, everything else needed from Debian-Marillat the backport repo has. 

Ubuntu is starting to pull away from debian and as it does the packages will become less compatible (like mandrake rpms on fedora install or what have you). I have run into problems and have had apt-get breakage because of the Debian-Marillat depending on Debian's repos being there (not Ubuntus).

With the backport repo you can dist-upgrade to new stuff without fear, with Debian-Marillat it can cause breakage. The Debian-Marillat is not needed and won't be needed in future unless backports go away (or its legally questionable files go away). Its a compatibility problem and my work to get people off the Debian-Marillat is work to allow them to upgrade their computers without fear.

there. Your answer from horse's mouth.[/QUOTE]
I have the backports listed in the Ubuntu User Guide, but not the Marillat repository. However, I am not able to install Nvu,DVD Ripper, gFTP, and a few others. How do I install these packages using apt-get, as opposed to downloading the tarballs from their respective sites?

---

### Post by poofyhairguy on 2005-06-03
[QUOTE=kozmo]I have the backports listed in the Ubuntu User Guide, but not the Marillat repository. However, I am not able to install Nvu,DVD Ripper, gFTP, and a few others. How do I install these packages using apt-get, as opposed to downloading the tarballs from their respective sites?[/QUOTE]


What you can do is add the lines of marillat, 

sudo apt-get update

sudo apt-get install whatever

Then go back into the sources.conf and delete those lines. You are taking a risk by doing this that I don't advise most to take, but if you need then you need. The main problem I have with marillat is people not deleting  (or commenting out) the lines right after use and then upgrading later with all kinds of junk from the repo. Treat it like any unofficial repo- with caution. 


 If you need something that isn't in the backport repo yet, you can also kindly ask jdong for it.

---

### Post by Efwis on 2005-06-04
I was looking at the changelog today and noticed that as of yesterday, june 3, 2005 the repos on the ubuntuguide are now 100% marillat free.

---

### Post by kozmo on 2005-06-04
[QUOTE=Efwis]I was looking at the changelog today and noticed that as of yesterday, june 3, 2005 the repos on the ubuntuguide are now 100% marillat free.[/QUOTE]
Yes, I noticed that to.

Now when new people try to use the [Ubuntu Guide](http://www.ubuntuguide.org) they will an error **package not found **when they try to install certain packages listed in the guide.

---

### Post by ShaneAu on 2005-06-04
[QUOTE=kozmo]Yes, I noticed that to.

Now when new people try to use the [Ubuntu Guide](http://www.ubuntuguide.org) they will an error **package not found **when they try to install certain packages listed in the guide.[/QUOTE]
 Unless it's added to Ubuntu Backports, which I'd say will eventually come.

---

### Post by poofyhairguy on 2005-06-04
[QUOTE=kozmo]Yes, I noticed that to.

Now when new people try to use the [Ubuntu Guide](http://www.ubuntuguide.org) they will an error **package not found **when they try to install certain packages listed in the guide.[/QUOTE]


I think the plan it to wget the debs needed in those cases.

---

### Post by poofyhairguy on 2005-06-04
Look here:

[http://www.ubuntuforums.org/showthread.php?p=199691#post199691](http://www.ubuntuforums.org/showthread.php?p=199691#post199691)

The breakage I have encountered before. This is why for the most part that french repo must go.

---

### Post by jiyuu0 on 2005-06-04
the UbuntuGuide will work fine... as Backports has all the Marillat packages that UbuntuGuide is using...

---

