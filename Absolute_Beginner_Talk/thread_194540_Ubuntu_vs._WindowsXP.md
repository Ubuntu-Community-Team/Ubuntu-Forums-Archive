---
title: "Ubuntu vs. WindowsXP"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by boom2k1 on 2006-06-11
I have 2 questions.
1) How is Ubuntu more stable than Windows?

2) Why is Ubuntu less susceptible to viruses than Windows XP?
Is it merely because people who write computer viruses usually pick Windows to attack?

Thanks!

---

### Post by glotz on 2006-06-11
1) Better code, better thinking, more revisioning and auditing. Try it if you don't believe me! :)

2) Not many viruses can do anything on Linux for now. In part this is because of the smart permissions system. And because of what you suggest.

You're welcome.

---

### Post by Zerocool10482 on 2006-06-11
1. It's free...legally free.
2. Almost every useful application you would ever want to run on Linux is free.
3. When you want to update to the latest and greatest version, with all the latest and greatest features, you don't need to buy a new version...and if you want to stick with the old, you can.
4. Security. Defaults are much better than Windows. There are so many free options for increased security, SeLinux and Grsecurity just to name a couple.
5. All you need to learn about it is out there somewhere, for free, whether it's online, in a man page, or in a forum or newsgroup somewhere.
6. Performance...Linux almost never forces you to upgrade your hardware, and it always runs better on older hardware than windows.
7. Simplicity. Yes simplicity. Most young people think Windows is easy because that's what they grew up with and had the most exposure to. That's like someone in the US saying english is the simplest language.
8. The choices...the free choices, are endless. What filesystem do you want to use, what do you want installed or not installed on your system, what graphical interface do you want to use and how do you want to configure it, which pdf viewer do you want to use, etc. Windows will never be that flexible.

---

### Post by Fafnir on 2006-06-11
The first is beyond my expertise, but as to the second, here are the reasons I know:

1) As you say, Linux has a far lower market share than Windows, so fewer people bother writing viruses.

2) But there's more than that. You have a huge number of distributions of Linux with slightly different kernels, and each one has a small market share (relative to that of Linux). So a virus written for, say, Fedora, probably wouldn't work on Knoppix. There are ways of working round that for applications, but they wouldn't really work for viruses... (Thank you for downloading ScrewYourComputer v10.4. To install the software, please type ./configure, then make. If you would like us to steal your credit card number, use the --moron parameter. Then type sudo make install and enter your root password. Have a nice day!)

3) Linux is open source, so you have a huge community of people looking for security glitches in order to fix them (and only a few trying to exploit them). The result is that any security hole is normally patched loooong before it's exploited. Since programs update themselves almost automatically (as opposed to Windows, which only updates the OS), just about everyone will be running fully secured programs.

4) There's also a far more fluid patch system in open source. Microsoft releases a patch once a month, so if a critical vulnerability is discovered the day after the last patch, you're hosed. In open source, people can focus on that vulnerability and release a patch for it ASAP.

5) Linux has a very rigid permissions system, so a few of the nastier virus symptoms in windows (damaging system files, installing rootkits, activating on startup for a Trojan etc) simply cannot be done without finding a vulnerability in the kernel itself. By default, Windows pretty much just lets programs do whatever they want, so you can get a Trojan from something like Internet Explorer regardless of the security of the operating system.

6) Microsoft doesn't write very good code :-)

---

### Post by boom2k1 on 2006-06-11
Thanks for all these replies!

The reason why I want to switch to Linux is pretty much because of the freedom and openness it offers (and that I am constantly learning how computer works), whereas Windows seems like a blackbox to me even as an experienced user.

How much would you trust that a Linux application is safe and secured?
For example, you have open source programs like AMSN and GAIM, which needs your password in order to connect to the network. How confident can you be that there won't be a code somewhere that could actually steal your user information?
I know how to program, but it is just too time consuming to go through their source codes and read every line to make sure the program is safe!

Hope this question does not offend anyone!

And thanks for reading and replying!

---

### Post by sweeney on 2006-06-11
On a wider note, check out [http://www.dwheeler.com/oss_fs_why.html](http://www.dwheeler.com/oss_fs_why.html) . this should answer most questions regarding the superiority of Free & Open Source soultions as opposed to the proprietary alternatives.

---

### Post by matrooswolf on 2006-06-11
[QUOTE=boom2k1]How confident can you be that there won't be a code somewhere that could actually steal your user information?
[/QUOTE]

If you think windows is more reliable read this:
[http://www.eweek.com/article2/0,1895,1974911,00.asp](http://www.eweek.com/article2/0,1895,1974911,00.asp)

and this:
[http://www.betanews.com/article/No_Fix_for_Critical_Windows_98_Me_Flaw/1149873723](http://www.betanews.com/article/No_Fix_for_Critical_Windows_98_Me_Flaw/1149873723)

and this:
[http://www.pcmag.com/article2/0,1895,1974580,00.asp](http://www.pcmag.com/article2/0,1895,1974580,00.asp)

and that is only the news from today :rolleyes:

---

### Post by glotz on 2006-06-11
I trust my software very much. I believe that any open source project that has gained some popularity has had it's code reviewed by peers. There's no such things there. Another question is bugs. Some bug might somehow leak out your private data but again, bugs are often detected and fixed rapidly in open source apps. (I think that coming from closed source the whole question is a little bit funny. No offence intended either.)

---

### Post by grsing on 2006-06-11
1. Better coding, programs are less intertwined (it's uncommon but by no means unheard of for a program to crash; I have yet to have one program bring down the whole system, though; admittedly, Windows has gotten better with XP with this problem, but it's still somewhat more likely to die).

2.  In large part, it's what you suggest (most people who use Linux are also fairly computer-savvy, so they're much harder targets than the masses that use Windows).  Also, like in 1, each program can do less to the system as a whole (at least without specific permission, the whole super-user thing), and a rogue virus program can't modify important things without permission (which you would hopefully deny).

---

### Post by grsing on 2006-06-11
[QUOTE=boom2k1]Thanks for all these replies!

The reason why I want to switch to Linux is pretty much because of the freedom and openness it offers (and that I am constantly learning how computer works), whereas Windows seems like a blackbox to me even as an experienced user.

How much would you trust that a Linux application is safe and secured?
For example, you have open source programs like AMSN and GAIM, which needs your password in order to connect to the network. How confident can you be that there won't be a code somewhere that could actually steal your user information?
I know how to program, but it is just too time consuming to go through their source codes and read every line to make sure the program is safe!

Hope this question does not offend anyone!

And thanks for reading and replying![/QUOTE]

Because it's open source, anyone can look at the code, and such a malicious part would be quickly caught (assuming it's something that a reasonable number of people use).  Basically, anything in the repositories can be pretty well trusted to be safe.

---

### Post by someusernoob on 2006-06-11
I never run into programs with ads, or programs that want to install malicious stuff :D

And xgl/compiz is so cool, where can i get it for Windows? I can install some 3rd party programs for more future-like effects on Windows, but they bring down the whole performance of the computer!

---

### Post by Fafnir on 2006-06-11
[QUOTE=boom2k1]Thanks for all these replies!

The reason why I want to switch to Linux is pretty much because of the freedom and openness it offers (and that I am constantly learning how computer works), whereas Windows seems like a blackbox to me even as an experienced user.

How much would you trust that a Linux application is safe and secured?
For example, you have open source programs like AMSN and GAIM, which needs your password in order to connect to the network. How confident can you be that there won't be a code somewhere that could actually steal your user information?
I know how to program, but it is just too time consuming to go through their source codes and read every line to make sure the program is safe!

Hope this question does not offend anyone!

And thanks for reading and replying![/QUOTE]

Basically, if there was a backdoor in a large, widely used project like GAIM, someone would find out pretty quickly. It might be a developer, it might be someone porting it to another distro or platform, it might be someone wondering how it worked, it might just be someone paranoid, but the news would get out a couple of days after the compromised version was released. And there would be a gigantic hue-and-cry, GAIM would die, and (*possibly* metaphorically speaking) burly men with big sticks would pay a visit to the developer who thought it up. Even if there was a backdoor in a small, seldom-used project, the odds against it remaining undetected for long would be astronomical.

The problem with putting backdoors in open source software is that (by definition) you can't hide them, so someone is going to find them - even if you personally don't check everything you download. And once one person's found a backdoor, *everyone* can verify it quickly and easily, and then the project disintegrates and there's the wailing and gnashing of teeth. So, especially compared to corporate software, open source is pretty much above suspicion as far as backdoors go.

---

### Post by kop316 on 2006-06-11
On the "how do you know if a program is secure", it would take a lot for a flaw like that to go onto our systems.

1) With some of the programs, there are people that make money or have a reputation with making a program. If there was a flaw of that magnitude, it is likely no one would trust that person/company again.

2) Not only do individual people go through the code, but the Ubuntu repositories are checked by the people of Ubuntu and the Debian packages are checked by the Debian people. I would imagine if it was to come out that they let a bad program onto their repositories, heads would roll inside that company.

3) You usually download programs form that repository or a trusted site (Like I had to compile a program for my MP3 player and got the source code from Sourceforge). It is rare if at all that you install a program from a non-trusted site.

4) Unlike WIndows, things cannot just install onto your computer. In order for something to install, you have to let it install by going into root. In order for anything to execute, you have to give it executable privilages by going into root, then execute it. For the most part, you will know exactly what is running on your computer.

Given that, I trust the programs that I get form trusted sites.

---

### Post by maddbaron on 2006-06-11
i can attest to all the things people said its amazing the difference. and honestly my system runs lighter but is working. in windows my fan would be going hard right now just to maintain firefox and my messenger and music programs and would have frozen a few times.

and for some reason my dsl wireless connection is more stable than in windows. when i installed ubuntu i couldnt work my dsl but after finally setting it up its more stable. my indicator lights are solid green all the time and i havent been booted yet. and the ability to custom is amazing...i didnt try the 3d desktop yet since i am fearful it will hurt my amd sempron but its cool that its available.....

and the fact that i dont need a firewall or antivirus feels good. when i launched frostwire it said i was behind a firewall already...amazing! ubuntu is now my main os and win xp is my backup and now that i can store files in my windows partition its also an additional storage space for me...

go linux!

anyway question,
is Grsecurity like a firewall? i went to their site and it sounds like an advanced firewall?

---

### Post by Omnios on 2006-06-11
Ubuntu is amazing with Xp I used to spend hours every day updating and running my ani virus anti spyware and and anti malware programs. Now I rarely use windows wich is there mostly as a back up and can plug away on the net without worries.

---

### Post by devurandom on 2006-06-12
As for the security of open source code against malicious intents, see:
[http://www.smh.com.au/articles/2003/11/07/1068013371170.html](http://www.smh.com.au/articles/2003/11/07/1068013371170.html)

Basically in 2003 someone had cracked the linux kernel repository and added a little nasty backdoor to its development (CVS) version.
First: the problem was spotted within **hours** and quickly resolved. Second: it required an actual cracker intrusion inside the CVS -something that could easily happen to proprietary software too.

If you try to apply an official patch, trying to put a backdoor in, it would have been immediately rejected.

---

### Post by u.b.u.n.t.u on 2006-06-12
[QUOTE=boom2k1]I have 2 questions.
1) How is Ubuntu more stable than Windows?

2) Why is Ubuntu less susceptible to viruses than Windows XP?
Is it merely because people who write computer viruses usually pick Windows to attack?

Thanks![/QUOTE]


1. You need to define stable. For me that means that I don't have to reinstall the operating system every month or so because I add and remove a lot of software for testing. ubuntu feels a lot more stable to me, but nothing I can quantify at this time.

2. ubuntu uses a different file system structure to windows, which means that it is unlikely to get a virus through an automated process. If people were to write more viruses for linux it wouldn't matter much as they still can't automate an install.

There is no need for an anti-virus with linux and no need for a disk defrag.

ubuntu is very new and only now good enough to replace XP in my view. From here on, it will only get better.

I used windows for many years. Switching to ubuntu on 2 June 2006 was a move I am very happy with.

---

### Post by aysiu on 2006-06-12
I don't know if Ubuntu is stabler than XP, to be honest.

The Linux kernel is pretty solid, but once you put KDE and Gnome on top of it, it can be unstable, depending on the situation.

I'll tell you--it doesn't happen very often, but I've got unrecoverable graphical freezes in Ubuntu, but I've never gotten them on XP. Sometimes certain programs are buggy.

---

### Post by brentoboy on 2006-06-12
[QUOTE=boom2k1]I have 2 questions.
1) How is Ubuntu more stable than Windows?

2) Why is Ubuntu less susceptible to viruses than Windows XP?
Is it merely because people who write computer viruses usually pick Windows to attack?

Thanks![/QUOTE]

I haven't had BlueScreenOfDeath, or other windows freezup problems since windows 2000.

Ubuntu is only more stable because normal users don't have root access so they cant install so much crap that they ruin the system.

A well administered windows box, with free anti-virus and anti-malware, running firefox, gaim, and other open source apps is fairly safe box, especially if you create a non-admin user, and only use the admin user when you are honestly administering the system.  this is easier to do in ubuntu than xp, as it is default in ubuntu, but not default in xp.

ubuntu has fewer viruses because you are not root by default, and it has a small enough user base that there isn't as much desire to write viruses for it.  if it was fairly popular, it would start to have viruses.  Just look at mac.  they were virus free for a long time, but recently they have become a target, and what was a "too secure for viruses" OS is now starting to be a target.

anyone who claims that viruses cant be written for Linux is elitist, arrogant, and uninformed.  but, to some extent they are correct (for now) because there aren't many out there, and those that are only work if they are run as root.

The only "problem" with windows is the licensing scheme, vendor lock-in and proprietary formats.

---

