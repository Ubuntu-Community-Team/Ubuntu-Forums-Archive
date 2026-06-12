---
title: "Dapper Updrade Disaster!!!"
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by catlett on 2006-05-18
I followed this thread [https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades)  That I got in a reply from this thread I posted [http://www.ubuntuforums.org/showthread.php?p=1023808#post1023808](http://www.ubuntuforums.org/showthread.php?p=1023808#post1023808)
The results, total destruction of my configuration.
I didn't really want to upgrade because I had my Ubuntu system the way I wanted it. I ran Automatix when I first installed, I mounted my other volumes, configured my printer and everything else I wanted. But I enjoy posting in the forums and helpling out. It seemed like more and more new people were coming into ubuntu with dapper and I thought if I am going to help I'll need to run Dapper so I'll know the advise I am giving will work.
Anyways I installed by doing```
 gksudo "update-manager -d"
```
The update manager alerted me to the dapper release and I said O.K. The install ran. It took longer than my original cd install. It finished and said to reboot.
Upon rebooting my x server wouldn't start. I ran sudo dpkg-reconfigure xserver-xorg and got my x to start but I am lucky I have been active in the forums and my learning has accelerated. I only installed 2 months ago. I knew nothing about linux 60 days ago, if this happend a month earlier I would have been really stuck.
After x started I started to notice all the other changes. None of my media cards or flash drives were mounted. They always mounted automatically. My windows partition is not mounted and I mounted that with the ubuntu thread about captive nfts. Also in "My Computer" folder none of my cd drives are there, None of my removable media is there.
I have an mp3 file on my desktop. I like to hover my mouse over it and hear it now and then (long story). That doesn't play any more. I put a dvd in to see if anything would happen. It didn't autoplay or give me a dialogue box. When I tried to open Totem to see if I could play it in Totem, Totem crashed.My nvidia drivers are no longer instaled. 
This wasn't an upgrade but a degrade. My cd install of Breezy was more functional than my Dapper upgrade.
Now here are my questions. Is this because I had Automatix install al my multimedia? Is it because I removed the Automatix repo list? Was I supposed to save copies of certain configuration files to copy over later?Is this because it is still a beta? Was I wrong to think my configuration would be the same? Should I have viewed an upgrade as if it was a new install?
If this is to be expected are people going to be warned? Like I said earlier, if this was a month ago I'd be really bummed out and mad that I upgraded. I'm lucky enough that I have learned enough that I can reinstall everything and remount but others might not.
Well I upgraded so I could pass along informed advice and it seems my first advice is to make sure you find out how to save your configuration. Whether it be your xorg file or your /etc/fstab or whatever. This may be a fluke but I ran the install through the upodate manager, followed all prompts and ended up with a command line and alot of work ahead of me.
Lastly excuse me if I don't repost. The last 2 days I can't connect to the Ubuntu forums. All I get from firefox is "server not responding timed out". I can't conect although I connect anywhere else on the internet. To post this I had to hit "retry" in firefox 3 times. I hope this is a fluke..
One more note. I truly enjoy Ubuntu very much and this mishap just gives me something to do this weekend.  I wanted to put it out there in case other people assumed like me that nothing would change they might not have the weekend to reconfigure their install or might not have learned enough about Ubuntu to reconfigure it.

---

### Post by &amp;)ky#)^ on 2006-05-18
As far as your partitions go, you'll need to work on fstab.  It may help to use a command like fdisk on your hard drive to get info about your partitions.

```
sudo fdisk /dev/hda
```

This is my first time helping someone on the forums, so I hope you find this helpful.

---

### Post by Sef on 2006-05-18
If you can download and burn a rescue disc, this one has captive built in.

[http://trinityhome.org/trk/]("http://trinityhome.org/trk/")

---

### Post by macdo on 2006-05-18
Interesting, if rather surprising.
I only had one problem when I installed Dapper on my laptop: the wireless network card stopped working. The only difference that I can see between you and me is that I reinstalled from a disc, and reformated (okay, so it's not the same thing at all :-) ).
I have to say that I really like Dapper, and have no problems at all with it. It's been on for over a week now, and has had a lot of use in that time. As I say, the only problem that I have had is my Linksys WPC54G wireless card, and I was expecting problems with that (Shorthand solution: install ndiswrapper, install windows driver, rmmod the broadcom kernel module, rmmod ndiswrapper, modprobe ndiswrapper - it doesn't make sense, but it works. If it ain't broke...)
My guess is that something went badly wrong during the upgrade procedure - but what?
If you ever find out, let us know, will you?

macdo

---

### Post by richbarna on 2006-05-18
Woah! Damn that is SO not good !! 
Sorry to hear about your problems, but thanks for the warning, I was going to upgrade tonight.
And Dapper is going to be ready on June 1st ??
I think I'll wait a bit, I've got Breezy just how I like it at the moment.
I don't mind having a few problems to learn from, but hey, that's a bit much.
And to think, everyone is worried about BUMP and Automatix in Dapper. What about worrying about a seamless upgrade first ?

---

### Post by Sef on 2006-05-18
If you do a dist-upgrade, you run a higher chance of having problems than by doing a clean install (reinstalling the os on a disc.)

---

### Post by richbarna on 2006-05-18
Still a bit worrying having to go through the dvd setups, hard-drive mounts and printers and graphic and tv card configs etc.
I am still reading a lot of posts regarding things that still don't work in Dapper. Do you think it will be ready for June 1st ?
Are there a lot of improvements regarding hardware support etc?
I finally got Ubuntu Breezy how I like it, and am not sure if to wait a while.
Although I have also heard how GOOD Dapper is.
Hmmm, decisions, decisions.

---

### Post by BjornHaland on 2006-05-18
Thanks for posting this, I also have upgrading issues. There's always something.

I'm new to this also. I have one question: 
When the final release is out, and upgrades keep coming, should we expect similar issues when upgrading?

---

### Post by Sef on 2006-05-18
> When the final release is out, and upgrades keep coming, should we expect similar issues when upgrading?

This is going from one version to another (sudo apt-get dist-upgrade).  Simple upgrades (sudo apt-get upgrade) will not have this problem.  

This is why a clean install is recommended.  (A clean install is installing from a disc.)

---

### Post by catlett on 2006-05-18
Hi everybody,
Glad to see some familiar avatars. Well for an update. Things were so bad I put in a Dapper 6.04 disc I burned a while ago but didn't use. I ran a clean install. The one good thing is I don't run a business or work from my computer, it is a recreational device for me. So reformating is not a big thing because I don't have important files. The only thing I would want to save would be my configuration and I already told you where that went.
I ran the cd install. It was faster than sudo update-manager -d. Once 6.04 was up and running I was alerted to 485 updates. I ran them right away. No need to put time into an install if I was just going to loose it. It recommended doing sudo apt-get dist-upgrade instead of updating through the manager because of all the packages to be removed.
Update went great. Everything was detected. Everything I entered during partitioning was mounted. I have a clean Daper 6.06 install now. Right now all I can say is I like the skin. The icons are nice etc.
My advice to others. I never made a home partition before. I did not understand install enough to configure it. So I had home and root on the same partition. This time I'll make a home partition and if I upgrade next time I will do a cd upgrade. Let it reformat root and install a new file system but leave home alone.
In the end I just wanted to pass my experience along for whatever it was worth. This is the type of feedback I like to see from people when I'm looking for information on something. 
See you around the forums, you should notice me I'll be the one looking Dapper:D (bad joke I know but give me a break it's been a long day)

P.S. One issue. In my "media" folder I have 12 cdrom folders. cdrom, cdrom0, cdrom1 thru 10. As well as 10 floppy folders. floppy, floppy0, floppy1 thru 8. Anyone know what is causing this?

---

### Post by confused57 on 2006-05-18
catlett,

Thanks for sharing...I've really had to resist the urge to dist-upgrade my Breezy install on my main system, your experience helps me wait a little longer.  I have Dapper and Xubuntu installed on an old "test" computer, think I'll just continue to mess with it on the old pc.

I've seen other people in the Dapper section have the same problem with multiple floppy & cd drives, hopefully the bugs will be worked out eventually.

I've installed Breezy in the past(on the test machine) setting up a separate /home partition...I mainly used the screenshots from Herman's dual boot site for this & it actually worked.  At least the newest Dapper install cd has a graphical install interface.

Keep us updated...this is how we all learn...for some(me) it takes a little longer to figure things out.   Dist-upgrading isn't something for the "faint of heart", sure can unintentionally learn a lot though while troubleshooting.

---

### Post by nalmeth on 2006-05-18
I'm not suprised at configuration's being lost with an upgrade. New version's of everything are installed, and their configuration's change too.

I've had total failure from two dapper upgrades, but this was sometime back.

I prefer a fresh-installation. Doesn't take me long to set everything up.

I think it would be nice to see a Dapper Upgrade Troubleshooting guide of somesort, including warning's about certain package updates that are known to cause problems.

---

