---
title: "What about security.......?"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by loyaleagle on 2006-12-06
I am a newby to Ubuntu Linux. I come from a paranoid XP world full of viruses, spyware and takeover attempts. My now erased XP hard drive was being scanned by AVG anti-spyware, Zonealarm, Spybot, Ad-aware and MS Defender.

Now having said that, I have heard so much about Ubuntu that I am giving it a try. I installed it and Ubuntu works flawlessly. It is taking some getting used to it, but that's part of the fun. 

I have several questions in mind:

1) Is there a good site where I when can learn the linux basics (installation / terminal window commands / etc.) (Maybe there are some pages within Ubuntu.com, but all I could find where some very generic manuals.)
2) Eventhough I sit behind a DSL wireless router, do I still need to install a firewall? (I have read a lot about that and my inclination is that I do not have to. Looks like not running as the admin in Linux is a GOOD thing.)
3) Should I be running a virus screener? If so, is AVG's linux version any good?

Well, thank you for reading and answering this post. I am looking forward to many years of happy Ubuntu computing. I am officially off the Microsoft Windows mouse wheel.

Benoit

---

### Post by Perfect Storm on 2006-12-06
1) [http://www.ss64.com/bash/](http://www.ss64.com/bash/) is one of many sites

2) Iptablets is installed by default, if you want a frontend for it you can use firestarter

3) No, not needed, only if you use your computer to protect windows machine or alike.

---

### Post by an.echte.trilingue on 2006-12-06
You can instal firestarter from the repos if you are paranoid.

However, a better route IMHO is to simply understand what services you are running and configure them properly.

open a terminal and type "netstat -tulp" to get a list of all the services you have listening to whatever port, (there should not be any on a default install) and then read the man pages about those services to learn how to configure them.

Otherwise, you really don't need to worry about security on your home computer running Ubuntu.

There is a very good beginner tutorial on linux.org that will introduce you to linux administration and scripting.  Beyond that, it depends on what you want to do.  Anything specific?

Catcha later.
-mat

---

### Post by ThrobbingBrain66 on 2006-12-06
1. [www.linuxcommand.org](www.linuxcommand.org) is good for terminal commands/script writting
1a. [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) is good for installing ANYTHING

2.  You dont need a software firewall, but one can't hurt either.  iptables is Ubuntu's firewall and is install automatically.  you can instal firestarter from the repos to configure it (although few ports are open by default)

I just found this post on ubuntu security thats pretty good.
[http://www.linuxforums.org/security/locking_down_ubuntu.html](http://www.linuxforums.org/security/locking_down_ubuntu.html)

3. No virus scanner is needed.

---

### Post by kjacks on 2006-12-06
Here is a great site to learn shell commands:

[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)


And this forum is another great resource.  This is by far the most helpfull forum I've ever used.

---

### Post by tribaal on 2006-12-06
Asiu has a nice security article [here]("http://www.psychocats.net/ubuntu/security").

You can also check out the wiki's [security manual]("https://help.ubuntu.com/community/Security"), if you want something more specific.

Hope this helps...

- trib'

---

### Post by loyaleagle on 2006-12-06
Thanks..... One more question? Do you have to run any defrag program for hard disk maintenance within Ubuntu?
I already checked the ss64 site and I can't wait to get familiar with all this?

Thanks again:

Benoit

---

### Post by deadgobby on 2006-12-06
> **loyaleagle said:**
> I am a newby to Ubuntu Linux. I come from a paranoid XP world full of viruses, spyware and takeover attempts. My now erased XP hard drive was being scanned by AVG anti-spyware, Zonealarm, Spybot, Ad-aware and MS Defender.

Now having said that, I have heard so much about Ubuntu that I am giving it a try. I installed it and Ubuntu works flawlessly. It is taking some getting used to it, but that's part of the fun. 

I have several questions in mind:

1) Is there a good site where I when can learn the linux basics (installation / terminal window commands / etc.) (Maybe there are some pages within Ubuntu.com, but all I could find where some very generic manuals.)
2) Eventhough I sit behind a DSL wireless router, do I still need to install a firewall? (I have read a lot about that and my inclination is that I do not have to. Looks like not running as the admin in Linux is a GOOD thing.)
3) Should I be running a virus screener? If so, is AVG's linux version any good?

Well, thank you for reading and answering this post. I am looking forward to many years of happy Ubuntu computing. I am officially off the Microsoft Windows mouse wheel.

Benoit
1. There is plenty of sites for Linux terminal commands. Like
[http://linux.org.mt/article/terminal](http://linux.org.mt/article/terminal) for a sample of many sites.

2. Ubuntu comes with a Firewall with in its software. After new version the firewall is up dated. There is additional firewalls that you can install. If you are not hosting a web site. Really no need for more fire power.
 
3. Getting a virus to work in Unix or Linux you have to invoke it. Virus work very different in Linux/Unix. Ok to give you a sample. You read your email using windows and you click on a exe file, link, or DL a porn meg from a P2P to invoke it. Off it flies and soon your are infected and effects the whole kernal. It could be a trojan horse or a worm. No matter what, the windows kernal is effected.
 In linux or unix world. A virus attacts very differently. It has to be a virus made for Linix. If it is made for Linux, it only to cause very min damage. It only attack a certian program to be infected. It cannot infect the whole kernal as of yet.Yet is the key factor.  And to get a virus to work in linux. You have to be logged in root user to invoke it. To fix a program that has been infected in linux is simple. Reinstall the program that is infected. When a virus. trojan horse, or worm can attack the Linux/Unix kernal. I am in big trouble.
 Now can a Linux user spread a windows virus. %100 yes they can. I can get "I Love You "  virus via email for sample. I can't open up the exe file and assume it a cute little post card. So I forward it to my family and friends who use windows. BAM! I just infected them all who open up the exe file.  If I did open the exe file using a windows emulator called Wine. It simply says HA! and cannot not open it.
 A virus protector is mainly for the Linux/Unix user is not infecting the window user and protects the user when in Root command mode not to invoke it.
Here is a link to tell the diff.
[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)
 You can do some home work on line and just Google Linux Viruses. There is far less viruses that can screw around Linux, Unix, or Apple O/S. Simple, both systems cannot read exe files.
 You do not need all that spy ware, antivirus, and all the crud that you need to install on Windows. If you want you can install Fire Starter in Synaptic for addition protection. 
Gobby

---

### Post by Biggus on 2006-12-06
> Do you have to run any defrag program for hard disk maintenance within Ubuntu?

Hi dude, I'm no expert, but I believe that, for some reason, the filing system used by Ubuntu does not require you to defrag it.

---

### Post by peterj on 2006-12-06
It forces a scan on the hard drive after 30 mounts (starts)

---

### Post by Perfect Storm on 2006-12-06
EXT3 filesystem is very effecient compare to the Microsofts FAT and NTFS. It places the files more logical than microsofts counterparts.

---

