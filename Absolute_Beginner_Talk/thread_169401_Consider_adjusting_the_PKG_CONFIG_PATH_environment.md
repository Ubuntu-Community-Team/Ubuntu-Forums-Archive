---
title: "Consider adjusting the PKG_CONFIG_PATH environment variable?!!"
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by mybootorg on 2006-05-02
I love Ubuntu's Synaptic Package Manager.  Because having to hunt down ten different obscurely named packages of a particular version range -- just to be able to install one package I want to use?  That's a lot of work.  Especially when several of the required packages undoubtedly have additional package requirements of their own.  *sigh*

However, if you really want the latest version of something - say, Evolution 2.6 -- then you have to go the manual install route.  In attempting to do just that, I downloaded the required packages:

Evolution   2.6.1
Evolution Data Server   1.6.1
GtkHTML 3.10.1
libsoup 2.2.92
Evolution Exchange 2.6.1

Here's the GOTCHA -- I get all the way to installing Evolution 2.6.1 itself.  I've installed GtkHTML 3.10.1 and I've even rebooted.  But running the included ./configure script for the main package, it runs for quite some time and then hits this:

> configure: error: Package requirements (libgtkhtml-3.8) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the GTKHTML_CFLAGS and GTKHTML_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.


..the hell.... I just installed the damned gtkhtml package - and the correct version Evolution had on their page too.  I didn't change any install paths... and yet, still the error.  

So how do I satisfy the Evolution installer than I do indeed have this package installed?  **It says I can set these environment variables... but pointing to what?  Where should each variable be pointed? Is there an easy way to view my environment variables like in Windoze?  Is this hardcoded path only so the installer can do its work or because Evolution needs constant access to it?  How long will the Environment variables last?  After a reboot?**

I know the actual command EXPORT ENVIRON_EXAMPLE="/this/sucks/" I guess I just don't understand why it's necessary or what to point each one to.

Sorry for somewhat of a rant.  But I've hit this same brick wall / different  package with gnomemenuedit, evolution-sharp... the list goes on and on.

This is a hurdle I'm hoping someone can teach me to jump. :)

---

### Post by username132 on 2007-08-19
Hey; this guy's still waiting for an answer! I have a similar problem install GIMP-GAP on SUSE. Where's the PKG_CONFIG_PATH environmental variable that I'm supposed to edit? I've run searches and can't find it...

---

### Post by schorsch on 2007-08-19
This message often leads to confusion as you are not missing exactly the mentioned package but the corresponding development package which usually ends with "-dev". So in the first post there is probably not the package "libgtkhtml-3.8" missing but the package "libgtkhtml-3.8-dev".

---

### Post by bsmonks on 2007-08-30
> **schorsch said:**
> This message often leads to confusion as you are not missing exactly the mentioned package but the corresponding development package which usually ends with "-dev". 

Yeah. Thanks for half the answer. How do I get a -dev package?!? It's not listed in the package list for me to install. Nothing says how to go out and find all this crap that needs to be installed/configured/typed! And most of the people who post answers to questions on this forum expect everyone who asks a question to know all the nitty gritty of linux. IF WE KNEW HOW TO INSTALL -DEV PACKAGES AND ./CONFIGURE -ING STUPID LITTLE PROGRAMS WE WOULDN'T BE POSTING OUR QUESTIONS! Look at our number of posts. Can't you tell we're all bloody newbs and don't know the ins & outs of this stuff.

Crimeney... I'm just tired of spending 3 days just trying to get discomatic installed. And I don't even know if it'll do what I'm wanting. It's just one stupid little program, but linux keeps throwing up these stupid walls and doesn't even try to help me get over them. NO! I have to google for hours, post on forums and hope I get some help.

And linux users wonder why they're always getting bashed and why nobody accepts the OS as legitimate.

God, I'm just tired...

---

### Post by splintercellguy on 2007-08-30
sudo apt-get install xxxxxx or search in Synaptic would do it. Make sure to install build-essential if you haven't done so already. I think in your case you should do sudo apt-get install libgtkhtml3.8-dev. Repeat for any dependencies, searching in Synaptic helps.

---

### Post by schorsch on 2007-08-30
> **bsmonks said:**
> Yeah. Thanks for half the answer. How do I get a -dev package?!? It's not listed in the package list for me to install. Nothing says how to go out and find all this crap that needs to be installed/configured/typed! And most of the people who post answers to questions on this forum expect everyone who asks a question to know all the nitty gritty of linux. IF WE KNEW HOW TO INSTALL -DEV PACKAGES AND ./CONFIGURE -ING STUPID LITTLE PROGRAMS WE WOULDN'T BE POSTING OUR QUESTIONS! Look at our number of posts. Can't you tell we're all bloody newbs and don't know the ins & outs of this stuff.

Crimeney... I'm just tired of spending 3 days just trying to get discomatic installed. And I don't even know if it'll do what I'm wanting. It's just one stupid little program, but linux keeps throwing up these stupid walls and doesn't even try to help me get over them. NO! I have to google for hours, post on forums and hope I get some help.

And linux users wonder why they're always getting bashed and why nobody accepts the OS as legitimate.

God, I'm just tired...
Hey calm down! First of all: Get used to synaptic as not every package is installable via "Add/Remove Programs". Especially the development packages are not mentioned there so fire up synaptic under "System/Administration/Synaptic Package Manager", click on search and type what you want to install.
Second: Do not complain about being not able to install software that is not in the repos by adding a post to a thread that you got some clues from how it COULD work but that was not originally started by you. Start a thread with a title like "How to install discomatic; I cannot find it in the repos" and someone out there will probably help you step by step.
Third: What exactly do you want to install and where did you get it from?
Fourth: Please read what splintercellguy wrote even it it does not cover exactly your problem ....

---

### Post by splintercellguy on 2007-08-30
I actually didn't notice that he wasn't the OP until now, but yes, what schorsch said :).

---

### Post by erloha@hotmail.com on 2007-08-30
This thread should be made into a monument.  These two newbies have captured my thoughts and frustrations to a 'T'.  Everyone that starts out new to Linux must go through this.  Excellent piece of writing.  My very favorite part....   "God, I'm just tired..."   I feel your pain man,  Been there (last night).   HERE'S TO US NEWBIES!   FFFFFRRREEEEEEDDDDOOOOMMMM!!!!!:):):)

---

### Post by bsmonks on 2007-08-31
Any other posts I make will be [here]("http://ubuntuforums.org/showthread.php?t=539694").

---

