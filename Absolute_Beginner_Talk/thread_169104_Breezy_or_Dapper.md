---
title: "Breezy or Dapper?"
date: 2006-05-01
forum: Absolute Beginner Talk
---

### Post by XPerienced on 2006-05-01
Hi!

When I installed Breezy I got seleveral problems with sources.list. Apt-get didn't find the packaged, where unable to install the and jada jada jada.

I got me so mad I almost gave up the idea to migrate, but with some support I made it quite well. Not exactly the way I wanted, but almost. It's good for now.  

Later it's possible to reinstall everything and make it perfect.

But now, I'm about to migrate my desktop so if I'm going to stay with Linux, this got to be more smooth, less problems, less frustration etc.

That's why I'm asking you guys here a question, or some questions:

Is it less problems with apt-get in Dapper then in Breezy? If I just use the standard packages like OpenOffice etc. should I say.

If I'm installing the latest release of Dapper (I know it's a beta, but it's pretty far gone I guess due schedule final release about one month), can it be update so it's like the final release? Or is it necessary to install the final release and do all configuration from the beginning so I won't have "bad files" which doesn't exist in the final release?

I hope you understand what I mean.

XPerienced

---

### Post by olsonar on 2006-05-01
When the final release comes out, the beta will just upgrade to it.

```
sudo apt-get update && sudo apt-get dist-upgrade
```

will be all you need to do.

---

### Post by DooX on 2006-05-01
Olsonar did you just said that with those commands are possible to upgrade whole distro?From Bagger to Dapper?I didnt know that is possible in Linux,its not possible in Windows which is less funkcional.

---

### Post by XPerienced on 2006-05-01
olsonar:
Thanks. You answered the most important question, but I need to the other as well.

Is it easier to make apt-get work i Dapper drake? I heard both yes or no. The latest was that Dapper was better, but needed work experience than Breezy.

I can try both, but I believe Dapper is better cause it more developed. Ubuntu is Linux everyone so my guess is that they are trying to make it easier and more functional. So apt-get should work better, but that just my guess.

DooX:
I think you can downgrade aswell. Linux is much better and if it get a little less frustrating to confiugre, it will be awesome! Don't misunderstand me. Things like apt-get is excellent, but apt-get didn't work properly in the beginning for me and that made me mad.

And I think problems in the beginng scares people who been running Windows for several years. I've been running it for over 10 years so this is a very special step so I don't want problems five-ten minutes after the installation is complete.

/

Some other problems is hard too know for an inexperienced guy like me. I tried to install Fluxbox on the Ubuntu serverinstallation and that didn't work. I had problems before I finally got IceWM to work, but I had to install packageds I didn't want to install.

So there's more to do, or more to read for me. :-) You can se it for more than just one angle... But I can read as long as I find a nice Ubuntubook on the library or something here.

But I got be easy to find, served. Read this, this and this and you know the basics. And read this if you would like to know a little bit more. The FreeBSD Handbook has about 1100 pages and that scared me so much I took Ubuntu instead. 

XPerienced

---

### Post by Nequeo on 2006-05-01
[QUOTE=XPerienced]Thanks. You answered the most important question, but I need to the other as well.

Is it easier to make apt-get work i Dapper drake? I heard both yes or no. The latest was that Dapper was better, but needed work experience than Breezy.

I can try both, but I believe Dapper is better cause it more developed. Ubuntu is Linux everyone so my guess is that they are trying to make it easier and more functional. So apt-get should work better, but that just my guess.

XPerienced[/QUOTE]

Hi XP... (Can I call you XP?).

I'm not sure why you had so much trouble with apt-get previously. Under Breezy 5.10, all the necessary lines you needed in sources.list were already in there. It was just a matter of removing some "#"s from that file.

But in Dapper, you don't even need to do that. The 'Add/Remove Applications' will automatically add in the Universe and Multiverse repositories for you if you select an application from one of them. And under the Repository menu of Synaptic you can just add Universe and Multiverse from a drop-down menu.

Then you can apt-get from the command-line to your hearts content, without worrying about potentially mucking up your sources.list file, editing it by hand.

Cheers,

---

### Post by DooX on 2006-05-01
[QUOTE=XPerienced]
DooX:
I think you can downgrade aswell. Linux is much better and if it get a little less frustrating to confiugre, it will be awesome! Don't misunderstand me. Things like apt-get is excellent, but apt-get didn't work properly in the beginning for me and that made me mad.

And I think problems in the beginng scares people who been running Windows for several years. I've been running it for over 10 years so this is a very special step so I don't want problems five-ten minutes after the installation is complete.
XPerienced[/QUOTE]

Yes,i know what are you talking about.I also dont like problems 10 minutes after instalation but hey this is FIRST Linux i installed without any problems from the begging.Now i had so far (this 2 days im using Ubuntu) several problems,im faceing one right now.I had problem with Samba server,actually problem was in fstab this distro put root to be owner of all mounted partitions except root.I didnt know that,so i was reading about Samba as crazy because Windows PC didnt had written permissions.When i got to the problem,edited fstab everything worked great.Now,i have problem with mp3.Just started to read Ubuntu Wiki,mp3 is not supported by default,you need to enable it because its illegal.Have few problems here thus,still dont hear the sound of mp3's but im though.I want to work with this Linux.

---

### Post by Sef on 2006-05-01
When you upgrade Linux/Gnu, it is best to do a clean install.   

I have been on Dapper for a bit and Beta 2 is really good.  Only about a month till it goes gold (1 June.)

---

### Post by XPerienced on 2006-05-02
Nequeo:
Great. That's what I would like to hear.

I don't know how I experienced so many problems. I tried to install Conky and Thunar. I also had problems with Xubuntu-desktop but I solved that by removing # in sources.list as you said.

And you can call me XP. It's ok. ;-)

DooX:
You know exactly what I mean. If Ubuntu is going to be a threat againg Microsoft it got to be more mature and Ubuntu has come a long, long way, but it's still not there yet.

Every little tiny problem, can be a little bit tricky to solve. I said once that you can do the same thing i Ubuntu as in Windows, you're just doing it another way. And for a guy who learned Linux the hard way by manually install Linux, Ubuntu is a freeride. 

And I'm also new as you. I'll change my deskop about two weeks or so. Say about a year or two when we say this threads about playing mp3-problems, we will laugh. "How stupid we where". Of cource it's easy when you have to knowledge.

I'm determine to stay on Linux too. I don't like the way Microsoft developing their operatingsystem. I heard a guy who ran a Vista (betaversion) and it used 600 MB without any applications running. So if you're going to use Vista without swapping you probably need at least 1024 MB. XP requires 128 MB, but it's inhuman to use XP with less than 512 MB. So it might be the same with Vista. 2048 MB is minimum. ;-)

And every applications that depens on another. When I uninstalled Outlook Express casue why should I have Outlook express when Outlook, but Outlook didn't start casue it need files that Outlook Express had. Yeah right. And to install Outlook Express, you probably need to install Internet Explorer.

So I don't like Microsoft beasue of:
- Their operatingsystem needs alot of computerpower
- Their application "depens" on another.
- You don't know what you get.
- You don't what which kind of information is in the "crashreport".
- You can't chose what you like, they install everything.

And much, much more.

I'm done with the anti-Microsoftpropaganda now. :-)

Linux doesn't cost a dollar, it's open and free. You not it's not evil. You can trust the processes in "taskmanager". And it's more slim, easier to personalize and so on. And it's more secure and have people around the world loving it and trying to make it better. And it's not many known virus for Linux. And I don't think there's so many threats cause I think virusmakers really hate Microsoft more than anything.

I actually think I'm about to love Linux, but first we need to fight as you do with your Linux, as I did and will. Then we both love it I guess. :-)

Sef:
Beta 2 doesn't mean Flight 2 I hope. I saw there were a new Flight about a week are so, but they didn't name it Flight 7 (I guess), they named it somethingelse. So the beta 2 your talking about is equale to Flight 7?

XPerienced

---

### Post by BarFly on 2006-05-02
gksudo "update-manager -d"  I did this tonight to a 5.10 Breezy Badger install and have no complaints other than the upgrade took forever.  It is probabally best to do a fresh install, though.  All my savings were intact, no data loss.

Don't listen to me, though.  I am trying to learn this odd OS as well.

---

### Post by steve.horsley on 2006-05-02
After Flight 5 came Beta1, then Beta2. The flights are really alpha versions.

I don't think the virus writers avoid Linux for political reasons. These days, most virus writers are there for the money. They avoid Linux because windows is more profitable, for 3 reasons I can think of:
* Windows is easier to infect
* There are more windows machines out there
* Linux users tend to be more aware and careful, and more likely to fix any infection

---

