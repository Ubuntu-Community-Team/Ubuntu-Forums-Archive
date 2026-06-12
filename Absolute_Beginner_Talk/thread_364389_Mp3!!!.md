---
title: "Mp3!!!"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by lemdiah on 2007-02-18
I'm new to Ubuntu and I found this site...:) 

I want to use other OS other than Windows... And I'm having a hard time figuring out what to do with Ubuntu...

I'm currently using Ubuntu 6.06 LTS (Drapper Drake), I just saw the codename on some other sites... My problems are:

[B]1)I cant play MP3 on Jukebox or even if I double click the mp3 file it wont play, just the error message.

2)I cant play my VCDs and DVDs.

3)I dont know how to use UNIX commands.(That's the worst!)[/B]:confused: 
	](*,)
I want to learn how to do all this things... as for now I really want somebody to teach me first because I cant concentrate studying if there's sound playing on my computer(OK so there's Windows but I really want sound on my Ubuntu). And I cant watch some of my movies on Drapper Drake... Please guys help me out here...

Please somebody help me... TVM!

P.S.:Total Newbie...

---

### Post by kinematic on 2007-02-18
[automatix](http://www.getautomatix.com/) can install every codec you need plus a bunch of other stuff such as java,flashplayer and nvidia/ati drivers.
just read the wiki and follow the instructions ;)

---

### Post by Bigbluecat on 2007-02-18
Ubuntu does not include support for MP3, DVD etc. by default becasue they are proprietary codecs. To enable them you need to specifically request their support. Have a look at the following link:

[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/codecs.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/codecs.html)

Now the first thing you need to do is enable the multiverse and restricted repositories. 

Start Synaptic package manager - you will find this in the system admin menu.

Once open you need to go to the settings menu and select repositories. Now make sure to tick the multiverse and restricted repos.

Exit those menus and hit reload in the top right. Now search synaptic for the gstreamer items listed in the above link and install them.

This will not take care of everything but will get you started.

I would also suggest a quick read of this link which will explain a few things and provides guidance for getting started.

[http://www.ubuntuforums.org/showthread.php?t=232059](http://www.ubuntuforums.org/showthread.php?t=232059)

You can also try some of the programmes that automate some of these tasks.

Easyubuntu and Automatix are quite popular although there are mixed views on the forums about them. Some people have problems when it comes to upgrades and others don't like them on the grounds that you will not learn as much by using them.

[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

[http://www.getautomatix.com/](http://www.getautomatix.com/)

Whichever way you choose - good luck. Welcome to Ubuntu. A little bit of patience and learning will go a long way.

---

### Post by PurplePenguin on 2007-02-18
These guys beat me to it, so I won't go over the details that they covered.  But I just wanted to add that it is very easy to add the stuff you need for multimedia (and should only get easier with the next version of Ubuntu that's coming out).  

It'll take a little bit of getting used to, but you'll be flying with Ubuntu in no time.

Here are a couple links that I really think might be useful.  [Ubuntu Guide for Dapper]("http://ubuntuguide.org/wiki/Ubuntu_dapper") and this thread called [Useful Terminal Commands for Newbies]("http://ubuntuforums.org/showthread.php?t=363055").  It's got some good tips, like using TAB to complete commands and stuff like that. :)

---

### Post by lemdiah on 2007-02-18
I really want to tell you guys... I'm a newbie and I'm a total idiot in this Ubuntu thing and I'm just starting... I just installed Ubuntu yesterday and my OS just go heyhow...

Can you tell me a step by step procedure on how to use my mp3 files on my Ubuntu???

I have gstreamer10 installed on my computer and As I had remember I think I did the the restricted and multiverse thingy...

I put check on all restricted icons and multiverse...
I did not put check on those that has universe...

Am I doing wrong???

I dont know how to install anything on my Ubuntu...

I have Netbeans for Linux/Ubuntu which I cant install and some other applications which I really want to use in my Ubuntu...

Automatix??? will it be available in other versions of Ubuntu???

I'm currently using Ubuntu 6.06LTS(Dapper Drake).

step by step pls... I dont know any UNIX commands...

---

### Post by Maestro23 on 2007-02-18
Some links to get you started lemdiah:

Installing in Ubuntu: [http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)
                              [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Restricted Formats: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Common Terminal commands/Linux File Structure: [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Enjoy and Good luck.:popcorn:

---

### Post by MetalMusicAddict on 2007-02-18
lemdiah. Is there any particular reason your using Dapper? You should really use Edgy (6.10)

---

### Post by lemdiah on 2007-02-20
The Reason why I'm using Dapper Drake is that its what I have right now...

---

### Post by lemdiah on 2007-02-20
Please dont treat me like I know something already... My Ubuntu is going nuts already... I tried reloading the synaptics but all it show is an error on four new components... and to ask me what component was an error??? well I just followed the you all said... I told you I'm a newbie and you cant put to my mind to to this and that and read this and that without me knowing what's all that...

Ok so let me start... It's like programming... I have to start from the question from my head... How do I enable MP3??? Again I know it seems stupid but please try to help me out here... Its been 3 or 4 days and still no progress... What do I do now??? So I have gstreamer10 and the other one said it will make a new but will not enable mp3... doesnt make sense... and your link to some website contradicts what you said... It said to unistall the gstreamer and save a backup which I really dont know how to... and a lot of mixes going on in my head and I cant seem to get it right because A lot of new things suddenly comes in my head... like sudo whatever... For short... Data Overload(In my brain)... 

I really want to know how to enable mp3 files to open and somehow things get so complicated... so OK i have the netbeans not working too... lets just start on mp3... Please guys help me...

I'm using Dapper Drake(Which is the CD i got and the free latest one from Ubuntu). That's Ubuntu 6.06 LTS...
How do I start??? what do I do??? Please no links... I tried reading the links and it gets more complicated because it directs me to sometimes a different concept and some even contradicts to one another... I'm already getting frustrated... I havent use any OS... not Even Linux... and not even MacOS... so imagine me as a one eyed Windows guy and wants his other eye to open up so he can see the light in Ubuntu...

---

### Post by ycmarvin on 2007-02-20
Hey lemdiah. Im newbie with ubuntu too, I'm using edgy.

Since you are seeking a step-by-step procedure. I'd suggest;

(1) In this forum section (Absolute Beginner Talk), there is a sticky post entitled 

READ THIS FIRST prior to posting - IMPORTANT links

Read that first because that thread contains links that are valuable to newbies like us. Try going one article at a time.   

(2) Then Go back here in your thread, the replies above have plenty of useful tips for you. Like in number 1, try one article/site at a time. Like if you're going to get automatix, read everything you can get about automatix.

Good luck!

---

### Post by Maestro23 on 2007-02-20
> **ycmarvin said:**
> Hey lemdiah. Im newbie with ubuntu too, I'm using edgy.

Since you are seeking a step-by-step procedure. I'd suggest;

(1) In this forum section (Absolute Beginner Talk), there is a sticky post entitled 

READ THIS FIRST prior to posting - IMPORTANT links

Read that first because that thread contains links that are valuable to newbies like us. Try going one article at a time.   

(2) Then Go back here in your thread, the replies above have plenty of useful tips for you. Like in number 1, try one article/site at a time. Like if you're going to get automatix, read everything you can get about automatix.

Good luck!

Very good advice.  Walk before you try to run.

---

### Post by Strider42 on 2007-02-20
Lemdiah,

I'm a 3 week Ubuntu virgin too, and I would say, stick with it.  It really is a new way of working, but once you read the support forum and ask a few questions you'll be flying.

I now have my laptop setup and running a sweet as anything.  I have VMware installed and running XP for my work software plus Edubuntu that I'm researching before adding to my kids machines.

You will get it all to work, it's a big learning curve, but well worth it.  And you'll learn loads too.

Good luck.

Paul

---

### Post by anaconda on 2007-02-20
(from the restrictedFormats page: )
Ensure the relevant repositories are enabled. Click System &#8594; Administration &#8594; Synaptic Package Manager &#8594; Settings &#8594; Repositories and then click Add. Check the Community maintained (Universe) and Non-free (Multiverse) boxes. When you close the window, click Reload.

If you already succeeded in enabling the multiverse and universe repositories then just copy-paste this command to terminal.. it will install mp3 support and also support for several movie codecs etc..

```
sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui
```

---

### Post by humbll on 2007-02-23
Step 1: Install AUTOMATIX by clicking here (it will ask you if you want to open or save, pick OPEN it This is for Dapper Drake):
[http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/automatix2_1.1-2.10-6.06dapper_i386.deb](http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/automatix2_1.1-2.10-6.06dapper_i386.deb)

Step 2: After AUTOMATIX is installed, run it from the APPLICATIONS menu (click APPLICATIONS-->SYSTEM TOOLS-->AUTOMATIX)
When you open it it will give you a disclaimer, click ACCEPT, when the program loads, look in the box on the left you will see several choices one of which is MULTIMEDIA, click on it.

Step 3: Now look in the right hand window and you will see various things, scroll down and find the one called MULTIMEDIA CODECS (the description under it will say "COMMONLY NEEDED AUDIO and VIDEO CODECS) Click on it.

Step 4: At the top of the AUTOMATIX window, just underneath FILE and VIEW you will see a button called START with an orange arrow pointing to the right. Click on it.

That is it. Now you can just doubleclick on the MP3 and it will play.

Happy listening!

---

