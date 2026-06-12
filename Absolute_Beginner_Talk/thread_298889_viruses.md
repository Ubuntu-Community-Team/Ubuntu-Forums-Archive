---
title: "viruses"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by rikguenther on 2006-11-13
does linux generally get attacked by viruses?  im just wondering so i know if i need some kind of virus protection or firewall or something of the sort.

---

### Post by joshsherman on 2006-11-13
typically not, although there are virus protection software, so eventually the situation may arise.

-j

---

### Post by an.echte.trilingue on 2006-11-13
There are currently something like 54 known viruses for linux, most of which only exist as proofs of concepts in labs and none of which are currently running in the wild.

It is not impossible, though.

---

### Post by mo79 on 2006-11-13
> **rikguenther said:**
> does linux generally get attacked by viruses?  im just wondering so i know if i need some kind of virus protection or firewall or something of the sort.

If like me you were lucky not to get viruses on Windows (or actually small ones), you'll probably be even safer on Linux.
But hey, if market share increases...

---

### Post by ReaderRat on 2006-11-13
If you have Ubuntu loaded and running, you have a firewall called *iptables*. You can install a GUI to work with it (called *firestarter*). There is AV software called *clamav*  ([**AntiVirus For Ubuntu**](https://help.ubuntu.com/community/ClamAV))  I believe both [COLOR="Red"]firestarter[/COLOR] and [COLOR="Red"]clamav[/COLOR] can be installed with Synaptic Package Manager.

---

### Post by Frak on 2006-11-13
There isn't any at the moment, but ever since Micro$oft made the deal with Novel, I've installed an Anti-virus just in case...
When Windoze is ever mentioned with linux...  I put up every guard known to man. I run an Anti-Virus right now for that reason, Micro$oft is going to get the $200 million back somehow and that's going to be to make Linux more popular... Viruses follow...
I run ClamAV just to say.

---

### Post by slibuntu on 2006-11-13
> **mo79 said:**
> 
But hey, if market share increases...

](*,) This is a common misconception, the main reason that linux doesn't have as many viruses isn't because its not as popular, its inherently more secure because of the way the 'root' system works. Also because it's open source, viruses can be spotted quicker because everyone has access to the code. Its harder to rob a house when everyone is watching.

---

### Post by slibuntu on 2006-11-13
> **Frak said:**
>  Micro$oft is going to get the $200 million back somehow and that's going to be to make Linux more popular... Viruses follow...
 
See above

---

### Post by SunnyRabbiera on 2006-11-13
A virus in linux???
Not any I know that is an actual killer, but there have been concept viruses.
But you have more of a chance of a virus on a Mac then linux.

---

### Post by slibuntu on 2006-11-13
There are only 2 that i've ever heard of, Bliss and Staog, but Staog has never been 'in the wild', i.e, travelling around infecting computers, and Bliss can be gotten rid of by typing --bliss-uninfect-files-please. 
Check them out here; [Staog]("http://en.wikipedia.org/wiki/Staog") and [Bliss]("http://en.wikipedia.org/wiki/Bliss_%28virus%29")

---

### Post by jbonll05 on 2006-11-13
While Linux is generally free from worm,virus, and malware attacks I have heard and read on-line that they can pass through to your contacts that have M$. For that reason i run clamAV with "Dapper". Anyone comment on pass through? I have Firefox, with a firewall that works well, that periodically tells me, by text message, that a "trojan", "mydoom", or "bot" got by my ISP.I never see the email; It is killed on sight. I really feel for my hardheaded friends that will not try Ubuntu. Two have and put it on their everyday(internet/email) machines.
JB; Ubuntu since oct05, "Dapper" and "Edgy".

---

### Post by aysiu on 2006-11-13
I think you should read this:
[http://psychocats.net/ubuntu/security](http://psychocats.net/ubuntu/security)

---

### Post by BarfBag on 2006-11-13
> **aysiu said:**
> I think you should read this:
[http://psychocats.net/ubuntu/security](http://psychocats.net/ubuntu/security)

VERY informative.

---

### Post by Grim Tuesday on 2006-11-13
viruses? never heard of any on linux (or mac)

---

### Post by Bllizzd on 2006-11-13
No program or operating system is ever going to be completely secure.

I would recommend that everyone has atleast a AV on any computer they have.

---

### Post by IYY on 2006-11-13
If you get your software from the official repositories, you'll be safe from viruses. Of course, nothing can truly protect you from malicious code in software you install with the admin account from random places on the net. All it takes is a script with the command **rm -rf /** to erase your entire hard disk (kids, don't try this at home; it probably won't get around to erasing the entire filesystem, but will break a lot of things before crashing.)

As for being hacked; update your machine from time to time (you will be notified when new updates are available automatically) and use real usernames and passwords (guest/guest is not a good username/password combination).

---

### Post by gnama on 2006-11-14
There ARE viruses for about every system. Thats why we should always use firewalls and anti virus. Google some of the entries of antivirus sites.

---

### Post by Portable_Jim on 2006-11-14
> **Grim Tuesday said:**
> viruses? never heard of any on linux (or mac)

There is only 1 virus for mac ([http://www.symantec.com/security_response/writeup.jsp?docid=2006-110217-1331-99](http://www.symantec.com/security_response/writeup.jsp?docid=2006-110217-1331-99))
while there is about 1 thousand for linux ([http://apple.slashdot.org/comments.pl?sid=204497&cid=16706233](http://apple.slashdot.org/comments.pl?sid=204497&cid=16706233))

...Authough  both lots of viruses are only in the lab, 'proof of concept ones'.

---

### Post by Portable_Jim on 2006-11-14
> **gnama said:**
> There ARE viruses for about every system. Thats why we should always use firewalls and anti virus. Google some of the entries of antivirus sites.

Using synaptic is easier

---

### Post by CatKiller on 2006-11-14
> **Portable_Jim said:**
> while there is about 1 thousand for linux ([http://apple.slashdot.org/comments.pl?sid=204497&cid=16706233](http://apple.slashdot.org/comments.pl?sid=204497&cid=16706233))

...Authough  both lots of viruses are only in the lab, 'proof of concept ones'.

The slashdot comment you linked to cited the numbers as coming from  [this]("http://www.linuxtoday.com/security/2006050502026OPSW") quite interesting article. So if you don't want to read a slashdot post, you might still want to read that article.

---

### Post by bodhi.zazen on 2006-11-14
Interesting virus links:

At this time it is possible to run windows viruses with wine. They do not run well yet.

	[Windows viruses with wine](http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss)

[Linux viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)

This wiki lists 14 known linus viruses.

---

### Post by UBU 4me on 2006-11-14
> **BarfBag said:**
> VERY informative.


I agree. Thanks for the link

---

### Post by deadgobby on 2006-11-14
Getting a virus to work in Unix or Linux you have to invoke it. Virus work very different in Linux/Unix. Ok to give you a sample. You read your email using windows and you click on a exe file, link, or DL a porn meg from a P2P to invoke it. Off it flies and soon your are infected and effects the whole kernal. It could be a trojan horse or a worm. No matter what, the windows kernal is effected.
 In linux or unix world. A virus attacts very differently. It has to be a virus made for Linix. If it is made for Linux, it only to cause very min damage. It only attack a certian program to be infected. It cannot infect the whole kernal as of yet.Yet is the key factor. And to get a virus to work in linux. You have to be logged in root user to invoke it. To fix a program that has been infected in linux is simple. Reinstall the program that is infected. When a virus. trojan horse, or worm can attack the Linux/Unix kernal. I am in big trouble.
 Now can a Linux user spread a windows virus. %100 yes they can. I can get "I Love You " virus via email for sample. I can't open up the exe file and assume it a cute little post card. So I forward it to my family and friends who use windows. BAM! I just infected them all who open up the exe file. If I did open the exe file using a windows emulator called Wine. It simply says HA! and cannot not open it.
 A virus protector is mainly for the Linux/Unix user is not infecting the window user and protects the user when in Root command mode not to invoke it.
  Here is a link to tell the diff.
 [http://www.theregis](http://www.theregis) ter.co.uk/ 2003/10/06/ linux_vs_ windows_viruses/
 You can do some home work on line and just Google Linux Viruses. There is far less viruses that can screw around Linux, Unix, or Apple O/S. Simple, both systems cannot read exe files.
Gobby

---

