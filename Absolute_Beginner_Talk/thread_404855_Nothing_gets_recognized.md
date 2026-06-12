---
title: "Nothing gets recognized"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by Billium on 2007-04-09
OK, I am one week into this ordeal of learning Ubuntu.

OS is installed 6.06 for Athlon 64.

I tried to get pictures from my camera, won't regcognize.
I tried to use card reader on the memory stick, won't recognize.
Have been reading the forums all day. 

This is what I don't understand. When I go into synaptic package manager to search for programs or software or "tarballs", I can't understand what to download.

It's all in computer speak. I keep going to absolute beginner, but if that's absolute beginner, then I'm absolute ignorant.

Can I find a site that will tell me where to at least buy a book that will take me step by step thru the process to do anything?

By the way, I like the idea of a decision tree. That I can understand. I seem to remember that the binary system is actually based on a decision tree of 0 and 1.
I'm not complaining just frustrated.

Thanks for listening.

---

### Post by Billium on 2007-04-09
Feel somewhat like an idiot.

Found a thread that helps me and I will go back and continue to learn.

It's all there, it's just sometims too hard to find.

---

### Post by aysiu on 2007-04-09
This may help you with some stuff:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by tonyr1988 on 2007-04-09
First, sorry you're having so many problems. I guarantee, though, that if you stick with it and get these stupid hardware things fixed, you'll have problems going back. :)

Some basic questions to get some more information to help you out:

-You have an Athlon 64. Did you install the i386 version of Ubuntu or the AMD64 version? Both will run on the 64-bit processor. You will have more problems getting things configured in the AMD64 version. I have an Athlon 64 and personally use the i386 version, since I don't do a whole lot of multimedia editing or intense CPU things.

-Is there any particular reason you chose the 6.06 (Dapper Drake) version? It is generally considered a more stable version, but I personally feel that Edgy (6.10) has better hardware detection, and I've heard good things about the upcoming Fiesty (7.04). You may want to consider using a different version if you're not too far into it.

-What is the camera you have? What kind of card reader do you have? Does anything come up when you plug them in?

-Just to make sure...you mean the Sony Memory Stick, right? (I've heard people refer to jump drives as memory sticks)

Also, how you download software will depend on what you're installing. In Synaptic, hit the Search button at the top and type the program you're looking for. If you find it, check the box and hit Apply at the top. Viola!

If it's not in there, it could be harder. If I were you, I'd work on getting all the hardware detected first, and then worry about software (software will generally be easier).

There are great introduction guides for [Edgy]("http://ubuntuguide.org/wiki/Ubuntu_Edgy") and [Dapper]("http://ubuntuguide.org/wiki/Ubuntu_dapper"). Take particular notice on these sections:

> # 1.4.1 How to add extra repositories
# 1.4.3.2 How to install Automatix2 on Ubuntu, Kubuntu, and Xubuntu
1.6.2.1 How to install Firefox32 in AMD64 (if you use the AMD64 version)
# 1.6.4.1 How to install Multimedia Codecs

Feel free to keep asking questions as you please. Also, be aware that many common ones are already on the forums (there's a search in the upper-right-hand corner) and there's a [good wiki]("https://help.ubuntu.com/community/") that also covers common problems.

Finally, the decision tree is an idea in the working. Once you feel comfortable working with Ubuntu, feel free to contribute! :)

(Sorry for being so long-winded)

---

### Post by Billium on 2007-04-09
I downloaded the 6.06 because ubuntu.org said it was for AMD Athlon 64, and that is my cpu.

My camera is a Nikon D50. I entered it as a search term and got no packages.
Entered 'card reader" and got several options and have downloaded them.

I have no attachment to any particular version and am open to suggestions.

I have tried several times to identify my hardware. I still don't know what MB I have.

I am learning. I am going to the suggestion on the previous post to see if I can learn anything.

I'll get back to you.

Thanks.

---

### Post by kvonb on 2007-04-09
> **Billium said:**
> I downloaded the 6.06 because ubuntu.org said it was for AMD Athlon 64, and that is my cpu.

Hmm, maybe that wasn't the best advice!

The version you have is the 64bit version, and it is a lot harder to use from what I've read!

It's more of a "development" version and even I wouldn't touch it, and I've been using Ubuntu for nearly 2 years now!

I would recommend downloading the standard i386 version, you don't **NEED** the AMD 64 version, it is an option that makes more use of the AMD64's special functions.

Your camera should simply pop-up on the desktop whenever you insert it into a USB port, no extra software is needed.

I would suggest either downloading and installing 6.06 i386 version, or better still, wait a week or so for the brand new 7.04 release and install that.

The 7.04 (Feisty) version is really nice and has a lot more features and is easier to use, however it is still a BETA release and might not be a good idea for you until it is actually an official release.

Regards, Kev :)

---

### Post by Billium on 2007-04-09
Can i just do an update? Or do I have to go thru the process of downloading an ISO and burn to disk and reinstall.

I would like to learn the command line, can I do it thru that?

Thanks

---

### Post by kvonb on 2007-04-09
> **Billium said:**
> Can i just do an update? Or do I have to go thru the process of downloading an ISO and burn to disk and reinstall.

I would like to learn the command line, can I do it thru that?

Thanks

Unfortunately in order to change to the standard 32 bit version you will have to download and re-install from scratch.

---

### Post by Billium on 2007-04-09
Thanks. 

I guess I'll just sit back for a while and play with what I have until 7.04 comes out. If I'm going to change to 32bit anyway, it wouldn't hurt to learn what to do on this OS so that I don't hurt the new one.

How do I find out when it is released?

And thanks for the help.

---

### Post by kpkeerthi on 2007-04-09
[http://help.ubuntu.com](http://help.ubuntu.com)

---

### Post by Billium on 2007-04-10
OK.

I have been doing a lot of reading on ubuntu.com. It says that I can update to 6.10 from 6.06 LTS with the command

gksu "update-manager -c"

Aren't they both 64bit systems?

Should I just do this, wait for 7.04, or go back to i386? Which I think is a 32bit OS?

---

### Post by BaffledMollusc on 2007-04-10
You can certainly upgrade from 6.06 to 6.10, that's no problem. However if your 6.06 install is a 64-bit version of the OS, then the upgraded 6.10 will also be 64-bit.

There are a number of reasons to use a 64-bit OS, but for desktop users the only real reason at the moment would be if you have 4 gigabytes of memory or more. You need a 64-bit OS to use that much memory (loosely speaking). If you haven't got that much memory in your computer, there's no real reason to use 64-bit. 

In fact, all things considered, I would advise against using a 64-bit version of the OS, since the software / driver support is not as good as for the 32-bit versions.

Personally, if I were you, I would wait a couple of weeks until 7.04 comes out, and download the 32-bit version of that. That should hopefully solve a lot of your problems.

Edit: Oh, one more thing. Regarding your first post, I'm sorry if a lot of the advice people have been giving you is overly technical. The problem is, after doing some things for so long it's easy to forget what's obvious to new users and what's not! If you don't understand what someone is saying, please feel free to say you don't understand a word of it and ask for a better explanation!

---

### Post by Maestro23 on 2007-04-10
Upgrade to Edgy: [https://help.ubuntu.com/community/EdgyUpgrades?highlight=%28upgrade%29](https://help.ubuntu.com/community/EdgyUpgrades?highlight=%28upgrade%29)

---

### Post by Billium on 2007-04-10
Thanks for the info alll.

I think I will wait and get the 32-bit 7.04 when it comes out. I only have 1GB of RAM and am using onboard graphics. I'll update both before I go to the 64-bit, I need a shallow learning curve anyway.

Thanks again.

---

### Post by Maestro23 on 2007-04-10
> **Billium said:**
> Thanks for the info alll.

I think I will wait and get the 32-bit 7.04 when it comes out. I only have 1GB of RAM and am using onboard graphics. I'll update both before I go to the 64-bit, I need a shallow learning curve anyway.

Thanks again.

Some links to help you learn the Ubuntu way:

Useful Links:

Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

Restricted Formats(mp3, playing DVD, etc..): [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Managing Repositories: [https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

Community Docs: [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

CommandLine Beginners: [http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

Basic Commands: [https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands)

LinuxCommand.org(Commands & Linux File Structure): [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Using the Terminal: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

Top 10 Commands for noobs: [http://blog.lxpages.com/2007/02/25/top-10-linux-commands-for-newbies/](http://blog.lxpages.com/2007/02/25/top-10-linux-commands-for-newbies/)

Graphic Card Drivers
ATI supported cards: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)
Installing ATI Drivers: [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)
Installing Nvidia Drivers:[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
Envy Script(ATI/Nvidia): [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Super Grub Disk: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Getting rid of junk: [http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)



Welcome and Good luck.

---

### Post by Billium on 2007-04-12
Been doing some more reading and am trying to do: Adding support for restricted formats.

Followed instructions. Got this error:  Can't find  "gstreamer0.10-pitfdll"

Went back in Synaptic Package Manager, added Multiverse and Universe, and did a search. No luck.

Can't you just leave those two choices checked all the time or do I have to go back in each time and recheck them?

I know that's two questions.

Thanks.

---

