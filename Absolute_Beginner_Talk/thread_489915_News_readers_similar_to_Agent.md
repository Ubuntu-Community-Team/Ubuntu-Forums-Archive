---
title: "News readers similar to Agent"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by valhalla2100 on 2007-07-01
Hello,

I got a new computer.  The clerk installed Ubuntu on it.  I like it so much that I am want to use it as my main OS for accessing the internet.   

Now, with Windows, I use Agent.  I like it because I can download all of the postings to specific groups and, for MP3 or other binary files, can select files for batch downloads.

Does any similar program exists for LINUX?

I am planning on switching to a new news groups provider.  Am interested in newsgroupdirect.com, but
if I find a better provider I will go with that.

Thomas

---

### Post by linuxfan2007 on 2007-07-01
pan is a great Linux based reader.

not as feature rich as Agent might be, but work quite nicely!

apt-get install pan

you should be able to do the rest.

---

### Post by djchandler on 2007-07-01
> **valhalla2100 said:**
> Hello,

I got a new computer.  The clerk installed Ubuntu on it.  I like it so much that I am want to use it as my main OS for accessing the internet.   

Now, with Windows, I use Agent.  I like it because I can download all of the postings to specific groups and, for MP3 or other binary files, can select files for batch downloads.

Does any similar program exists for LINUX?

I am planning on switching to a new news groups provider.  Am interested in newsgroupdirect.com, but
if I find a better provider I will go with that.

Thomas

Go to the top menu bar, and select **System**, then select **Administration**, then select **Synaptic Package Manager**. You will then be asked to enter your main account password so you can make a change to the system, which is called becoming the **superuser** or abbreviated as **su**.  The Synaptic Package Manager will then launch. On the left you will see the word **All**, and buttons below as well. In the right upper window, you will see names of programs, and installation status with a short description. Below that is a window which will give a more detailed description of a program package highlighted in the window just above it. Click on the button labeled **Sections** on the lower right. You will notice the window above now has a bunch of selections. In the upper right window, scroll down to **Newsgroup**. Two program package names will appear, **Gnus** and **Pan**. I think you will want to try Pan. Click on the box next to Pan, and select **Mark for Installation**. You will get a curved arrow in the box. Click on the check mark above the right upper window to apply the change. Now you know how to add any program you will need in Ubuntu. Below is the description for Pan.

Welcome to the Ubuntu Forum. I see somebody beat me to telling you to get Pan, but this way is easier if you are new to Linux.

Have fun!:popcorn:

DJ

> 
A Newsreader based on GTK2, which looks like Forte Agent 
Pan is a newsreader, loosely based on Agent and Gravity,
which attempts to be pleasant to use for new and advanced
users alike. It has all the typical features found in
newsreaders and also supports offline newsreading,
sophisticated filtering, multiple connections, and a number
of extra features for power users and alt.binaries fans.


PS Sorry I'm so slow with my reply. I have a little trouble typing very fast for the time being

---

### Post by Howard Kaikow on 2007-07-02
Speaking of Pan, I just installed the critter a few daze ago.

There is no user manual, so I am having difficulty finding out how to do the following.

In Outlook Express, I can set up multiple accounts and have separate subscriptions in each account.

With Pan, all the subscriptions seem to get lumped together.
I see a menu for specifying a group name, but I do not see any info on how to use it.

I would like to categorize subscriptions, at least, based on the server.
Better yet, any way I wish, can this be done with Pan?

---

### Post by qpieus on 2007-07-02
valhalla2100 - what version of agent are you using? The reason I ask is that Agent up to v3.3 work very well when run under wine. I've tried v 4.0 and above also, but they don't work right. If you're happy with v3.3 though, then you can have your linux and agent goodness at the same time.

---

### Post by djchandler on 2007-07-02
> **qpieus said:**
> valhalla2100 - what version of agent are you using? The reason I ask is that Agent up to v3.3 work very well when run under wine. I've tried v 4.0 and above also, but they don't work right. If you're happy with v3.3 though, then you can have your linux and agent goodness at the same time.

qpieus,

Do you know if Gravity works under Wine? It fits my needs like it was written just for me, but even though it is FOSS, there's not a Linux version. Just curious--I have an XP box still, so I have not considered running Wine yet. I finally have a processor in my Ubuntu box that may be capable of running it.

DJ

PS Maybe I should go to the Wine website myself and see if anybody else is running it. The website is [http://www.winehq.org/](http://www.winehq.org/) :)

---

### Post by djchandler on 2007-07-02
> **Howard Kaikow said:**
> Speaking of Pan, I just installed the critter a few daze ago.

There is no user manual, so I am having difficulty finding out how to do the following.

In Outlook Express, I can set up multiple accounts and have separate subscriptions in each account.

With Pan, all the subscriptions seem to get lumped together.
I see a menu for specifying a group name, but I do not see any info on how to use it.

I would like to categorize subscriptions, at least, based on the server.
Better yet, any way I wish, can this be done with Pan?

That's one of the things I like about Gravity, but its other options make Outlook Express look just like the rudimentary program it is meant to be. If you think you have options in OE, Gravity will blow you away. I'm not sure about Pan, as I don't use it--I still use that other OS for enough stuff, I can let Gravity run in the background while I'm working on something else. I like this idea of using Wine for some of this stuff we like that only runs under that other OS.

DJ

---

### Post by qpieus on 2007-07-02
Don't know about gravity, I have not used it. Give it a try with wine though, you can't hurt anything :)

---

### Post by djchandler on 2007-07-02
> **qpieus said:**
> Don't know about gravity, I have not used it. Give it a try with wine though, you can't hurt anything :)

Just checked the Wine Application Database.

> Best Newsreader (at this version free). The Gnome-Newsreader \"Pan\" was modelled after Gravity. GUI works fine, but storing data in gravity\'s internal database doesn\'t work. So at this time is unusable.

At least we're getting beans. Where did valhalla2100 go? :p

DJ

---

### Post by alienexplorers on 2007-07-02
I use Pan and it works great on all different usenet news services.  Downloads amd decodes binaries and mp3's.

---

### Post by Manasia on 2007-07-08
I just installed Pan, I have not used it yet, but I must say that it blows somewhat because it can only use 4 connections. :-( My News service allows 8

---

### Post by Lord_Vacuity on 2007-07-08
I have been using Pan since I started using Ubuntu and it works just fine. Or I should say it worked just fine until last night. Now it won't open.  I even tried running it from the command line and I get the following message:
> pan: fptools.c:458: _FP_fgets: Assertion `*buf' failed.
Aborted (core dumped)

I didn't make any changes to Pan that I know of. Anybody help me figure out how to fix it.

I've tried :icon_frown::icon_frown::icon_frown::(:( Thunderbird's newsreader but it doesn't support yenc so I end up with a lot of gibberish in some of the binary groups.

---

### Post by Old Pink on 2007-07-08
[http://www.mozilla.com/en-US/thunderbird/](http://www.mozilla.com/en-US/thunderbird/)

Mozilla Thunderbird. 

Email Client and RSS reader. Used on my setup for both, you could use it for either. :) 

Not sure how feature rich it is, all I know is it syndicates RSS 2.0 with images, etc perfectly. Not sure what other features you can have in an RSS syndication tool really, I'm sure there's loads but if you're just looking for something reliable and well known, Thunderbird is the one for you.

Available in the repos, so you can install it via Applications > Add/Remove :)

---

### Post by Lord_Vacuity on 2007-07-08
Pan is supposed to look like Agent. I like Agent. That is what I used over in that other OS. Pan is not quite Agent. My Pan stopped working. I read in here that older versions of Agent would work under Wine. I have the latest Wine. I downloaded the Latest Agent. Installed it with Wine. Voila! I now have Agent running in my Ubuntu!!! O frabjous day! Callou! Callay!

---

### Post by Manasia on 2007-07-10
Pan is working like a charm for me. I get great download speeds. I wish I could setup viewing messages like I did in agent, but I got a workaround for that.

---

### Post by Lord_Vacuity on 2007-07-11
As I said, I got Forte Agent working by using Wine. It works great. The only thing that isn't working is launching files because there are no mime pairings possible since wine apparently does not see the hidden linux folders so I can set up image viewer or ida as the goto program. I thought to install Irfanview into the Wine folder but that requires some windows library that I it did didn't find in Wine.  No biggie though because Pan didn't have a launch capability either.  At least with Agent, I can open the attachment folder from the context menu. 

and my news server allows 10 connections and agent can be set for 10 connections

---

### Post by qpieus on 2007-07-11
> **Lord_Vacuity said:**
> I have the latest Wine. I downloaded the Latest Agent. Installed it with Wine. Voila! I now have Agent running in my Ubuntu!!! O frabjous day! Callou! Callay!

So you have agent 4.2 and the newest wine working well? I tried agent 4.2 about a month or 2 ago with wine and it wouldn't start up. I'll have to give it a try again, wine must have had an update that had the nice side effect of making the newest agent work. Yay. Please post your wine and agent versions.

Regarding launching of files. Yes, that doesn't work great with agent/wine. There are a few thing you can do though. As you pointed out, Irfanview doesn't seem to work. But, I have an old copy of ACDSee which works fine with wine. Once it's installed, you can use agent's mime type setup to associate picture files with ACDSee. Works fine. BTW, you do know that Agent 4.2 has an image preview function that might eliminate or cut down the amount of times you actually need to launch a picture viewer app? (it did for me)

Also go find a windows notepad.exe file and place it in the wine fake c: directory. Then you can associate txt or nfo files to the notepad.exe file and launch them right from agent. Works fine although there's a slight lag in opening the files. It's still better than having to save the files somewhere and then open them manually.

---

### Post by Lord_Vacuity on 2007-07-12
Yes, I have Agent 4.2/32.118 and Wine 0.9.40 which I downloaded from WineHQ.org not from the repositories. I originally tried to use the old Wine to access the Agent 4.2 installed in my XP hd but that didn't work. So I re-downloaded Agent and installed it using the New Wine and voila! 

When I close Agent, I do get a message about a memory dump and asking me if I want to forward it as a bug to Forte, but as it hasn't seemed to have messed anything up I just close it and continue on my merry way.

---

### Post by qpieus on 2007-07-13
OK, I have Wine 0.9.40 also, from the winehq repository. I'll give Agent 4.2/32.118 another try. I've also seen that memory dump error, and I agree it doesn't seem to cause any problems. When I tried Agent 4.2/32.118 before, I got agent to open right after it installed (when the installer asked if I want to run agent now). But after that initial start, it would not start up any more. When I closed agent after that initial and only start is when I got the memory dump error. Thanks for the info....

---

### Post by Lord_Vacuity on 2007-07-13
FYI there is an even newer Wine in the repositories today. 0.9.41

---

