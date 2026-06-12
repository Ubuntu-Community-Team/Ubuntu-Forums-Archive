---
title: "No previous experience with linux."
date: 2008-01-05
forum: Beginner Team
---

### Post by KoolBeans on 2008-01-05
I am new to Linux. Tired of the problems in Winblows. Since I am new there is a learning curve.

When I say new, I mean, tried livecd for two days third day installed on my comp. No previous experience with linux.

I would like to see in Absolute Beginners:
A. Installation
A1. Clean install - step by step, maybe even screen shots.
A2. Install with partition: A.K.A. Dual boot O.S.
B. Initial steps after you install Ubuntu
B1. Nescesary maintenance and setup
B2. Updating
B3. Restricted formats
B4. Things to check to make sure of propper operation. Video, Audio, Plugins, Programs...

Something like this is what I would have expected in a sticky.

A sticky should be limited to posts by Admins, Mods, and certified experienced users. This would create a channel of trusted information that would reduce frustration on first timers not familiar with programming structure and language. Posting to sub threads can be done by those seeking help.

The Topics structure seems a little confusing on the menu page. By looking at it I don't feel I can find what I need by topic and sub topic.

Currently videos on the web sometimes work sometimes don't. Can't download the Macro flash player via add/remove. Unsure how to install the Adobe version. I am not sure how much of these probs are related to my ATI radeon.
I don't have sound right now, not sure how to fix that.

I really need an ABC Guide.

Post #34 would like to see this as a sticky.
Post #49 would like to see this step by step; 3 partitions? What are the benefits and features of this? What are the drawbacks of this? What is microboot?

(I have a Toshiba Satalite A215 7422, Win Vista Premium, Ati video, 160gbhd)-incase someone can point. Using Ubuntu Studio.

Previously posted here- [http://ubuntuforums.org/showthread.php?t=583007&page=9](http://ubuntuforums.org/showthread.php?t=583007&page=9)

Now I just need to find out if I can run Fruiyloops in Linux. And a Firewire m-audio sound card.

---

### Post by rcsarver on 2008-01-05
Installation: [http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020)
or were you just saying it should be sticky?

As far a fruity loops, it may be possible to get it working using "wine". Go to System>Administration>Synaptic Package Manager to install. You may need to add the universe repository (in synaptic, settings>repositories). Otherwise there is an application similar to fruity loops called lmms.

---

### Post by KoolBeans on 2008-01-06
> **rcsarver said:**
> Installation: [http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020)
or were you just saying it should be sticky?

I think that this is closer to what should be in a sticky, needs editing though, it has a lot of extra words.

> **rcsarver said:**
> As far a fruity loops, it may be possible to get it working using "wine". Go to System>Administration>Synaptic Package Manager to install. You may need to add the universe repository (in synaptic, settings>repositories). Otherwise there is an application similar to fruity loops called lmms.

I won't be able to check any of that out until my comp is running 100%. I currently don't have any sound. It begins at boot up. Something about "PCI-no device...", flashed by so fast I couldn't see what was wrong. Maybe there is a boot error log. but don't ask me to search for it in the threads-----\/.

Also the Ubuntu Forums are Bedlam at Best. 
A moderators advice was " to search threads for help". 
Their is no valid logical order to the forum menu structure. Sure it's logical, but not valid. Too put it in other terms; It is loose, and unfocused. I have ten tabs open right now, have closed ten+ more, searching for answers. 
Note these Forums:
[http://www.castlecops.com/forums.html](http://www.castlecops.com/forums.html)
[http://www.wilderssecurity.com/](http://www.wilderssecurity.com/)
in these forums you can navigate to areas where help is close by and knowledgeable people can post where they feel comfortable in answering based on experience. By bringing together the people who need help with x to the most experienced users with valid knowledge. Creating an environment of accomplishment. See.

As a way to cope I started writing a flow chart of how I think the menu structure should look when I visit Ubuntu Forums. I will post it when I finish.

For instance- How do I locate "My Posts"? Is that button in my Control Panel?

Also, the screen capture takes a picture of itself as part of the image.

---

### Post by savagenator on 2008-01-06
I can understand what you are saying, but it is difficult to get everything organized.

I'm not sure if you have seen the [www.ubuntguide.org](www.ubuntguide.org) site, that has a lot of good info. The information for booting dual OS's is there (grub, which is the bootloader, assuming you don't already know that)

And about everything else, you may know this: 
swap: like paging files, except its own partition. Have to have it, if you run out of ram its a doozy
For the other 2 partitions, the benefits of having a seperate partition for /home is so that if you do a clean install, you don't have to erase your data

As for your sound card: 
you will need to find your model, and search the internet for the drivers. You may have to compile it, and thats another lesson. Searching the model in the forums may help, but also may not. If you can't find a person there that had your problem then google is your friend.

the flash player: assuming you didn't find it in the repositories, download it from the adobe site, extract it, and go to it from terminal (using the cd /<place where it is>) and then type ./<script adobe gives you> that will execute and install flash. 

i'm a bad teacher, but I hope i helped.  if everything doesn't work straight off, its difficult and you must learn how to use linux truly. Reading a lot on the forums helped me slowly learn everything

---

### Post by KoolBeans on 2008-01-06
Also, the screen capture takes a picture of itself as part of the image.
Example screen capture:

---

### Post by KoolBeans on 2008-01-06
> **savagenator said:**
> 
As for your sound card: 
you will need to find your model,

How do I use Ubuntu to find all that  is inside my computer?
Windows has device manager, listing the device and manufacturer. What is comparable in Linux?

---

### Post by KoolBeans on 2008-01-06
> **savagenator said:**
> 
I'm not sure if you have seen the [www.ubuntguide.org](www.ubuntguide.org) site, that has a lot of good info. The information for booting dual OS's is there (grub, which is the bootloader, assuming you don't already know that)

This site looks like a place where a hacker collects user info through the browser to better prepare an attack, nothing important there! -The noid in me:)

---

### Post by Sukarn on 2008-01-06
> **KoolBeans said:**
> This site looks like a place where a hacker collects user info through the browser to better prepare an attack, nothing important there! -The noid in me:)

Its supposed to be [www.ubuntuguide.org](www.ubuntuguide.org)
He/She forgot the u after t.

---

### Post by John.Michael.Kane on 2008-01-06
> **KoolBeans said:**
> I am new to Linux. Tired of the problems in Winblows. Since I am new there is a learning curve.

When I say new, I mean, tried livecd for two days third day installed on my comp. No previous experience with linux.

You will find some that will tell you that being new to any OS will bring with it frustration. 

> **KoolBeans said:**
> I would like to see in Absolute Beginners:
To answer the issues below.

A. Installation
There are many way to install Linux/Ubuntu or any distro for this matter. You will not see a one method install. Thus the live install cd, and alternate cd that Ubuntu makes.

A1. Clean install - step by step, maybe even screen shots.
This site [Ubuntu-installing]("http://www.psychocats.net/ubuntu/installing") is as close to step by step you will get short of writing it yourself.

A2. Install with partition: A.K.A. Dual boot O.S.
Again there are many ways to users have set-up dual boot.
[WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")
[Howto dual-boot separately on two HDs]("https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs?highlight=%28dual%29")

B. Initial steps after you install Ubuntu
Every users post install methods will be different. you will have to find what works your set-up, and needs
[http://ubuntuforums.org/showthread.php?t=624916](http://ubuntuforums.org/showthread.php?t=624916)

B1. Nescesary maintenance and setup
Most would tell you maintenance eg: defragmenting anti-virus is not needed. Again you will have to find what fits your particular set-up. 

B2. Updating
Ubuntu updates can be installed by clicking---->System---->Administration---->Update manager 
The other option is the command below run from a terminal.
```
gksudo aptitude upgrade
```

To move from one version to another. Say from 7.04 to 7.10. run the below command.
```
update-manager -d
```

After which the update manager will pop up stating New distribution release '7.10' is available.

B3. Restricted formats
[Playing Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats?highlight=%28formats%29")

B4. Things to check to make sure of propper operation. Video, Audio, Plugins, Programs...
To check your video acceleration run the command below.
```
glxinfo | grep rendering 
```
If the below is shown you installed the drivers properly.
```
direct rendering: Yes
```

most audio chips work from the start,however. those that do not work will sometimes require then end-user to compile support for that driver.

Plug'ins can usually be installed simply by using synaptic
Found by clicking---->System---->Administration---->synaptic

> **KoolBeans said:**
> Something like this is what I would have expected in a sticky.
As said many times there is no one method to installing anything under Linux/Ubuntu or any distro. You may write a method, and someone will still feel there are better ways to do it.

> **KoolBeans said:**
> A sticky should be limited to posts by Admins, Mods, and certified experienced users. This would create a channel of trusted information that would reduce frustration on first timers not familiar with programming structure and language. Posting to sub threads can be done by those seeking help.

First off I disagree. This forum is about everyone being able to contribute. not limiting as you are describing. 

Second who is going to determine a users experience/knowledge

Also just because someone is a mod or has been on this forum or any other forum for a long time does not == knowledge. learning is an everyday event, and even those with massive knowledge of this OS , and others learn something new.

What you describe would IMHO put a lot of people off using this forum, and possibly create a hostel atmosphere.

> **KoolBeans said:**
> The Topics structure seems a little confusing on the menu page. By looking at it I don't feel I can find what I need by topic and sub topic.

The topics of the from page are the main topic of the particular section, and within certain main topics are sub-forums.


> **KoolBeans said:**
> How do I use Ubuntu to find all that  is inside my computer?
Windows has device manager, listing the device and manufacturer. What is comparable in Linux?

To find your machine spec's type either of the commands below in the terminal.

```
lshw
```

```
lspci
```

Next scroll through the info listed till you find the device your looking for in your case your sound card make/model

The other option for finding your hardware info.

Click ---->System---->Preferences---->Hardware Information  

As to your other issues.
[WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

---

### Post by bodhi.zazen on 2008-01-06
First, Welcome to Ubuntu.

Second, thank you to John.Michael.Kane for a comprehensive answer.

My advice is : 

First, patience. As has been said many times, Ubuntu (Linux) is not windows and you can not expect to master any OS in two days :)

Second, as you can see, there is a wealth of information already available, it is a matter of finding it.

The Ubuntu wiki is a great source of information :

[https://help.ubuntu.com/](https://help.ubuntu.com/)

[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

Third, I would echo John.Michael.Kane. This is  community and I advise you learn by participation. You will find that there are many helpful users here, not just mods and admins. In fact, we have an entire team of users committed to helping new users.

In summary : The best way to learn Ubuntu is to use Ubuntu, read, search, and be active with the community. Active participation can not be replaced b a few how-to's or wiki pages.

---

### Post by KoolBeans on 2008-01-06
Thank you for your thorough answer that addressed many of my problems. There may have been areas I didn't clarify properly to convey my ideas well. The Sticky thing.
> First off I disagree. This forum is about everyone being able to contribute. not limiting as you are describing.

Sticky's should contain help info that is the result of someone being helped and not queries for help. By allowing anyone to post to a sticky it can get filled with things not germain to the original idea of such, becoming off topic. See.

> Second who is going to determine a users experience/knowledge

Peer review is the method all use, whether narrow minded or open minded. Peer review is amoral, and the results of same will be the mind of those involved.

> Also just because someone is a mod or has been on this forum or any other forum for a long time does not == knowledge. learning is an everyday event, and even those with massive knowledge of this OS , and others learn something new.

One mod does not a forum make. We are Learning together, you and I, through this discussion. I have learned where to look and prod with, in linux. I have learned of other resources that could improve my understanding of what I need by where I am in understanding. This is the type of info that should be in a sticky at Absolute beginners forum. 
I am not yet frustrated with Linux or UbuntuLinux. If I were I would have wiped and be done with it.  Starting from ground zero allows you to make choices you would not want to make again. Sort of like reincarnation OS style. See.

> What you describe would IMHO put a lot of people off using this forum, and possibly create a hostel atmosphere.

> Third, I would echo John.Michael.Kane. This is community and I advise you learn by participation. You will find that there are many helpful users here, not just mods and admins. In fact, we have an entire team of users committed to helping new users.
In summary : The best way to learn Ubuntu is to use Ubuntu, read, search, and be active with the community. Active participation can not be replaced b a few how-to's or wiki pages.

A clarification...The Ubuntu Forums are Loose and Unfocused. This creates an atmosphere that can breed confusion.
I am suggesting a Loose and Focused environment in Ubuntu Forums. That can only occur by reorganizing the Ubuntu Forums page structure. The data will not change just a new perspective of the data. See.

Again, Thank you. I am nominating you for Certified/Experienced User.

How do I locate "My Posts"? I can check my PM but not my Posts.

If I get frustrated Here I may get my own vBulletin. Can anyone point where I can learn what I need for MySQL and PHP or the Linux equivalents ;)

---

### Post by ugm6hr on 2008-01-06
> **KoolBeans said:**
> How do I locate "My Posts"? I can check my PM but not my Posts.

In any thread - just click on your own name. It will bring up a list of options, including "Find all posts by Koolbeans"

As for structured documentation, there are plenty of sites, including [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

As previously mentioned:
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

---

### Post by John.Michael.Kane on 2008-01-06
To locate all your postings.

Click-----> Search a panel will show listed at the bottom is the option Find All My Post, as well as find All My Threads

This will bring up either all your post, and the threads they were made in Or any direct thread you were the OP in.

Edit:ugm6hr method works as well.

Regarding sql/php.
[URL="http://us3.php.net/tut.php"]php a simple tutorial
[/URL]
[PHP / MySQL Tutorial]("http://www.tizag.com/mysqlTutorial/index.php")

For further info/help advice you might want to ask around [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39") section of the forum.

---

### Post by Samhain13 on 2008-01-06
edit: beaten by above poster. :)

> How do I locate "My Posts"? I can check my PM but not my Posts.

Click on "Search" and it will bring down a box. The item you're looking for is at the bottom.

I agree with you, although I've learned to live with them, that many features of the forum aren't very helpful. And my personal gripe is with text resizing and how the layout breaks with it.

---

### Post by SunnyRabbiera on 2008-01-06
> **KoolBeans said:**
> Also, the screen capture takes a picture of itself as part of the image.
Example screen capture:

this is from the desktop effects manager if you are using it, its a glitch mainly seen in gnome, the window manager of ubuntu (what you use)

---

### Post by KoolBeans on 2008-01-06
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
        Subsystem: Toshiba America Info Systems Unknown device ff0a
        Flags: bus master, slow devsel, latency 64, IRQ 16
        Memory at f8600000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

This is a result of lspci -v, or the audio portion. How do I determine if this is true or what Linux has loaded for the device?

 *-multimedia
             description: Audio device
             product: SBx00 Azalia
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=64 module=snd_hda_intel

This is the audio snippet from lshw. Question remains the same as above.
Also, if it isn't working what now?

---

### Post by bodhi.zazen on 2008-01-06
> **KoolBeans said:**
> Sticky's should contain help info that is the result of someone being helped and not queries for help. By allowing anyone to post to a sticky it can get filled with things not germain to the original idea of such, becoming off topic. See.

Allowing comments does not detract from the original posting in a sticky and encourages feedback and community involvement. You are free to read through the comments or not.

> Peer review is the method all use, whether narrow minded or open minded. Peer review is amoral, and the results of same will be the mind of those involved.

The Ubuntu way is that we are all equals. I know a little of this, you a little of that, and together we form a community that is greater then the sum of it's parts. ~ see my sig.

> A clarification...The Ubuntu Forums are Loose and Unfocused. This creates an atmosphere that can breed confusion.
I am suggesting a Loose and Focused environment in Ubuntu Forums. That can only occur by reorganizing the Ubuntu Forums page structure. The data will not change just a new perspective of the data. See.

You are of course entitled to your opinion.

The Forums are just that, ongoing discussions and I am not certain how one would moderate such discussions.

Searching the forums has it's role, but also it's limitations. To get the most out of any discussion, forums or otherwise, I encourage active participation.

As far as format / organization, this has also been discussed. While there is no perfect system that will please all of the people all of the time, the current system is working for most of the people most of the time and it is hard to do much better then that.

Last, I think you will find some of what you are asking on the Wiki. The wiki is much more of a text then a discussion and the wiki team is large and active.

> Again, Thank you. I am nominating you for Certified/Experienced User.

LOL

> **KoolBeans said:**
> This is the audio snippet from lshw. Question remains the same as above.
Also, if it isn't working what now?

I don't know, what now ?

I suggest you start a thread stating your problem and I would assume you will get some help. This thread, however, in not in a support section. As you have posted in the Beginners Team section I have answered as I see the Beginners Team role.

---

### Post by KoolBeans on 2008-01-07
Oh yes, How do I thank someone?

---

### Post by John.Michael.Kane on 2008-01-07
> **KoolBeans said:**
> Oh yes, How do I thank someone?

Press the gold,and blue medal icon that should be in the members post you wish to give thanks for.

---

### Post by bodhi.zazen on 2008-01-07
> **KoolBeans said:**
> You and I are not equal. Our experiences, which are a summation of our choices, make us unique.

I always though of equal different from you. The ERA amendment for example does not say that men and women are the same.

To me equality means treating people with respect and kindness despite our differences. I do not perceive my self as better or superior to you or anyone else simply because I am a moderator.

> What makes you differnt than me is that your signature is at odds with your personal beliefs.

It is ?

> Then how is it that you are on the Forum Staff if you can not manage the pages your title says you have permission to do?

We do not manage the forums in the way you envision. We do not dictate or regulate the conversations per se. We monitor for inappropriate behavior or language, as you can see in the language filter you encountered. We also field complaints between community members, delete spam, etc. Basically we enforce the [Code of Conduct](http://www.ubuntu.com/community/conduct)

> Why would one so high up choose to humble himself and spend time providing counter point to valid queries and not provide any helpful diatribe? 
In other words you are blowing smoke up my ar_se. Helping to foster confusion, which is your tool to distract those who would embodie what is in your signature.

I am sorry you feel that way. I feel I have taken the time to explain a little of the forums and the philosophy to you, and how and why it is the way it works. We may differ on our perspectives, but there is no need for you to be insulting.

How can I be of assistance to you ?

---

### Post by LaRoza on 2008-01-08
I see a lot of negativity directed towards bodhi.zazen. 

I would like to counter that by saying they (the mods) do a good job in enforcing the Code of Conduct and are very good members of the community.

---

### Post by Dr Small on 2008-01-08
What in the world???
This thread looks like something I would have read in the backyard!

I'm all for Bodhi.Zazen

---

