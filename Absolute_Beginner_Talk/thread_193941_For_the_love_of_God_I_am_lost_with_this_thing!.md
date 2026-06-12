---
title: "For the love of God I am lost with this thing!"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by Kasabian on 2006-06-10
Right - this is deffo my last attempt at grasping Linux - damn Gates and his making me so dependent on double clicking.

So far I have XP Pro and Ubuntu Drake dual booting. And I have run the updates in Ubuntu - so you know where I am as of now.

I simply can't get anything to install - it's mid boggling at times. As crap as XP may be it's gravy for a complete moron to install aps - I am no moron - so why am I struggling so much to get my head around this?

E.G - found a link on here that showed how Opera 9 is installed from a terminal - worked fine - but all I am doing is Copy/Pasting into Terminal - I have no idea what the hell it is I am doing.

My main issues at the moment are grasping getting ATI drivers installed - DivX/Xvid and some kind of MP3 decoder - that reminds me - is there Winamp for Linux? I can't find it - so what are you all using instead that is similar.

BTW - don't think you are treating me with disrespect by telling me the obvious - I can't seem to get anything working. Imagine I don't know the Alphabet and you are teaching me to spell cat - yes it is that bad.

It's really hard to start searching for answers when I have no idea what I am doing wrong - if you know what I mean. Christ - Dos/Win3.11 was never this hard to grasp ](*,)

---

### Post by colo on 2006-06-10
Quit the trolling/astroturfing, and you will surely get the support you need so desperately.

Next applicant, please.

---

### Post by Jagot on 2006-06-10
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

The above link is a fantastic resource for learning to install things in Ubuntu.  This link also explains some of that but also has some more stuyff on there that may be of use to you as well:

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

DIVX, Xvid, mp3 codecs are all covered here:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

XMMS and Beep Media Player are oth very similar to Winamp and you can use Winamp skins with them and equaliser settings.

A lot of your experience at the beginning will be of copying and pasting commands, but the more you use it, the more you'll work out what everything does and how it works.

---

### Post by bobpur on 2006-06-10
I know what you mean. I've stumbled across more fixes by accident than  on purpose. Most of this is as clear as mud but I keep trying.
                             Good Luck

---

### Post by Donshyoku on 2006-06-10
Go to the Third-Party Programs forum here on the site.  There is a program called BUMPS that will install your video driver, Xvid/Divx (and TONS of other codecs) including your MP3 decoder.

The program is simple to run.  Put it in your home folder, extract it (secondary-click, Extract Here) and do as follows (replace "luser" with your login name):

```
cd /home/luser/bumps/
```

"cd" means "change directory" if you want to learn commands.

Then:

```
./bumps
```


"./" will initiate the script.  Once it is initiated, follow the instructions in the ensuing windows.  It has a basic GUI for installing the software.

I hope that helps!

---

### Post by Bd0g on 2006-06-10
Since you are new you might want to check out Automatix. It's what most people want at first when they want a smooth transition into their system.

[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)
[http://www.ubuntuforums.org/showthread.php?t=177646](http://www.ubuntuforums.org/showthread.php?t=177646)

You will be suprised on how fast you can get a system going in no time with that :P

Concerning ATI Drivers:

[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

Winamp for Linux... 

Xmms or Beep Player .. You can get both if you use Automatix.

---

### Post by unicycler on 2006-06-10
compiling and building from source is not easy task. I have had very little success. The easiest way to install anything is with the synaptic packet manager. Search of the program you want to install and select it. It will select automatically any libraries or system files that need to be installed with it. Similarly, on the command line you can use: sudo apt-get install "package name". And last that I know of is the .deb is the equivalent to an .msi and most .exe files on windows. A .deb is an installer package. This just needs the command line: sudo dpkg -i <~/Desktop/package location>. Google's Picasa uses a .deb and goes on no problems.

---

### Post by Bd0g on 2006-06-10
One more extra..   If you feel like getting away a little from the terminal when you install *.deb files.. just

sudo apt-get -i gdebi

Ok, that was one more extra time.. but hey :P

---

### Post by zugu on 2006-06-10
[QUOTE=Kasabian]Right - this is deffo my last attempt at grasping Linux - damn Gates and his making me so dependent on double clicking.

So far I have XP Pro and Ubuntu Drake dual booting. And I have run the updates in Ubuntu - so you know where I am as of now.

I simply can't get anything to install - it's mid boggling at times. As crap as XP may be it's gravy for a complete moron to install aps - I am no moron - so why am I struggling so much to get my head around this?

E.G - found a link on here that showed how Opera 9 is installed from a terminal - worked fine - but all I am doing is Copy/Pasting into Terminal - I have no idea what the hell it is I am doing.

My main issues at the moment are grasping getting ATI drivers installed - DivX/Xvid and some kind of MP3 decoder - that reminds me - is there Winamp for Linux? I can't find it - so what are you all using instead that is similar.

BTW - don't think you are treating me with disrespect by telling me the obvious - I can't seem to get anything working. Imagine I don't know the Alphabet and you are teaching me to spell cat - yes it is that bad.

It's really hard to start searching for answers when I have no idea what I am doing wrong - if you know what I mean. Christ - Dos/Win3.11 was never this hard to grasp ](*,)[/QUOTE]

As you said, it's like you're re-learning the alphabet.

Ubuntu is not Windows XP. It's just another operating system. There are differences and similarities between the two.

I can understand your frustration, because I used to be like you 2 months ago. EWverything was different: there was no "My Computer" icon on the desktop, I could not listen to my mp3s etc. And the machine had no internet access, meaning I could not use one of the best features of Ubuntu/Debian: the apt-get command (it installs a program, along with its dependencies). i had to manually download the needed files, then install them, then see that I need some deps, then download the deps from another computer, then install them, then see that some of them have deps themselfes etc. It was a hell. but in this process I actually learnt what I was doing in that terminal. I learnt how Ubuntu works and how to achieve what I want.

So here's my advice for you:

- break your BIG problem into smaller, specific ones: like 'how do I install the program !@#$ ?', and post them in these forums - it's easier for you to get help in this way
- read this post of aysiu: [http://www.ubuntuforums.org/showthread.php?t=63315](http://www.ubuntuforums.org/showthread.php?t=63315) and find out if Ubuntu really is for you.

If you really have patience and try to learn something, you'll have a working, customised system in no time.

Good luck.

---

### Post by Kasabian on 2006-06-10
Thanks for all those - gives me something to work with - already read some bits and bobs that make sense (or more sense that 10 mins ago) I am waiting for that shining moment when it just clicks what it is I am doing and why I am doing it.

BTW - Quit the trolling/astroturfing, and you will surely get the support you need so desperately. Next applicant, please. Just doesn't help at all - in fact has really pissed me off - so kudos if that was the aim.

Also looks like starting with the ATI drivers is an error - I have found so many threads saying it is a pain in the butt to sort. Maybe I should start a bit lower and work my way up.

Find out if Ubuntu really is for you - basically if I can get some kind of a grip on Linux as fast as possible there are more jobs I can apply for - that's the main reason for trying it. I haven't used it since Libranet about two years ago and I have forgot everything I learned - DOH!

Anyway Cheers again.

---

### Post by Skye on 2006-06-10
No worries, we all have to start somewhere!

Ubuntu uses a package installation system.  Ideally, you shouldn't have to touch the command line to install things, but it's not always that easy.  

The first program you should become familiar with is Synaptic.  You can start the program by going to the System menu (at the top of the screen), and then the Administration submenu, and finally clicking on "Synaptic."  It will prompt you for your password because this is a program that installs things, so give it your password, and it'll start right up.

Synaptic has, by default, a list of every officially supported package (package == program) in ubuntu- these are packages that the Ubuntu team is going to support, release bugfixes for, and in general, guarentee to work.  If I remember correctly, it's something like 6 or 7 thousand packages.  These packages are hosted online in something called a "repository", which synaptic talks to in order to show you the programs you can download.  But, I assume that you want access to everything Ubuntu has to offer, so you need to add the multiverse and universe repositories.  Universe and Multiverse are repositories containing program that are still made for Ubuntu, but are not officially supported by the Ubuntu team.  The benefit is that after you enable you can access a staggering number of programs through the universe and multiverse repositories- over 18,000 programs, total.

To do this, follow the guide [here]("https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28repositories%29#head-5be95103ff75d442c031184440fc53892140eead") [Ubuntu Wiki].  That specific guide refers to Breezy Badger in the pictures and text, but the steps to follow are the same for your version, Dapper Drake.

Once you do that, and synaptic updates the package list, you have the full array of Ubuntu packages availible to you.  You can search the repositories using the "Search" function in Synaptic for anything you want- chances are, it's in there somewhere.

Now, to answer your specific questions:

_ATI Drivers:_
Follow the guide [here]("http://www.ubuntuforums.org/showthread.php?t=191944") [Ubuntu Forums]

_DivX Player:_
MPlayer is an excellent movie player, with a wide array of support formats.  Search for, and install **mplayer** in synaptic.

_MP3 support:_  
Check out the guide[ here]("https://wiki.ubuntu.com/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29") [Ubuntu Wiki]

_Winamp:_  
There is indeed a Winamp clone for Ubuntu- in fact, there are two:  **xmms** and **beep-media-player**.  Both of these are very similar to Winamp, but if you would like a full-featured program for organizing and playing music, (somewhat similar to iTunes, but with better playlist support) I'd suggest checking out **amarok**.

The wonderful thing about the Ubuntu community is the fact that there are so many people willing to help others out.  If you have a problem with something, search the forums first, because chances are, someone else has had the same problem, and fixed it.  But if you can't find anyone else with the problem, post about it, and someone will help you out.

Welcome to Ubuntu!

---

### Post by richbarna on 2006-06-10
[QUOTE=colo]Quit the trolling/astroturfing, and you will surely get the support you need so desperately.

Next applicant, please.[/QUOTE]

Great way to treat new users !!!
Why don't you try helping instead of trolling/ "astroturfing?" and posting a decent reply.

By the way Kasabian, take a look at the links in my signature, it's tough being new to a system, you will find a lot of excellent information here.
|
|
V

---

