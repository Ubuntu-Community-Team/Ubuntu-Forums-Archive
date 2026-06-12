---
title: "Installing Java runtime environment"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by Pai on 2007-02-16
I need to install jre:
[img]http://img235.imageshack.us/img235/1928/untitledzq6.png[/img]

So I looked around for instructions on doing so in Dapper, and found the following:

 >    * Navigate to [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp) 

Choose "Java Runtime Environment (JRE) 5.0 Update 10" and click on "Download"
Accept License Agreement 
Download the "Linux self-extracting file"

    * Install the required tool : 

sudo apt-get install java-package

    * Create the Ubuntu package : 

fakeroot make-jpkg jre-1_5_0_10-linux-i586.bin

    * Install the resulting package : 

sudo dpkg -i sun-j2re1.5_1.5.0+update10_i386.deb


So I followed those instructions (replace **jre-1_5_0_10-linux-i586.bin** with the newer **jre-6-linux-i586.bin ** that I downloaded.), but ran into trouble creating the Ubuntu package:

karl@karl-desktop:~$ sudo apt-get install java-package
Reading package lists... Done
Building dependency tree... Done
java-package is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
karl@karl-desktop:~$ cd Desktop
karl@karl-desktop:~/Desktop$ fakeroot make-jpkg jre-6-linux-i586.bin
Creating temporary directory: /tmp/make-jpkg.XXXXhYHkGg
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2 sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sd k.sh
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to de fault (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to de fault (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to de fault (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to de fault (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to de fault (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to de fault (native compilation)

No matching plugin was found.
Removing temporary directory: done
karl@karl-desktop:~/Desktop$


So, are these faulty/outdated instructions? Or am I simply doing something wrong.

Thanks.

PS. Can I easily change the name of my computer, so that the terminal says karl@<new name>: ?

---

### Post by timlewis242 on 2007-02-16
Do yourself a favor and download and install "Automatix". Among other things, it will install that for you.

---

### Post by taurus on 2007-02-16
Looks like you need to install gcc compiler first.

```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by meng on 2007-02-16
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)
you will have to enable extra repositories, it's a link in there

---

### Post by Maestro23 on 2007-02-16
I'm running 6.10, but you should be able to get java from the Ubuntu repositories via Synaptic(GUI) or apt-get(command line).  Will be easier on you.

Open up your Synaptic package manager and search for "java".

You might have to enable extra repositories to get it though.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by Pai on 2007-02-16
> **timlewis242 said:**
> Do yourself a favor and download and install "Automatix". Among other things, it will install that for you.
No thanks. I'd still be running XP if I wanted that.

@Taurus, I installed the compiler, but am still having the following problem:

karl@karl-desktop:~/Desktop$ fakeroot make-jpkg jre-6-linux-i586.bin
Creating temporary directory: /tmp/make-jpkg.XXXXddG4US
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done
karl@karl-desktop:~/Desktop$


More when I return from class.

---

### Post by meng on 2007-02-16
Repositories - trust us, it's the Ubuntu way.

---

### Post by timlewis242 on 2007-02-16
After years of exploring Linux, I've come to conclusion that there is no honor in fighting with software or hardware to make it work. In fact, one of the reasons I'm now running Ubuntu is because it just works and I don't have to waste what little time I have trying to work out libraries and packages. Having said that, I'll make a personal observation and hopefully not make too many people mad at me.

It seems to me that in the early days of Linux, when it wasn't just a lack of knowledge about the OS that would hinder you but just the lack of the maturity in the OS itself, there was a percentage of people who liked to ridicule anyone using Windows. Assuming, I suppose that the rest of the world had nothing better to do but sit in their basement and spend the day trying to make things work and ocasionally scratching their heads at the mysteries of the Windows users.

Finally, along comes a distro like Ubuntu and these same people reidicule them and the vendors who make 'non-free' Linux drivers because it's all just too 'easy'. They claim that they want Linux to succeed and surpass Microsoft but they complain when someone makes strides in making that a possibility. In fact, they even compalin when Ubuntu contemplates including these 'non-free' drivers in their distro. That's not exactly a good way to encourage vendors to continue spending their time and resources in making additional drivers.

The fact is there is a percentage of Linux users who don't really care how successful the OS is, they just like being on the 'fringe' and spending their hours recompiling packages and bragging about their vast knowledge to their friends. The bottom line is until the single mother can isntall the OS for her children, or until office can be reasonably certain that their entire IT team will not spend the day trying to make a printer work or those like me who already work 50-60 hours a week and just want a stable operating system and don't have to quit their job to set it up, Linux will never be a threat to anyone except itself.

Thank you Ubuntu team for the short cuts. the updates, the GUI's and everything else that makes it possible for me to run a stable and reliable OS on my laptop, which goes with me to work every day!

---

### Post by phossal on 2007-02-16
Why would anyone download the .bin file from SUN and create a *package*? Why not just install using the .bin, and incorporate Java into update-alternatives?

---

### Post by meng on 2007-02-16
I bow to your superior knowledge phossal.
```
sudo apt-get install sun-java6-jre
```
just seems to me to be simple, direct, and takes advantage of the repositories. If that's stupid, then I'm proud to be stupid.

---

### Post by phossal on 2007-02-16
MENG, I would never claim *you* were stupid, no matter how many hundreds of times I had installed JDK's of every flavor, using every method. And I would never suggest that using a repository isn't *a relatively easy* way to accomplish a task. What I asked is why would anyone download the *.bin* file and then create a package? 

For the record, my argument against using the repository for Java 6 is that a) I know who made that package and he's an idiot. b) it's a *third* party package in *backports* which means it has all the security risks of the SUN bin file *plus* any that the packager wanted to include and c) it doesn't even configure your system properly. Finally, it isn't updated nearly as quickly as the source, SUN's .bin file, and you can't install more than one JDK.  Oh, and you can't install the *older* version. I guess that's a *lot* of reasons not to use the package manager. The package manager is *stupid.*

Why not just download the bin and run it? Isn't *that* easy? I'm not a lemming. I don't follow the Ubuntu way when it doesn't make any sense.

[EDIT] Another *strong* reason for suggesting that people download the JDK and JRE directly is that it's much simpler to diagnose a failed (or partial) installation. A blown package install is a *nightmare* to diagnose.

---

### Post by meng on 2007-02-16
Fair enough, I certainly can't argue with the security risks. As far as function is concerned, it satisfies my needs, but of course I can't speak for any other user.

---

### Post by timlewis242 on 2007-02-17
I rest my case.

---

### Post by phossal on 2007-02-17
> **timlewis242 said:**
> I rest my case.
What is your case again? You've just realized Linux isn't Windows? I tend not to read the newbie babble about the OS wars they believe exist after reading the "tech" columns of magazines and newspapers. There isn't any war. In any area where developers can make their own decisions, which is less frequent in the general operation of Windows, you're going to have conflicts of opinion caused by, at the very least, the needs and tastes of the individual developer. 

I couldn't care less if Linux is ever installable by a single mom. Truthfully, I couldn't care less if single moms can do *anything.* My goal in life is not to pad all the sharp corners of existence so that every idiot can function without too much trouble. I want to solve my own problems efficiently and *effectively*. That's true regardless of the OS.

My conversation with MENG in previous posts was a less-than-subtle way of offering an alternative route to accomplish a task that *has* multiple routes. On Windows, you download the .exe from SUN, end of story. If that's *ideal* for you, you should head back to Windows. It wasn't a war. MENG is an intelligent, knowledgeable user, and I thought he might convince me I was doing it all wrong, or at least give me a reason I could latch on to for doing it differently than I do. I was trying to get information. It isn't support for an OS war.

---

### Post by timlewis242 on 2007-02-17
Again I rest my case. You simply continue to critisize anyone you think is not up to par with your "intelligence". As far as being a newbe, a title I'm sure you like to throw around on chat boards to show your deep-seated knowledge, I've used LInux for many years and understand full well that it's not Windows. Hey, don't you have some libraries or some dependencies to compile?

---

### Post by phossal on 2007-02-17
No, I have actual *work* to do. You can type "I rest my case" repeatedly, but I'm still without a clue as to what your case *is*. Are you trying to communicate something? I certainly wasn't trying to *offend* you. I suspect, though, you have a perspective that's skewed slightly from reality. 

While I know I can make a pretty nice looking truck out of Play-Doh, I know it doesn't compare to the truck-like nature of a Tonka. If you're a Tonka fan, you shouldn't buy Play-Doh when you want and need Tonka qualities. If you're a Play-Doh user who thinks your toy is trying to steal Tonka market share, your perspective of reality is skewed.

My premise is that Linux users *know* they're using Play-Doh, so any criticisms about it's failure to be more Tonka-like fall on deaf ears and earn harsh looks. So, again, if you have something to say, I wish you would repeat it, because I would like to try and understand what you think your point is. Then, when we're clear about what you think you mean, I'll explain to you - if you still need me to - why nothing I've said supports any argument of yours worth making.

---

### Post by timlewis242 on 2007-02-17
Okay, but remember you asked for it. My initial posting, I thought, was self explanatory but I'll do it again and then drop this petty topic.

I can't imagine any of us would not like to see Linux spread to a larger market, maturing the OS, increasing the number of users, increasing the demand for hardware support, etc. With that in mind, I (who have used Linux in one fashion or the other since 1999) do not understand why there are people like you who find it more preferrable to keep it where it is. My statements are simply my personal gripe with a small percentage of users who seem to come to these support forums and then be-little anyone who might have a different view or a different way of doing things. People who do not want to see the user base widen or ridicule those who try to make the procedure of running Linux easier. You may or may not fit in this category but you probably do and I'll explain why.

"For the record, my argument against using the repository for Java 6 is that a) I know who made that package and he's an idiot"
   Intent: To show everyone who might muster up a response to your previous reply that you are high on the linux food-chain and you know 'people'.
   Reality: You may know "of" him but you most likely do not know him personally or you would not be so quick to call him an "idiot" on a public forum.

"it's a third party package in backports which means it has all the security risks of the SUN bin file plus any that the packager wanted to include and c) it doesn't even configure your system properly"
   Intent: To show that you know far more about the package developement than anyone else and this fact alone should stifle any response form people seeking help on  this board or questioning your expertise.
   Reality: You probably did stifle some people seeking help from this board.

"I tend not to read the newbie babble about the OS wars they believe exist after reading the "tech" columns of magazines and newspapers."
   Intent: Minimalize anyone who challenges me so that I can minimalize whatever point they may be making
   Reality: I stated clearly in my first post that I have been using Linux for years and whatever name you want to attach to me means little. There was no mention about "OS Wars" in any of my posts and that was not the point of my post.

"I couldn't care less if Linux is ever installable by a single mom"
   Uh, WOW? I guess you don't think the guy who developed the repository (the one you know) or any single mothers could possibly look for assistance from this board. Or maybe you're so self centered you don't care.

"My goal in life is not to pad all the sharp corners of existence so that every idiot can function without too much trouble"
   I guess anyone who posts questions is an "idiot"? Functioning without too much trouble is the premise behind the Personal Computer I think. Correct me if I'm wrong.

"While I know I can make a pretty nice looking truck out of Play-Doh, I know it doesn't compare to the truck-like nature of a Tonka. If you're a Tonka fan, you shouldn't buy Play-Doh when you want and need Tonka qualities. If you're a Play-Doh user who thinks your toy is trying to steal Tonka market share, your perspective of reality is skewed."
   Again we're back to assuming anyone that wants to see Linux easier to administer must be minimalized and talked to as if he's just made the wrong choice of OS's. 

   I can't go through anymore of these. The crux of my post was this. There is a small percentage of people in the linux community who take great pleasure in slamming users who post questions and enjoy the fact that there can be a certain amount of difficulty in administering the OS. These people ridicule anyone and everyone who would dare to use automated tools (tools that someone spent many hours to develope) in order to make the job easier. If you fall into that category, sorry it offended you but if you look at the title on this particular board I think it reads "Absolute Beginner Talk" not "LPIC 1 & 2 Exam Cram". 

  I would think that if you're going to enter a forum like this and attempt to help people with their problems (considering the title) that you would be a little more patient and a little less critical. I have no doubt you're well educated in the OS but that's no reason to refer to the rest of the people here as "idiots" who need the sharp corners of existence padded for them.

That is my point.

---

### Post by RedSquirrel on 2007-02-18
> **Pai said:**
> I need to install jre:
[img]http://img235.imageshack.us/img235/1928/untitledzq6.png[/img]

So I looked around for instructions on doing so in Dapper, and found the following:

 
So I followed those instructions (replace **jre-1_5_0_10-linux-i586.bin** with the newer **jre-6-linux-i586.bin ** that I downloaded.), but ran into trouble creating the Ubuntu package:

karl@karl-desktop:~$ sudo apt-get install java-package
Reading package lists... Done
Building dependency tree... Done
java-package is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
karl@karl-desktop:~$ cd Desktop
karl@karl-desktop:~/Desktop$ fakeroot make-jpkg jre-6-linux-i586.bin
Creating temporary directory: /tmp/make-jpkg.XXXXhYHkGg
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2 sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sd k.sh
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to de fault (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to de fault (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to de fault (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to de fault (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to de fault (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to de fault (native compilation)

No matching plugin was found.
Removing temporary directory: done
karl@karl-desktop:~/Desktop$


So, are these faulty/outdated instructions? Or am I simply doing something wrong.



I think the problem is that the **java-package** in the repositories is too old for the jre-6.

There is a patched version on post #15 of this thread:

[http://www.ubuntuforums.org/showthread.php?t=316980&page=2](http://www.ubuntuforums.org/showthread.php?t=316980&page=2)

I used it for the jdk-6 and it worked like a charm.

---

### Post by picpak on 2007-02-18
I personally would've just opened up Applications > Add/Remove and install Java from there, but that's just me.

---

### Post by jay019 on 2007-02-19
> **phossal said:**
> 
I couldn't care less if Linux is ever installable by a single mom. Truthfully, I couldn't care less if single moms can do *anything.* My goal in life is not to pad all the sharp corners of existence so that every idiot can function without too much trouble. I want to solve my own problems efficiently and *effectively*. That's true regardless of the OS.


Wow. I thought ubuntu meant "humanity"
All I can see here is a lack of it.

Why are you using ubuntu? Shouldn't you (with your unlimited intelligence) be using slackware or your personal LFS?

---

### Post by timlewis242 on 2007-02-19
Yeah, sorry about that, I guess the 'adult' thing to do would have been to let it all go but I hate bullies, intellectual or otherwise.

---

### Post by phossal on 2007-02-19
You keep acting as if you're above the argument with me, but yet there is a daily response from you. Do you want me to take the time to write out a page long explanation for you? If you're *capable* of learning something, I believe I know a few things that would change your perspective if you're a *reasonable* person. I tried not to respond and to let it go, but I'll engage you if that's what you *want.*

As it stands, you're on a high horse, preaching nonsense.

For those of you who choose to download Java 6 from the backport repositories, I don't *care.* But you cannot deny the reality that the package is prepared by someone you don't know. You have no idea how it was packaged, or what steps the installation script performs. You cannot deny that it doesn't solve the problems of installing the plugin or web start. You cannot deny the reality that the package is just prepared using the SUN .bin file that you can get and install *yourself*. You cannot deny that the package method prevents you from taking advantage of updates from SUN until someone packages them for you.

Of course, you're free to choose to use the package still, and I don't *care* if you do. But, if you have other needs like I do, you might *enjoy and benefit* from knowing how to install Java (and other software) on your own, so you're not obliged to wait for others, suffer with out of date versions, risk security breaches, etc. Why am I such a bad guy for suggesting that method? I have a few hundred thank you emails from people who found the method useful. For the record, Java isn't the only example of software better installed on your own.

I don't *want* an argument, and I don't *care* how you choose to manage your system. But, I'm willing to risk seeming cocky to present you with an alternative. If you think this somehow prevents Linux from overtaking Windows, you've wrongly assumed I give a crap about Linux over taking Windows. No one *cares* about that who is *practical.*

---

### Post by phossal on 2007-02-20
I edited the tutorial I had written on installing Java to reduce it to [six steps]("http://ubuntuforums.org/showthread.php?t=332674#1"). It doesn't mean you can't still download the backports package. It's just a suggestion that frees you from relying on anyone else to stay current, and it might offer insight into your system that can be used for powerful modifications.

---

### Post by igknighted on 2007-02-20
Not much to add here, I do agree with Phossal about the Java install being the best way, but this is linux, so it's all personal preference.

As for the side debate, I also must agree with Phossal here.  He sounds harsh, but he makes a great point.  As a linux user, I don't really care if linux ever overtakes Microsoft.  In fact, in a lot of ways I don't want it to happen.  The extra attention could very easily prove a derisive force, and the influx of users could prove too much for the community to support.  If anyone with a genuine interest wants to learn linux I would LOVE to sit down and help that person learn the ropes, be they an advanced computer user or a single mom.  The experience of passing on knowledge I have to someone who wants to learn is great.  However, in a more general sense, I really don't care.  Linux is more important to me than the users, and in the end the OS has to work for me, so if making a few changes at the heart of the OS would bring in thousands more users, well, I don't want that for the sake of new users.  I want my OS, and if others like it, great, I'll help you learn it and make it your OS too.

The point of the preceding paragraph is that I fully understand where Phossal's frustration comes from.  While I might not agree with the time or place of the conversation (cafe might be more appropriate, or other OS talk), I sympathize with his feelings on the subject.

---

### Post by Sarteck on 2007-02-20
> **jay019 said:**
> Wow. I thought ubuntu meant "humanity"
All I can see here is a lack of it.

~nodnod~

Yeah, this debate is getting a bit out of hand, I think.  Hey, Phossal.  Would you consider putting up your way of installing Java as a HowTo for newbies?  I actually searched for such a thing, but couldn't find it, and ended up ultimately installing it using the backports.

Other than that...  Geez, guys, chill out.  XD  Have some popcorn.:popcorn:

Edited, nevermind, phossal, I see you linked to your guide. XD

Edit2:  This kind of makes me wish, though, that it was part of the links in the stickies up there, for us newbs.  :(  After reading the arguements, I really do agree with phossal, and I think his way is the right way.  At least for now.

---

### Post by phossal on 2007-02-20
I've chosen the wrong *way* of saying what I mean to say lately. I must be partially *bored* with the forums. It's my own fault. I seem to have lost sight of the fact that I want to help the people who want to be helped. Sorry for my bad attitude, gang.

---

### Post by jay019 on 2007-02-20
> **phossal said:**
> I've chosen the wrong *way* of saying what I mean to say lately. I must be partially *bored* with the forums. It's my own fault. I seem to have lost sight of the fact that I want to help the people who want to be helped. Sorry for my bad attitude, gang.

I didn't meant to have a dig at you, just the single mother bit hit a nerve due to my circumstances. Nevermind, no harm done. In fact I have java and netbeans running great so I cant complain.

---

