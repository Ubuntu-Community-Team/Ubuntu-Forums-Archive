---
title: "how do I install Apps and programs"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by Jeffro430 on 2007-03-13
Greetings Ubuntu Masters,

I am an absolute beginner and I need to know how to install applications and progams aas well as plugins into firefox. I have been a Win Xp user for 6 years. I have figuered out the synaptic package manager and love it,  there are evidently 2 ways to install things into Ubuntu A command way which I don't understand and SPM. I also don't get all the abbreviations everyone uses when talking about installing programs.
Please help
Many thanks

---

### Post by AndyCooll on 2007-03-13
The easiest way is to use Synaptic (System > Administration > Synaptic Package Manager). That takes all the grunt out of installing programs for you.

:cool:

---

### Post by Tyr Norian on 2007-03-13
Synaptic is great, but ultimately it's just a convenient GUI frontend for the package manager for Debian, which is called aptitude. You can invoke it on the command line with apt-get. For example, the following command installs the package wine:
```
sudo apt-get install wine
```
Other options, like "remove", also work. If Synaptic works for you, I suggest sticking to it, since it can do most things apt-get will do without learning the syntax, but if you're curious, read the manual for aptitude:
```
man aptitude
```
I find Synaptic can be a little bit slow, so when I know the name of the package I want, I use the command line. Using Linux for a while tends to make you into a bit of a speed demon!

---

### Post by Tipo on 2007-03-13
You can also take a look at the "Applications" menu and select "Add/Remove..."

Although it's not as extensive as the Synaptic package manager, it's a little more user friendly; It divides up available apps up into categories, and uses icons :)

---

### Post by Jeffro430 on 2007-03-13
WOW guys what a great community this is, I left for a minute to read some threads on the beginners team and BAM ive got 4 responses sweet!!
thanks folks I'll work with all your suggestions

---

### Post by ygarl on 2007-03-13
A bit of advice:
People seem to just be giving you commands without explaining them. Let me see if I can help some more. I feel it's more important WHY you are putting commands in than just what to put in. Otherwise you're just acting like a monkey - and if something goes wrong you won't know what to do!

Here goes:
sudo apt-get install (package)

Break it down... Hammer time:

sudo - basically makes you a "superuser". Otherwise, you won't get permission to install anything. This is one of the reasons virii just don't get a foothold very easily on Linux!

apt-get - this is the program with lets you install/uninstall new software on Ubuntu. There are other odd and wonderful things you can do with apt-get (and various other "apt" programs), but most of them are somewhat obscure to a newbie.

install - this is just telling apt-get what you want to do. You can also use "update" and hit Enter which will go online and make sure the list of programs available are up-to-date, or "remove" with does precisely what it says on the box - removes programs. Again, going through the "man" like an earlier person said will help

So, you are using sudo to get permission to be a "superuser", then using apt-get to install whatever program you put on the end.

Hope this helps. It's actually much faster than Synaptic if you know the name of the program you want to install (try amarok if you want just about the best music mananger in the world!).

Bob

---

### Post by Berylfun on 2007-03-15
newbie here as well.
Has the Synaptic Manager always the latest version of the programs ?
How can i install a program that have downloaded as a file in a different part of my disk ? For example i have just downloaded the latest version of Azureus. I have it as a file on my desktop but i m really not sure how can i install it.

---

### Post by hyper_ch on 2007-03-15
Regarding for plugins in firefox those are .xpi files. Just save them (on the desktop) and then in Firefox go to "File" --> "Open File" (or press ctrl-o) and select the downloaded .xpi file. It will then ask you whether you want to install it.

Well, there's not always the laste program in the repositories but if there is not a really necessary reason why you want a newer version than there is in the repository then stick with the ones offered by Synaptic/Adept/Aptitude/apt-get... because those versions have been throughly tested and work just fine... other downloads may not work and then you can get into troubles.

However if you decide to download a newer version it depends whether it's a .deb file or a ".tar.gz" or ".bz2".

.deb files are "debian package" files just like the ones that you can find in synaptic. Download it on the desktop and double-click it.. you will then be asked whether it should be installed.

If it's not a .deb file then you will have to compile the program from the source yourself. In the beginning I advice against compiling if there is not a really good reason for it. Have a read here: [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by Berylfun on 2007-03-15
Thanks a lot for the immediate answer !!
One silly question again (please forgive me...) in which directory i must install the programs ?

---

### Post by hyper_ch on 2007-03-15
Depends... when you using synaptic or another package manager you can't choose... it was precompiled for your version...

with the .deb files the same applies from above...

and when you compile programs from source then normally it will also install to default locations... so you have to be more specific :)

---

