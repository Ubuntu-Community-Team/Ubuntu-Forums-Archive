---
title: "Basic help for a newbie learning from the tutorials above."
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by SouthernPott on 2007-11-18
So far I have set up this computer as a dual boot with WinXP and another older computer with only Ubuntu 7.10 and a wireless card.  Both work great and internet connections are fine.

Now I am trying to dig into Ubuntu and learn how to use the terminal.  I have started with the tutorials posted by starcraft.man in the stickies at the top.  I am running into problems with terminology and instructions not being quite as intuitive as I would like.  

An example is using the "su" command in the terminal (one of the practice exercises)  When asked for my password, I type in the only password I know and I get back an error message something to the effect of "Authentication Denied Sorry".  Where do I find my password if it is not the same thing as the one I use for logging on and for the "sudo" command?

One of the basic projects was to write the script for "Hello World" in the Gnome editor.  I managed to do this and managed to save it as "my_script".  Then I was supposed to be able to create a new "file" or "directory" called "bin" to move it to which I attempted to do.  Once it was moved to this place I was suppose to be able to type "my_script" when I open the terminal and then it reads "Hello World".  Anyway, somewhere along the way I must have made a mistake.  I can find the "my_script" file but it does not work as it is supposed to in the terminal.

Further along in my reading I was trying the "aliases" tutorial.  It said to find and open the ",bash_profiles" file which I don't have and enter the practice codes at the bottom of the file.  I finally found something similar in ",bashrsc" (I think that was it) which said it would be better to create a new file ".bash_aliases" rather than adding aliases at the bottom of the ".bashrsc" file.  I also found mention of the .bashrsc file at the bottom of the page of the tutorial I was reading after I had already been attempting to find the .bash_profiles file and do the exercise.  Is this a change from 7.04 to 7.10 and the tutorial just isn't caught up?  Now I have two .bash_aliases files, one .bash_aliases and one ~.bash_aliases I think and don't know what to do with either of them.

Evidently the learning curve is going to be steep for me.   I can read the lexicon and interpret the terms I don't know but I seem to find practice exercises that are not quite as direct as the author intends, at least for me.  Is this normal for someone with no Linux background?  Am I supposed to be learning by trial and error rather than repetitive practice?  I hate to come here and ask for a code each time I find something new I want to try.  Seems I should be learning to do it myself somewhere along the way.

---

### Post by MaximusTG on 2007-11-19
Well, basically while learning linux, I have learned that "google is your friend". Whenever you run across something you don't understand, search around google, and this forum for related topics. And don't be afraid to try something. Some of your questions:

if you type su in a terminal, it will ask you for the root's password. But that isn't setup as default in Ubuntu. So you type sudo su to become root. Why is that? Well:

su requires the root password OR root privileges to be executed. 

So if you run sudo su, you use sudo, which takes your password, to execute su with root privileges. 

If you make a shell script in linux, your first have to make it executable before you can run it. You do a chmod +x yourscript. 

To call this script you either enter it's entire path, i.e. if it was located in your home directory, you would type:  /home/yourname/yourscript  
You can also move it into a directory in your PATH. Your PATH contains a list of directories that are searched through, when you enter a command. 
To add, for example the folder /home/yourname/bin to your path, edit the .bashrc file, which is located in your home directory, and add a line saying 

export PATH=$PATH:/home/yourname/bin

As you said, .bashrc says that it's better to edit .bash_aliases to add aliases, 

```

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

```

See those #'s ? that means that that code is commented out. It is not executed. So when you make a .bash_aliases file, remove the comment from the above section like this:
```

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

```
That will make the .bashrc file check for .bash_aliases and do what's in it.

---

### Post by SouthernPott on 2007-11-19
Thanks for the reply.  I forgot to mention that the tutorials I was trying were in linuxcommand.org. 

In the practice tutorial it asked for me to use only the su command which is for "superuser" or root.  From what you are saying it would be impossible for me to do this without using the sudo su command.  So why show it in the tutorial?

I left out a detail on the Hello World script.  It did ask me to used the chmod command and I did do this correctly I think.  I am not using Linux right now so I can't trace the path but what you are saying makes sense.  It is just that from the tutorial I was getting the impression that once I saved the script as "my_script" and followed the directions, it would be executed from a newly opened terminal just by typing in   my_script.  

Your .bash_aliases explanation makes the most sense and I got the feeling when I was doing it that a code would be required inside the file so that .bashrsc would read it.   I did figure out from the tutorials that anything with # or ## are just comments and not operational so that helped follow some of what they were showing.  I am assuming that in previous versions of Ubuntu there must have been a .bash_profiles file already set up that had this code.  Was I correct that there is not a .bash_profiles file in 7.10?

I really like the idea of Linux and have been following it for a few years, just too afraid of trying it.  Finally giving it a shot with 7.10 and I guess what I am looking for is a beginner's guide with tutorials that start from the beginning with repetitive practice commands and explanations.  From what I have been seeing and from what you are saying it isn't quite that straight forward and I should just prepare myself to ask questions every step of the way.  I have found the search function in Ubuntu forums to be the most useful when I actually have a problem/issue question.  It is the times like this when I am just practicing, no real issue to resolve, that I am unsure of what questions to ask.

Again, thanks for the help.

---

### Post by PeterJS on 2007-11-19
> **SouthernPott said:**
> Thanks for the reply.  I forgot to mention that the tutorials I was trying were in linuxcommand.org. 

In the practice tutorial it asked for me to use only the su command which is for "superuser" or root.  From what you are saying it would be impossible for me to do this without using the sudo su command.  So why show it in the tutorial?


Ubuntu is actually quite unique in the respect that it doesn't have a root password. That would work for every other distribution out there. Odd thing is I just realized that I never set a root password on my machine since I did a wipe and upgrade from 6.10 to 7.04, and hadn't even thought about it. I guess this backs up the rational given that sudo is enough to get the job done.

---

### Post by SouthernPott on 2007-11-19
Ubuntu is actually quite unique in the respect that it doesn't have a root password. That would work for every other distribution out there. --PeterJS

Thanks Peter.  From your comment I gather that from one distro to the next most of the commands are the same but in the case of the "su" command it is deprecated to "sudo su" in Ubuntu.  I didn't think about that when I first started looking at  [www.linuxcommand.org](www.linuxcommand.org), assuming instead that what I was looking at directly applied to Ubuntu.  So I need to be careful when doing the practice tutorials.

Would this be why I didn't find a .bash_profiles file in Unbuntu? Because it never existed in Ubuntu rather than being removed in only 7.10.

Here is an easier question.  When posting on these forums, how do I take a comment from your post and include it in mine like you did where it is boxed in and shows me as the writer?  I have noticed people doing this but I don't know how other than copy/paste and it would certainly be much more helpful in following and commenting during a discussion.

---

### Post by SouthernPott on 2007-11-19
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

Is this link a better place for going step by step?

---

### Post by PeterJS on 2007-11-19
> **SouthernPott said:**
> 
 So I need to be careful when doing the practice tutorials.


There are enough small variations over all distributions it's hard to find a guide that is comprehensive, complete, and universal. But don't lest that discourage you +90% of things will be the same, you ran in to a discrepancy early it happens. Don't be afraid to ask, a lot of the time the answer will be, oh yeah forgot about that here's what's going on.

> 
Would this be why I didn't find a .bash_profiles file in Ubuntu? Because it never existed in Ubuntu rather than being removed in only 7.10.


I just went and looked, and I do have a .bash_profile, I carried my home directory forward from 7.04 so it must be something new.
EDIT: also it's .bash_profile with no s on the end that's also a likely possibility. Try in your home directory
```

ls -a | grep bash

```

That will list all files, including hidden files with bash in the name.

> 
Here is an easier question.  When posting on these forums, how do I take a comment from your post and include it in mine like you did where it is boxed in and shows me as the writer?  I have noticed people doing this but I don't know how other than copy/paste and it would certainly be much more helpful in following and commenting during a discussion.

In the lower right corner there of each post there is a button that says quote, clicking on that will start a new reply with the entire post it was attached to quoted, you can trim the text down from there. And related to that here's a guide to all the vB code markup the forums use.

[http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

> **SouthernPott said:**
> [http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

Is this link a better place for going step by step?

It certainly looks like it covers pretty much everything but command line usage, I can't tell you much about the quality as it's a bit large to review in one sitting. The ubuntu community generally does a pretty good job with there guides though.

---

### Post by RedSquirrel on 2007-11-19
Here's a link for information on sudo:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You might want to have a look at some of the guides at:

[http://tldp.org/](http://tldp.org/)

Good luck. :)

---

### Post by SouthernPott on 2007-11-19
> I just went and looked, and I do have a .bash_profile, I carried my home directory forward from 7.04 so it must be something new.
EDIT: also it's .bash_profile with no s on the end that's also a likely possibility. Try in your home directory
Code:

ls -a | grep bash

That will list all files, including hidden files with bash in the name.

I didn't have a .bash_profile file but I did find .bash_aliases and .bash_aliases~.  On the bright side I did get to use the rm .bash_aliases~ command and it worked.  Using the command from your post .bash_aliases~ no longer shows.

Back to the su password thing.  Since that is the root  / I most likely shouldn't or won't be doing anything at that level so I shouldn't worry/bother with it, correct?

Now a partitioning problem.  Since I am dual booting with XP when I did the setup with Ubuntu I selected guided partitioning in the free space which in my case was about 55Gb.  XP is about 25Gb and there is also a small FAT16 partition of about 32mb on the XP side.  Then I set the Ubuntu partition of about 10 Gb and a 2Gb SWAP space.  By doing this I created 4 primary partitions which then made the rest of the space unusable.

I have read some of the guides showing a large "SHARED FILES" partition and also a partition on the Ubuntu side called /home I think for putting personal settings so that with each new edition of Ubuntu it is possible to just format the main Ubuntu partition for a new install and not lose all my settings.  Is that unusable space recoverable by repartitioning the main Ubuntu partition and then making a logical drive rather than a primary drive?

Or do you just do an upgrade each 6 months and everything pretty much stays the same anyway?

---

### Post by SouthernPott on 2007-11-19
```
malcolm@home-desktop:~$ ls -a | grep bash
.bash_aliases
.bash_aliases~
.bash_history
.bash_logout
.bashrc
malcolm@home-desktop:~$ rm .bash_aliases~
malcolm@home-desktop:~$ ls -a | grep bash
.bash_aliases
.bash_history
.bash_logout
.bashrc
malcolm@home-desktop:~$ 

```

---

### Post by PeterJS on 2007-11-20
> **SouthernPott said:**
> 
Back to the su password thing.  Since that is the root  / I most likely shouldn't or won't be doing anything at that level so I shouldn't worry/bother with it, correct?

No it is rather important, the way the linux security is set up anything outside of the home directory requires elevated privileges, such as installing new software, changing any system configurations.

> 
Now a partitioning problem.  Since I am dual booting with XP when I did the setup with Ubuntu I selected guided partitioning in the free space which in my case was about 55Gb.  XP is about 25Gb and there is also a small FAT16 partition of about 32mb on the XP side.  Then I set the Ubuntu partition of about 10 Gb and a 2Gb SWAP space.  By doing this I created 4 primary partitions which then made the rest of the space unusable.

I'm not sure if I got the right impression but I'm seeing this:
```

+-----------------------+-+--------------+--------+
|       XP 25gb         |*| Ubuntu 10gb  |  2gb** |
+-----------------------+-+--------------+--------+

```
*Fat16 not big enough to bother with
** swap

I'm not sure how this relates to the 55gb figure you mentioned.


> 
I have read some of the guides showing a large "SHARED FILES" partition and also a partition on the Ubuntu side called /home I think for putting personal settings so that with each new edition of Ubuntu it is possible to just format the main Ubuntu partition for a new install and not lose all my settings.  Is that unusable space recoverable by repartitioning the main Ubuntu partition and then making a logical drive rather than a primary drive?

Or do you just do an upgrade each 6 months and everything pretty much stays the same anyway?

Yeah, having / and /home on separate partitions makes the wipe and re-install upgrade method a lot easier. I've used a couple of different methods to upgrade, going from 6.10 to 7.04 I backed my home directory up to an external drive, wiped the whole partition, installed 7.04 and then restored my back up home directory. Going from 7.04 to 7.10 I just edited my sources.list to use the gutsy repositories instead and then upgraded all my packages, this has advantages like saving all of your settings and keeps all your software installed, but has the disadvantage of not changing any settings to use new defaults and not everything migrates automatically, in my case I had to manually un-install Beryl and install Compiz.

As for setting up shared files, I used a second driver formatted fat32 for a long time, for a long time that was the easiest to set up. The ntfs-g3 driver has gotten to the point of being very usable and stable, in light of that my current set up is a large windows partition with a symlink between the directory I keep my data in and a directory named windata in my home directory.

If you've got a place to back your home directory up to I'd suggest sitting tight on what you've got now, and changing around the partitions if you want to when installing Hardy.

---

### Post by SouthernPott on 2007-11-20
> **PeterJS said:**
> No it is rather important, the way the linux security is set up anything outside of the home directory requires elevated privileges, such as installing new software, changing any system configurations.

After rereading the tutorials and a little more practice I see where my mistake was in my statement/question.  By default the terminal opens in the home directory.  Any software installation/system changes I have done have been through the System>Administration menu rather than the terminal so the change is kind of transparent to me.  Now I see that this is what the sudo su command enables in the terminal.  

> 
I'm not sure if I got the right impression but I'm seeing this:
```

+-----------------------+-+--------------+--------+
|       XP 25gb         |*| Ubuntu 10gb  |  2gb** |
+-----------------------+-+--------------+--------+

```
*Fat16 not big enough to bother with
** swap

I'm not sure how this relates to the 55gb figure you mentioned. 

I think the 55gb was the approximate size of the open space after XP was installed.  Your diagram is correct so I have ~43gb of what is termed "unusable space" on the disk after the Ubuntu and swap partition setup.  Honestly, it isn't that big a deal as I don't save much and I have an older 8gb drive that I will probably put back into this computer for backups.  I think at this point my best course is to keep experimenting with Ubuntu and get a more comfortable feel for it.  My concern was in having my settings saved to slide over into the next version but the worst case is I start over from scratch.  


I finally found the .bash_profile file.  Something I was reading referenced /usr/share/doc/bash/bash-doc/examples (or something close to that) so I started looking in Synaptic for it.  Found "bash-doc" and it had the _profile and _aliases files.   This is one of the things I have been having trouble with.   Does it exist and I have to find it or do I have create it from scratch?  If it does exist do I make the changes in the terminal or do I edit in Gnome-editor?  

Thanks for the help.  I am sure I will be back with more questions often.

---

### Post by PeterJS on 2007-11-22
> **SouthernPott said:**
> 
I finally found the .bash_profile file.  Something I was reading referenced /usr/share/doc/bash/bash-doc/examples (or something close to that) so I started looking in Synaptic for it.  Found "bash-doc" and it had the _profile and _aliases files.   This is one of the things I have been having trouble with.   Does it exist and I have to find it or do I have create it from scratch?  If it does exist do I make the changes in the terminal or do I edit in Gnome-editor?  

Thanks for the help.  I am sure I will be back with more questions often.

There are a bunch of things that reside in /etc, most of them configuration related, but the one that's pertinent to the discussion at hand is /etc/skel/, which is the skeleton from which new users are home directories are created. When a new user is created /etc/skel/.bashrc is copied to their home directory. /etc/skel/.profile has comments in it to the effect that it is the default .bash_profile, and will be used if ~/.bash_profile does not exist, and that bash-doc contains more information and examples that will be installed in /usr/share/doc/bash/examples/startup-files.

As to why you don't have a .bash_profile it looks like 7.04 and previous used the same copy setup for .bash_profile as is currently used with .bashrc, I say this because the only difference between my ~/.bash_profile and /etc/skel/.profile are the comments. So to set up a custom .bash_profile copy the profile given in /etc/skel/.profile and work from there.

And for .bash_aliases it's not that important unless you plan on setting up command aliases, I haven't and don't have a .bash_aliases, and even then it's not strictly required as you can define aliases at the bottom of your .bashrc and have it work exactly the same.

And to beat the partitioning dead horse one last time, when Hardy comes out I'd suggest copying everything in your home directory, don't forget the hidden files those are the important ones, to another partition (possibly on that 8gb drive), wipe all the (ubuntu) partitions and rebuild the whole lot using all the free space, with separate partitions for / and /home/ to make upgrading to 8.10 smoother. I've been gentoo free 2 years now, but I've still have a bit of ricer left in me, getting your swap partition as close to the front of the disk as possible will get you slightly faster access speeds on your swap, it's minimal, but it's not hard to set up, so why not put it first.

---

### Post by SouthernPott on 2007-11-23
Honestly, the more I dig into it, the more I think I need to leave it alone unless I have problems.  I have been looking at Ubuntu from the wrong perspective and expecting to do things in it that I could never do in WinXP.  What I should have been thinking was can I set up a computer with Ubuntu that meets or exceeds my expectations with WinXP.  It more than does that.

I got the wrong impression from the tutorials I think, not their fault.  I was putting too much emphasis on the importance of learning the content shown rather than the context and the idea that things can be created, fixed, or tweaked from the command line.  

Thanks for the tip on the partitions.  I wondered about the SWAP being in front of the main Ubuntu partition rather than behind it.  I was going by the graphs shown on the pyschocats website.  Still need to do some reading up on that too.  Will definitely wipe that partition when I do the upgrade, maybe the whole thing, XP and all.  I have noticed that the XP side seems to run much better since I started over.  

On XP I have Norton 360 for my firewall and virus scanner.  I run Spybot, Ad-aware, and CCleaner as well, all manually, a couple of times a week.  I know in Ubuntu the setup is different but I don't quite understand why.  The iptables act as the firewall and I used Firestarter to look at changing any settings but left it as is.   I noticed in Firestarter that I can create rules (if I knew what I was doing) and that there is a whitelist and blacklist for outgoing but I also noticed when running a Shields Up scan from Gibson Research that everything was showing stealthed and no problems.   Are the default settings fine?  Is there a need for running a virus package and if so what package?

Mostly, it seems to me is that I spend a lot of time and a little bit of money maintaining the XP side.   Ubuntu doesn't look like this will be required.  What happens to the internet history, temp files, or usual junk that seems to build up in Windows?

---

### Post by PeterJS on 2007-11-23
> **SouthernPott said:**
> On XP I have Norton 360 for my firewall and virus scanner.  I run Spybot, Ad-aware, and CCleaner as well, all manually, a couple of times a week.  I know in Ubuntu the setup is different but I don't quite understand why.  The iptables act as the firewall and I used Firestarter to look at changing any settings but left it as is.   I noticed in Firestarter that I can create rules (if I knew what I was doing) and that there is a whitelist and blacklist for outgoing but I also noticed when running a Shields Up scan from Gibson Research that everything was showing stealthed and no problems.   Are the default settings fine?


It's the difference in paradigms once again, under windows you run a firewall that closes everything that you don't explicitly open because you never know what's accessible, so it's better to err on the side of caution. Ubuntu does come with iptables installed, but that's only because nobody ships a linux kernel with out it, it doesn't take up that much disk space (the whole kernel weighs in at about 1.7 meg), it incurs no overhead when set no to do anything. The default settings for iptables is to do nothing, and this is perfectly safe because Ubuntu has no services listening on the network, so there's nothing to protect. So you only need a firewall if you explicitly install things like samba, nfs, etc that work over the network that you don't want the whole world to see, and even then if you're behind a router, you'd only need the firewall if you didn't trust the rest of the local network.

> 
 Is there a need for running a virus package and if so what package?


This one's a bit more contested, there have only been a couple hundred linux viruses ever, as opposed to hundreds of thousands for windows, so to say there are no linux viruses isn't strictly true, but it's a safe and practical assumption to make. There are anti-virus packages for ubuntu, such as clamAV, but there are currently no defs available for linux viruses, as there aren't currently any known to be in the wild. The unix security model also plays in to this, on windows everybody runs as admin, so getting a user to run something gives complete control of a machine, where as on linux, if a linux user runs something malicious the worst it can do is mess up there home directory, or run programs as that user. This gets back to sudo, if you ever get prompted for your password when you aren't expecting it, that's a pretty good warning that something fishy is going on. Theoretically a malicious program could lie in wait for the user to do something with sudo, and then ride coat tails on the authorization time frame, but I've never heard about this idea discussed beyond the realm of wild speculation (like this).

> 
Mostly, it seems to me is that I spend a lot of time and a little bit of money maintaining the XP side.   Ubuntu doesn't look like this will be required.  What happens to the internet history, temp files, or usual junk that seems to build up in Windows?

Most programs are pretty good about cleaning up after themselves in /tmp, sometimes they're too good about it, Ark (kde program for extracting compressed files) I'm looking at you. But, even if the applications themselves don't do a good job cleaning up after themselves, /tmp is tmpfs which is a pretty clever scheme that amounts to the file system residing entirely in RAM, but not taking up any more space than needed, so it gets destroyed and recreated every time you reboot. Firefox's caching behavior is the same on windows and linux, and I can't speak authoritatively about other browsers. Ubuntu also doesn't have the registry to build up registry cruft and junk in, it's got /etc to hold configuration stuff the only things that get put in /etc were put there by the package manager so it knows to remove it, or was put there by the user, which they should know it's there and remove it if they feel they need to. This is the differnce between remove, which uninstalls the program but leaves it's configuration data in case you ever re-install it, and completely remove which does just what it says.

---

### Post by SouthernPott on 2007-11-24
I assumed it was pretty secure as is from what I had been reading but I feel better about it now.  Wish I had given Linux a try a few years ago when I first heard about it so I wouldn't be so far behind.  Still lost on a lot of the terminology and interactions but the construction seems so much more logical the more I look I at.  

Outside of not understanding what I am doing with the terminal, it has run very well.  Minor hiccups with deciding which applications to run for certain things like the DVD player but all in all pretty easy. 

The biggest problem I have run into (in my opinion) is switching back and forth between XP and Ubuntu.  I have to hit the auto adjust buttons on the monitor because when it is aligned correctly in one OS it is off about 1cm in the other OS, either to the right or left depending on which OS was the last one used.  So I have to push two buttons to reset it.  Same thing with the speaker volume. My normal settings in XP are too low in Ubuntu and my normal settings in Ubuntu are too loud in XP.   I saw a post from someone regarding the issue of the monitor from a few weeks ago and I used the terminal to get the numbers for my monitor but it got a bit complicated for me.  I imagine the speakers will be about the same.  At some point in time I will figure out how to set them both correctly on bootup and it will save those settings for Ubuntu while reverting to the correct settings for XP, at least until I give up XP entirely.

On top of learning for me I am trying to learn for the neighbor's children.  We refurbished an old desktop HP and added a wireless card so they can use my internet connection for school projects rather than having me download and print stuff for them.  It had Win98 on it and no reinstall CD so after I got the hang of putting it on this one I reformatted their hard drive and put Ubuntu on it. It works great and the kids have an internet connection in their home now but I haven't felt like I could tell them how to really get into it and learn to make it better/do what they want.  I am getting a little more comfortable with it though and hopefully one of the kids will catch on faster than me and start telling me how to do things in the near future.

Again, thanks for all the help and information.

---

