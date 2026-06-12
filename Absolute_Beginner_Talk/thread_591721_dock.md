---
title: "dock"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by limac on 2007-10-25
I want to try out installing dock, or give my awn a dockish look. How do I do either of them?

thanks a lot!

---

### Post by limac on 2007-10-25
please, anyone? I need help with this.

Thnx

---

### Post by Maestro23 on 2007-10-25
Are you wanting to install the AWN?  Here is the AWN Wiki: [http://wiki.awn-project.org/index.php?title=Main_Page](http://wiki.awn-project.org/index.php?title=Main_Page)

---

### Post by limac on 2007-10-25
I actually want to install kxdocker on my ubuntu gutsy. I already have awn installed but i want it to get replaced by kxdocker, or dock itself if possible.

Thnx

---

### Post by Maestro23 on 2007-10-25
Googled up KxDocker, Found this site: [http://www.xiaprojects.com/index.php?section=All&project=KXDocker](http://www.xiaprojects.com/index.php?section=All&project=KXDocker)

You might be able to google up some more info.

Good luck.

---

### Post by limac on 2007-10-25
anything more explanatory than that?

---

### Post by Maestro23 on 2007-10-25
> **limac said:**
> anything more explanatory than that?

The page seemed informative to me.  What exactly do you want it to tell you?

That link came from the Documentation link on the following page:[http://www.kde-apps.org/content/show.php?content=10958](http://www.kde-apps.org/content/show.php?content=10958)

---

### Post by limac on 2007-10-25
So well, according to your understandings, what did it say. Since i am pretty much a newbie, I kind of need very detailed pieces of info to fulfill it. 

So what exactly does it say to do?

Thnx

---

### Post by Maestro23 on 2007-10-25
> **limac said:**
> So well, according to your understandings, what did it say. Since i am pretty much a newbie, I kind of need very detailed pieces of info to fulfill it. 

So what exactly does it say to do?

Thnx
There are Download links at the top of the page.  There's not an Ubuntu Binary, so you will have to download/compile the source code.  The link is at the top of the page.

There are installation instructions at the bottom of the page:

> Compilation

compile it and install (use $KDEDIR or your default kde directory installation):

./configure --disable-debug --prefix=$KDEDIR
make
make install
kxdocker



You run into trouble, there's a FAQ link at the top of the page as well.

IF you have never installed from source on Ubuntu, you will need to install **build-essential** first.

> sudo apt-get install build-essential

If that doesn't help you, then try might want to try and google up something else.

Good luck.

---

### Post by limac on 2007-10-26
if you don't mind can u tell me the commands and all things about downloading kxdocker?

---

### Post by twiceasworn on 2007-10-26
You know, we don't mind helping but the fact that you aren't willing to read the link and do what it says is a bit ridiculous.

---

### Post by limac on 2007-10-26
Well I am a very much a newbie and am not really familiar to all the terms so ur help makes it a lot more clearer.

---

### Post by limac on 2007-10-26
I don't get what to do with these:

Trash component;
kxdocker-gtrash-1.0.0.tar.bz2 [15/February/2006 12:42 ]

Task manager component;
kxdocker-taskmanager-1.0.2.tar.bz2 [08/April/2006 19:42 ]

Ho do i install these or what do u i do with these?

Thnx

---

### Post by Pumalite on 2007-10-26
I don't think you are ready to compile. Stick to Synaptic for now, until you are more familiar with the terms and commands.

---

### Post by limac on 2007-10-26
But i want to install kxdocker

---

### Post by pilli on 2007-10-26
Do some research and some reading.  Most of all, research and read the advice and links people give you here.  It'll generally be good or it'll lead you to the answer.  Your effort is, however, needed.

I suspect most people posting here have traveled this road.

---

### Post by Incense on 2007-10-26
> **limac said:**
> I don't get what to do with these:

Trash component;
kxdocker-gtrash-1.0.0.tar.bz2 [15/February/2006 12:42 ]

Task manager component;
kxdocker-taskmanager-1.0.2.tar.bz2 [08/April/2006 19:42 ]

Ho do i install these or what do u i do with these?

Thnx

Those are just plug ins that will be installed with the rest of the files if you keep following the guide. Good luck. Compiling source can be rough, but it's really cool the first time you make it work! Just don't be intimidated by it.

---

### Post by llamakc on 2007-10-26
> **limac said:**
> if you don't mind can u tell me the commands and all things about downloading kxdocker?
My bad. replied to post on 1st page instead of reading the rest of the thread.

---

### Post by limac on 2007-10-26
What is KDEDIR?

---

### Post by llamakc on 2007-10-26
> **limac said:**
> What is KDEDIR?

It's letters. The letters represent the path for KDE when compiling in that particular example.

---

### Post by limac on 2007-10-26
How can I figure out the command for 

Trash component;
kxdocker-gtrash-1.0.0.tar.bz2 [15/February/2006 12:42 ]

Task manager component;
kxdocker-taskmanager-1.0.2.tar.bz2 [08/April/2006 19:42 ]

any suggestions for how to figure the command out?

thnx for help so far and boosting up my figuring out confindence.

---

### Post by llamakc on 2007-10-26
> **limac said:**
> How can I figure out the command for 

Trash component;
kxdocker-gtrash-1.0.0.tar.bz2 [15/February/2006 12:42 ]

Task manager component;
kxdocker-taskmanager-1.0.2.tar.bz2 [08/April/2006 19:42 ]

any suggestions for how to figure the command out?

thnx for help so far and boosting up my figuring out confindence.

There is  NO command for that. 

A. Do you have a Terminal opened? Answer that first.

---

### Post by limac on 2007-10-26
yep I have a terminal opened

---

### Post by limac on 2007-10-26
what do u do if there is no command for that?

---

### Post by llamakc on 2007-10-26
> **limac said:**
> what do u do if there is no command for that?

What are you talking about? You're SUPPOSED TO FOLLOW the instructions on the link provided earlier to build kxDocker. It is NOT currently supported by the APT package management system, so YOU have to build it from source.

GO to the link provided and follow the directions.

---

### Post by limac on 2007-10-26
One question what do they mean by source directory? what is it?

---

### Post by llamakc on 2007-10-26
That can mean alot. You'll get much more concise and informative answers if you provide the context for your question.

Remember, the people trying to help you aren't necessarily trying to install the piece of software that you are. Therefore it is your responsibility to the community to ask questions that are easily understandable.

What do YOU mean by "they mean"? Provide the link to the page where you are confused by the instructions.

Typically, it means to change directory (cd) into the downloaded source code directory.

---

### Post by limac on 2007-10-26
this is what sudo make install says:

/usr/bin/ld: cannot find -lXtst
collect2: ld returned 1 exit status
make[2]: *** [libKXMouse.la] Error 1
make[2]: Leaving directory `/home/ron/kxdocker-1.1.4a/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ron/kxdocker-1.1.4a'
make: *** [all] Error 2

so any suggestions for how i can avoid that error.

And about the Trash component;
kxdocker-gtrash-1.0.0.tar.bz2 [15/February/2006 12:42 ]

Task manager component;
kxdocker-taskmanager-1.0.2.tar.bz2 [08/April/2006 19:42 ]

what do i do about that?

---

### Post by llamakc on 2007-10-26
So the "make" command completed without error?

---

### Post by limac on 2007-10-26
the link to the page i was confused about was:

[http://wozlabs.com/linux/kxdcfht.html](http://wozlabs.com/linux/kxdcfht.html)

---

### Post by llamakc on 2007-10-26
So the make command completed without error?

---

### Post by limac on 2007-10-26
> **llamakc said:**
> So the "make" command completed without error?

i have no clue about that.

What ur view about it?

What do u think the problem might be?

---

### Post by SqdnGuns on 2007-10-26
[http://ubuntuforums.org/showthread.php?t=554127](http://ubuntuforums.org/showthread.php?t=554127)
 
Not gonna hold your hand though....................

---

### Post by llamakc on 2007-10-26
> **limac said:**
> i have no clue about that.

What ur view about it?

What do u think the problem might be?

Once again, without you providing details there is no way to say.

---

### Post by limac on 2007-10-27
Then How in the world can i install kxdocker?

---

### Post by limac on 2007-10-27
Those links are doing the job of installing kxdocker perfectly.

---

### Post by limac on 2007-10-27
> **llamakc said:**
> Once again, without you providing details there is no way to say.

I meant that when you said "So the "make" command completed without error?" to my post   , I didn't really have a clue about what you meant by saying that.

---

### Post by limac on 2007-10-27
sorry for starting a similar thread. I somehow can't be able to navigate to my other thread anyhow. 

Well anyway, my question is regardless of how many times I tried installing kxdocker, I always failed? So how can i install kxdocker successfully?

Thnx

---

### Post by limac on 2007-10-27
Hello?

---

### Post by llamakc on 2007-10-27
You can't. Use software in the repositories please. And learn how to use the search features of the forum before creating duplicate threads.

limac, you seriously need to start reading the advice given to you. It is approaching the point where folks who are eager to help out will begin to start avoiding your posts.

kxDocker is no longer worked on. If you can't follow the instructions already posted, I suggest you look on the support mailing list or forums for the piece of software you are attempting to install.

In the meantime, only install stuff from Synaptic/Adept. Do you know what Synaptic or Adept are?

---

### Post by limac on 2007-10-27
of course i do?

Then which kind of dock applicable to ubuntu resemble Apple mac's?

---

### Post by llamakc on 2007-10-27
Are you being rhetorical?

Avant-Window-Navigator.

Perhaps it is best if you spend more time getting the basics down? [http://linuxcommand.org](http://linuxcommand.org)

---

### Post by limac on 2007-10-27
So what do you think about kiba-dock? what's your opinion about it?

---

### Post by Maestro23 on 2007-10-27
> **llamakc said:**
> Are you being rhetorical?

Avant-Window-Navigator.

Perhaps it is best if you spend more time getting the basics down? [http://linuxcommand.org](http://linuxcommand.org)

Just to add to llamakc's post:

Here's the website for Avant-Window-Navigator: [https://launchpad.net/awn/](https://launchpad.net/awn/)

---

### Post by limac on 2007-10-27
awn is giving me some hard times.

---

### Post by Maestro23 on 2007-10-27
> **limac said:**
> awn is giving me some hard times.

Kiba-Dock: [http://www.kiba-dock.org/](http://www.kiba-dock.org/)

Ubuntu How-To: [http://ubuntuforums.org/showthread.php?t=263810](http://ubuntuforums.org/showthread.php?t=263810)

---

### Post by limac on 2007-10-27
so which one in your opinion is better and looks more mac os type, Xqde or kiba-dock?

---

### Post by limac on 2007-10-27
any opinion?

---

