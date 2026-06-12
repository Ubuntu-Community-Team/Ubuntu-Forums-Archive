---
title: "[SOLVED] this is starting to annoy me..."
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by ~~Tito~~ on 2007-10-08
I cant install vmware server for whatever reason. . . I tried some guides and they never work. . .. It always gives me an error. I am getting mad. . . Some one link me to a guide that works. . . Its getting really complicated to simply install something. A RPM is worse. . .

---

### Post by llamakc on 2007-10-08
> **~~Tito~~ said:**
> I cant install vmware server for whatever reason. . . I tried some guides and they never work. . .. It always gives me an error. I am getting mad. . . Some one link me to a guide that works. . . Its getting really complicated to simply install something. A RPM is worse. . .

You know what else is frustrating? When somebody says they need a guide because the guides they've followed are not working, but always fail to tell the forum what they have ALREADY tried.

You should give more information, like the error message for starters.

---

### Post by doron387 on 2007-10-08
oh yes, welcome to this world... i started a week ago , installed 4 days ago and can't start the session yet... it is not enough beginner  user friendly yet.
good luck on your way.
:popcorn:

---

### Post by ~~Tito~~ on 2007-10-08
> **llamakc said:**
> You know what else is frustrating? When somebody says they need a guide because the guides they've followed are not working, but always fail to tell the forum what they have ALREADY tried.

You should give more information, like the error message for starters.

Well, when I installed it from the tar.gz it gave me this error. . . .```
tito@TITOS-LAPTOP:~$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/home/tito/bin/vmware-config.pl.

tito@TITOS-LAPTOP:~$
``` 

I followed all the guides in this thread. . .[http://ubuntuforums.org/showthread.php?t=570238&page=1](http://ubuntuforums.org/showthread.php?t=570238&page=1)

I followed them exactly, and it didn't give me any compiling errors. Yet I cant go in.

---

### Post by ~~Tito~~ on 2007-10-08
> **doron387 said:**
> oh yes, welcome to this world... i started a week ago , installed 4 days ago and can't start the session yet... it is not enough beginner  user friendly yet.
good luck on your way.
:popcorn:
I have been with ubuntu for almost one year, I am not new, this program is very frustrating to install. .

---

### Post by rsambuca on 2007-10-08
Perhaps you should consider a thread title which describes your problem, and is a little more civilized with it's use of language.

---

### Post by ThrobbingBrain66 on 2007-10-08
> **~~Tito~~ said:**
> Well, when I installed it from the tar.gz it gave me this error. . . .```
tito@TITOS-LAPTOP:~$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/home/tito/bin/vmware-config.pl.

tito@TITOS-LAPTOP:~$
``` 

I followed all the guides in this thread. . .[http://ubuntuforums.org/showthread.php?t=570238&page=1](http://ubuntuforums.org/showthread.php?t=570238&page=1)

I followed them exactly, and it didn't give me any compiling errors. Yet I cant go in.

So have you tried to configure it using the command in the error message?  What errors (if any) did that produce?

---

### Post by ~~Tito~~ on 2007-10-08
Ok, Will try.

---

### Post by ~~Tito~~ on 2007-10-08
> **ThrobbingBrain66 said:**
> So have you tried to configure it using the command in the error message?  What errors (if any) did that produce?

I did like 3 times. . . And It still showed that message. . .

---

### Post by llamakc on 2007-10-08
VMWare uses a kernel module that has to be properly installed (and/or compiled) along with other settings. Running that setup script is business as usual for VMWare.

---

### Post by llamakc on 2007-10-08
What command are you trying to run?

---

### Post by ~~Tito~~ on 2007-10-08
But it did. . . Is there a very detailed guide? I am not a noob but I need one that does every step and does not assume you know what that person is talking about.

---

### Post by ~~Tito~~ on 2007-10-08
> **llamakc said:**
> What command are you trying to run?
I just ran ```
vmware
``` and it showed that.

---

### Post by shad0w_walker on 2007-10-08
Try running this command:

```
/home/tito/bin/vmware-config.pl
```

---

### Post by llamakc on 2007-10-08
See that's the point: you can't run "vmware" until you've ran the perl script for configuring, JUST like the output in the error tells you to. That how-to on howtoforge also pointed that out.

Did you choose the defaults when you ran vmware-install.pl?

If you chose the DEFAULTS, you can type /usr/bin/vmware-config.pl to get the config done.

---

### Post by ~~Tito~~ on 2007-10-08
I uninstalled and I am looking for another guide, also i tried that and it gave me that" that is not a real directory or whatever. . .". Is there a more detailed guide?

---

### Post by ~~Tito~~ on 2007-10-08
> **llamakc said:**
> See that's the point: you can't run "vmware" until you've ran the perl script for configuring, JUST like the output in the error tells you to. That how-to on howtoforge also pointed that out.

Did you choose the defaults when you ran vmware-install.pl?

If you chose the DEFAULTS, you can type /usr/bin/vmware-config.pl to get the config done.

Yes, I did choose the default. . . and I did that.

---

### Post by llamakc on 2007-10-08
[https://help.ubuntu.com/community/VMware/Server?action=show&redirect=VmwareServer](https://help.ubuntu.com/community/VMware/Server?action=show&redirect=VmwareServer)

Is the how-to at help.ubuntu.com

BTW, did you run the patch? Are your kernel modules loaded?

---

### Post by ~~Tito~~ on 2007-10-08
Ok, I will try that guide. There was one with a patch but it was for another version.

---

### Post by llamakc on 2007-10-08
Good luck with it. Any particular reason you're going to use VMWare? I find VirtualBox ALOT easier to get up and running.

---

### Post by ~~Tito~~ on 2007-10-08
Virtual Box? No one told me about virtual box. ..  Do you have to pay for it? Or is it free like the server version?

---

### Post by ~~Tito~~ on 2007-10-08
Ok, I was looking for virtual box and I got it and tryed to install but when Ever i try it gives me the error to close synapatic or apptitude and they are both closed and when I run synapatic or apt get in the terminal i get this. . ```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```

What do I do. . .

```
A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package virtualbox needs to be reinstalled, but I can't find an archive for it.'
```
After I did what it said it gave me that. . . ^ in update manager. . .

---

### Post by shad0w_walker on 2007-10-08
You do what it tells you in the error message and run this command:

```
sudo dpkg --configure -a
```

---

### Post by rsambuca on 2007-10-08
Do exactly what it says!```
sudo dpkg --configure -a
```

---

### Post by ~~Tito~~ on 2007-10-08
I did but then. . . Just read i edited it..

---

### Post by ~~Tito~~ on 2007-10-08
Anyone???

---

### Post by rsambuca on 2007-10-08
Did you download the deb file, or use the repository method.  Also, did you follow the instructions for installing the required libraries first?> You will need to install some additional libraries on your Linux system in order to run VirtualBox - in particular, you will need libxalan-c, libxerces-c and version 5 of libstdc++.

And quit bumping your threads so quickly, it is very bad etiquette.

---

### Post by ~~Tito~~ on 2007-10-08
Anyone? Help me this is a huge problem. . .

---

### Post by ~~Tito~~ on 2007-10-08
> **rsambuca said:**
> Did you download the deb file, or use the repository method.  Also, did you follow the instructions for installing the required libraries first?

And quit bumping your threads so quickly, it is very bad etiquette.

Deb, how do I remove it?

---

### Post by shad0w_walker on 2007-10-08
Answer the question about deb or repo and stop bumping so much and you will probably get useful replies.

---

### Post by rsambuca on 2007-10-08
Did you install those extra libraries first?

---

### Post by ~~Tito~~ on 2007-10-08
I went here and it didn't mention anything about that.

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by shad0w_walker on 2007-10-08
It mentions is just under the downloads and the instructions on using the Virtual box repos. Read the damn instructions, almost everything has had very very clear instructions you just haven't bothered to read.

---

### Post by ~~Tito~~ on 2007-10-08
I don't see it. . . How do I remove it?

---

### Post by rsambuca on 2007-10-08
Read All The Instructions Before Posting Here Again.

---

### Post by ~~Tito~~ on 2007-10-08
. . . Lol, I thought that was only for Debian. How do I remove it. I want synaptic to work and update manager and apptitue and apt get to work.

---

### Post by rsambuca on 2007-10-08
I am trying to help you here, but you seem incapable of following instructions, reading instructions, or answering any questions that we ask.  I suggest you try the [virtualbox forums]("http://forums.virtualbox.org/") to get help.

Good luck.

---

### Post by ~~Tito~~ on 2007-10-08
I simply asked how to remove it, I get all these errors when I go in synaptic. This happened to me before but I cant find the thread in my started threads. It was a simple command that deleted any remnants of it. I am just asking for that command.

---

### Post by ~~Tito~~ on 2007-10-08
Ok, I cant find those librarys, I googled them but nothing. Where are they exactly? I have looked and nothing. .

---

### Post by Roaster on 2007-10-08
PEBKAC! Good grief!

---

### Post by ~~Tito~~ on 2007-10-08
WHAT??? People, listen. I don't know where to look for this kind of stuff, sheeesh!! You guys act like I know where to look and do. I googled I cant find it, if I do find it its irrelevant. . .

---

### Post by philinux on 2007-10-08
+1 Roaster FUBAR too.

---

### Post by ~~Tito~~ on 2007-10-08
What are you guys talking about?

---

### Post by rsambuca on 2007-10-08
I don't think I can stand back and watch these ID-ten-T errors any longer.

Please download this manual and read the section on installing in linux.

[http://www.virtualbox.org/download/UserManual.pdf](http://www.virtualbox.org/download/UserManual.pdf)

---

### Post by n3tfury on 2007-10-08
> **philinux said:**
> +1 Roaster FUBAR too.

aye, goosechicken.

---

### Post by philinux on 2007-10-08
The answer to all your questions are held within this thread if you would just read.

People have tried to help but you dont read the instructions or even follow them.

---

### Post by llamakc on 2007-10-08
I gave up and went for beer.

---

### Post by ~~Tito~~ on 2007-10-08
Yes Yes, I have gotten the manual, but I don't understand how to do it! Can some one simplify. . . Look if I am asking to much then just ignore but I need to make it simpler. . . I am not going to windows, I may not be able to pay attention because I have a migraine but I want this done with out me having to take aloooooonbg time to figure something out that was simple to begin with..

> VirtualBox uses a special kernel module to perform physical memory allocation and to
gain control of the processor for guest system execution. Without this kernel module,
you will still be able to work with Virtual Machines in the configuration interface, but
you will not be able to start any virtual machines.
  To be able to install this kernel module, you will have to prepare your system for
building external kernel modules. As this process can vary from system to system, we
will only describe what to do for systems we have tested
    &#8226; Most Linux distributions can be set up simply by installing the right packages.
      Normally, these will be the GNU compiler (GCC), GNU Make (make) and pack-
      ages containing header files for your kernel. The version numbers of the header
      file packages must be the same as that of the kernel you are using.
         &#8211; In newer Debian and Ubuntu releases, you must install the right version of
            the linux-headers**I dont know where to go to install or where to find it** and if it exists the linux-kbuild**the same for this** package. Current
            Ubuntu releases should have the right packages installed by default.**??/?**
         &#8211; In older Debian and Ubuntu releases, you must install the right version of
            the kernel-headers package.
         &#8211; On Fedora and Redhat systems, the package is kernel-devel.
         &#8211; On SUSE and OpenSUSE Linux, you must install the right versions of the
            kernel-source and kernel-syms packages.
    &#8226; Alternatively, if you built your own kernel /usr/src/linux will point to your
      kernel sources, and you have not removed the files created during the build
      process, then your system will already be correctly set up.
  In order to use VirtualBox&#8217;s USB support, the user account under which you intend
to run VirtualBox must have read and write access to the USB filesystem (usbfs).
  In addition, access to /dev/net/tun will be required if you want to use Host
Interface Networking, which is described in detail in chapter 6.3, Introduction to Host
Interface Networking (HIF), page 60.


My questions are in bold. . .

---

### Post by llamakc on 2007-10-08
That's the thing, Tito. If you follow the how-to your questions are actually answered because that is an important step of the installation.

Once again, WHAT howto have you decided to use? Give me the link please.

---

### Post by dz0004455 on 2007-10-08
i used automatix to install it, but that really screwed up my repositories

---

### Post by ryanVickers on 2007-10-08
> **rsambuca said:**
> I don't think I can stand back and watch these ID-ten-T errors any longer....

People still say that?! :p

Anyways, have you tried VirtualBox?  It's way faster, super easy to install and run, and...

---

### Post by ~~Tito~~ on 2007-10-08
Yes, but I cant seem to install it with out problems. Can you tell me the steps you used to installed it? Simplified please?

---

### Post by Beggar on 2007-10-08
Have you considered using windows?

Linux isn't for everyone, you need to be able to read instructions to use linux.

My 2 cents.

Just in case someone else is looking for help (Tito already stopped reading), 

```
sudo apt-get install virtualbox
```

---

### Post by ThrobbingBrain66 on 2007-10-08
Just so everyone is aware, I've reported this thread as needing to be closed.  It's run it's useful life.

---

### Post by ComplexNumber on 2007-10-08
> **ThrobbingBrain66 said:**
> Just so everyone is aware, I've reported this thread as needing to be closed.  It's run it's useful life.
don't be so harsh. not everyone has the same level of confidence with new ideas. maybe the OP can go back over some of the advice in the thread and be able to pick some suggestions up that he may have missed.

---

### Post by ~~Tito~~ on 2007-10-08
Listen, I have been running ubuntu just fine for about 6 months and havent even thought of replacing it. I have been reading. . . Also I have tryed that but it wonr work this is what it has been giving me ```
tito@TITOS-LAPTOP:~$ sudo apt-get install virtualbox
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package virtualbox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package virtualbox has no installation candidate
tito@TITOS-LAPTOP:~$ 


```.

I know what to do(kinda), and this has gave me a lot of problems. . . I hate windows, I am never going back. I can think straight now because my migraine went away because I am going to eat steak!:)

---

### Post by ThrobbingBrain66 on 2007-10-08
> **ComplexNumber said:**
> don't be so harsh. not everyone has the same level of confidence with new ideas. maybe the OP can go back over some of the advice in the thread and be able to pick some suggestions up that he may have missed.

While I generally agree with your assessment of confidence levels, I have to disagree overall.  the OP has refused to answer many questions or follow advice/instructions/howtos given to him.  The OP can still page through the thread for anything he missed while it is closed.

I guess we'll agree to disagree and I'll bow out not.  My apologies for the interruption.

---

### Post by ThrobbingBrain66 on 2007-10-08
> **~~Tito~~ said:**
> Listen, I have been running ubuntu just fine for about 6 months and havent even thought of replacing it. I have been reading. . . Also I have tryed that but it wonr work this is what it has been giving me ```
tito@TITOS-LAPTOP:~$ sudo apt-get install virtualbox
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package virtualbox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package virtualbox has no installation candidate
tito@TITOS-LAPTOP:~$ 


```.

I know what to do(kinda), and this has gave me a lot of problems. . . I hate windows, I am never going back. I can think straight now because my migraine went away because I am going to eat steak!:)

I think it's
```
sudo apt-get install virtualbox-ose
```

That's what's in the repos anway...

---

### Post by llamakc on 2007-10-08
virtualbox-ose is a Gutsy only package, right?

---

### Post by steveneddy on 2007-10-08
Um - did you look [here]("http://ubuntuforums.org/showthread.php?t=550438")?

It worked for me.

---

### Post by ~~Tito~~ on 2007-10-08
I got it guys, its working. . . Thanks for being patient. "Windows" welcome back(kinda).

---

### Post by Beggar on 2007-10-08
No, in 7.04 the package is virtualbox.

Someone with more patience is going to need to post for the 1 millionth time on this thread how to enable to other repositories. Its ok though, OP has been using linux for 6 months now. Although without codecs/etc. Im not too sure what shes been doing.

---

### Post by ~~Tito~~ on 2007-10-08
??? I am a dude. I installed linux-kbuild so I think I am ok right?

---

### Post by Beggar on 2007-10-08
> **~~Tito~~ said:**
> ??? I am a dude. I installed linux-kbuild so I think I am ok right?

Couple of things, first of all, a question mark(?) usually follows the question, its only placed before the question in other languages, see [Spanish]("http://en.wikipedia.org/wiki/Spanish_language"). 

As far as the second question, the joy of ubuntu is you can install whatever package you want to, and it shouldn't break anything. Unless you use that package to break something. I highly recommend against you finding a guide and using kbuild though.

---

### Post by ~~Tito~~ on 2007-10-08
I know that, I put the question marks in the beginning because I couldn't see how you wouldn't think I am a dude, (See my avatar).

Greetings from windows!! I am on it right now!! Ok, I get it guy. I know that. Thanks guys for the help!

---

### Post by BertP on 2007-10-08
> **dz0004455 said:**
> i used automatix to install it, but that really screwed up my repositories

I was considering using automatix for the install but could you elaborate on exactly how your repositories were screwed?

---

### Post by ryanVickers on 2007-10-08
*I* have never had a problem with it, but lots of people say it really messes things up, bad!

---

### Post by Beggar on 2007-10-08
I cant seem to find the usual sticky thread, but here is the relevant post about it:

[http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)

---

### Post by ~~Tito~~ on 2007-10-08
What if there is no sound in Virtual Box? I enabled it but there is none. . .

---

### Post by Beggar on 2007-10-08
Please confine your questions to one thread, now your spamming the forums and not just your own thread.

As far as sound not working, Im going to go out on a limb here, is the guest OS muted? If not, is Ubuntu muted? Do you have speakers? If so are they plugged in? Is the sound turned up to a reasonable level on them?

---

### Post by Incense on 2007-10-08
You will also want to make sure that your Guest OS is not using sound (in Videos or Music players).

---

### Post by ~~Tito~~ on 2007-10-08
Opps, sorry bout that. No sound in ubuntu is just fine, yes I have speakers and they are built in my laptop.  Any other reasons?

---

### Post by ~~Tito~~ on 2007-10-08
> **Incense said:**
> You will also want to make sure that your Guest OS is not using sound (in Videos or Music players).

Nope nothing is using my sound. What could it be then?

---

### Post by ~~Tito~~ on 2007-10-09
Never Mind, I had to enable it to ALSA! I officially declare this thread SOLVED! Thanks guys for bing sooo patient and soooo understanding ;).

---

### Post by Incense on 2007-10-09
> **~~Tito~~ said:**
> Nope nothing is using my sound. What could it be then?

Have you installed the Guest Add-on's?

---

### Post by ~~Tito~~ on 2007-10-09
Its fixed, though the sound quality is poor.

---

