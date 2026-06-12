---
title: "Why doesn't Linux need Antivirus and Defrag?"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2006-12-25
Once I asked the questions what equivalence does Antivirus program from Windows XP have in Linux.  And what Defragmentation program Linux uses where Windows have Diskkeeper.
I was given the responses that the Linux file system isn't built like Windows filesystem thus don't need any disk defragmentation.
That viruses in Linux doesn't have as much action as under Windows.

Now I want to find some more descriptive information regarding my 2 questions (on a laymens level, I'm not technical).  Can you recommend/direct me to some articles, threads or FAQs that explains why Linux doesn't need Antivirus and Defragmentation in more detail?

---

### Post by meng on 2006-12-25
[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)
[http://www.theregister.co.uk/security/security_report_windows_vs_linux/](http://www.theregister.co.uk/security/security_report_windows_vs_linux/)

---

### Post by macogw on 2006-12-25
Someone attempted to run 5 of the most annoying Windows viruses on Wine in Linux to see if it could be done.  They gave the viruses full permission and everything.  Only one would install and run.  When it ran, it spit crap into the terminal.  When you hit ctrl+c, it quit.

---

### Post by pistcivet on 2006-12-25
> **macogw said:**
> Someone attempted to run 5 of the most annoying Windows viruses on Wine in Linux to see if it could be done.  They gave the viruses full permission and everything.  Only one would install and run.  When it ran, it spit crap into the terminal.  When you hit ctrl+c, it quit.
I remember that article. Old, but still pretty funny.
[http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss](http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss)

---

### Post by Regel on 2006-12-25
> **pistcivet said:**
> I remember that article. Old, but still pretty funny.
[http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss](http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss)

That article sums it up. =)

---

### Post by meng on 2006-12-25
Hence proving that wine is not an emulator (or at least not a good one!)

---

### Post by idrinkwhisky on 2006-12-25
there is linux anti virus software out there. I believe Xandros ships standard with antivirus software.

the defrag has to do with how ext3 "stores" information on your harddrive.

---

### Post by macogw on 2006-12-25
There's ClamAV in the Ubuntu repos

---

### Post by ubuntu27 on 2006-12-25
There are antivirus for Linux, but it is generally used to scan Windows computers in your network.

---

### Post by macogw on 2006-12-25
I scan occasionally in case there's something I downloaded that I would be passing on that could have a virus hidden in it which is dormant on my system but dangerous on a Windows computer.  Since there's not much that I pass like that, I don't really bother with scanning too much.  Do need to look into infected jpegs though...those could easily be passed.

---

### Post by az on 2006-12-25
Ext2 or ext3 filesystems defragment themselves with use.  It's built-in.

Viruses are pretty much a windows-type of security vulnerability.  Fixing some kinds of security vulnerabilities in windows in a straightforward way would shut down functionality that it needs to have - it would break stuff.  That's why you have to scan and remove viruses instead of fixing the underlying problem.  This is not the way linux is built.  Linux is not without security vulnerabilities, but viruses are not a particularly effective way to exploit a linux system.

If you stay up-to-date with security updates, your linux box is as secure as an OS can be.  That's much simpler and more straightforward than windows.

---

### Post by IYY on 2006-12-25
The defrag issue is fairly obvious; the filesystem that GNU/Linux uses defrag-as-you-go techniques. In layman's terms, it just doesn't leave unfinished work behind.

As for viruses, the simplest answer is that there are no viruses for Linux, so you don't need an antivirus. As for why there are no viruses, here are some possible reasons:

[LIST]
[*]GNU/Linux is not as commonly used as Windows, and those who use it love it too much to sabotage it on purpose.

[*]A virus can only be installed with the superuser password. So, you will *know* that you are installing a program, so you can make sure it came from a trusted source. In Windows, some viruses can be installed via security holes, without the user ever realizing that something is being installed.

[*]When a virus is indeed embedded in software (rather than installed in a sneaky manner), the software in question is usually pirated. You certainly won't get a virus when installing a store-bought version of MS Word in Windows. GNU/Linux don't pirate software; they have free alternatives. When a program is downloaded from the programmer's own site, it has a far higher chance to be clean.

[*]Most GNU/Linux users download software from trusted places, where there can be no viruses. When you apt-get a program, you're getting it from heavily guarded repositories that are very reliable and will certainly have no viruses. Even when you get a program from sites like freshmeat.net, the odds of it having viruses in it are very low because of the sites' strict policies.
[/LIST]

---

### Post by jingo811 on 2006-12-26
kewl! :KS

---

### Post by Sef on 2006-12-26
> GNU/Linux is not as commonly used as Windows, and those who use it love it too much to sabotage it on purpose.

For web servers that is not true.  Linux is run on about 2/3 of the web servers, and Windows is run on about 20% of them.  Yet the viruses are designed for Windows.

---

### Post by IYY on 2006-12-27
> For web servers that is not true. Linux is run on about 2/3 of the web servers, and Windows is run on about 20% of them. Yet the viruses are designed for Windows.

True, but getting your virus installed on a server is much more difficult than on a desktop machine because the servers actually have real system administrators.

---

### Post by denver on 2007-03-12
> **IYY said:**
> True, but getting your virus installed on a server is much more difficult than on a desktop machine because the servers actually have real system administrators.

So in conclusion...the epidemic forced on the windows world is more likely to be aimed at home users who mostly watch movies, listen to mp3's/CD's surf the web and download recipes for cheese cake and stuffed cabbage:) .Or it may be the work of tired or just plain bored programmers that want to drive you mad by sending you infected e-mails. To me it would make more sense to  attack a more meaningful target, such as a popular server of some sort.

But again...how else are people going to be forced in buying spyware remover programs if no spyware exists. Its not uncommon to be plagued by nasty HTML wallpapers warning you that your computer might blow up if you don't download a spyware removal program. Or even better...spyware that launch a browser window every minute or so taking you to some online casino where you are always the 1000 000 visitor and you need to claim your prise. Perhaps its my own fault i went through all that back in my windows days....but one should not be afraid to use his PC or the Internet because he or she might get infected and have to reinstall.

Windows is not a bad OS...its not the OS's fault people write viruses...but for me...learning a different OS was far easier the recovering my personal data ( which i never managed to do by the way )

---

### Post by RobMBaker on 2007-03-21
> **denver said:**
> 
Windows is not a bad OS...its not the OS's fault people write viruses...

Well, I believe the point is that Windows *is* inherently worse than any Linux-type OS; *because* it is designed in a way that allows viruses to gain entry more easily, and wreak more havoc once they get in.
I had (slightly paranoid) questions about potential Linux infections; but I concluded that a user would have to have a bit of knowledge, and a whole lot of stupidity to get a serious Linux virus ... No-one normally runs Ubuntu as root/superuser, so anything dodgy trying to change the root filesystem would be immediately obvious.
And I doubt any novice user is capable of making a dodgy binary executable - and no experienced user would do so ... unless they're doing it at their own risk (so don't do it if you don't want to risk it). The only things I've ever installed NOT from the Ubuntu repos were Skype (trusted anyway), Sun Java (that was a binary, but I felt fairly confident in getting it straight off Sun's site) and Freemind (I trust that, but that's 'cos I used to use the Windoze version) ... so basically, stick with the repos to be safe.

---

### Post by cowlip on 2007-03-21
Just be careful about adding repositories from everywhere (even though this was touched on), because then all packages on your system can be modified.  Eg., your wallpaper can be changed, or far worse.

[http://www.pthree.org/2006/11/23/untrusted-repositories/](http://www.pthree.org/2006/11/23/untrusted-repositories/) "untrusted repositories"

---

### Post by fizban on 2007-03-21
My belief is this.....since most computers manufatured have microsoft running on them then virus writers target that OS. Also, you cannot do anything to a Linux system unless you are in root. Make sure your password is strong enough and you should be fine.
Fizban

---

### Post by NikoC on 2007-03-21
The defragging link in the second post cleared things up for me as well! Nice link there!

---

### Post by jingo811 on 2007-03-21
**@Cowlip>>>**
Nice article link, yeah I've always had a feeling that the repository would be the first door to Linux intrusions.  Just didn't know how exactly but that article confirmed my fears now I need to {educate myself}={wasting more time and brain energy} #-o

**@everyone>>>**
So I practically had to open up all the repos from this list to be able to install the side buttons on my mouse is this a security threat by having to do so?
I mean sure it's a Ubuntu Wiki but there are many Multiverse, Universe, Risky and Unsupported links I've connected myself into.  Is this still OK security wise?
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories)

---

### Post by Tomosaur on 2007-03-21
> **jingo811 said:**
> **@Cowlip>>>**
Nice article link, yeah I've always had a feeling that the repository would be the first door to Linux intrusions.  Just didn't know how exactly but that article confirmed my fears now I need to {educate myself}={wasting more time and brain energy} #-o

**@everyone>>>**
So I practically had to open up all the repos from this list to be able to install the side buttons on my mouse is this a security threat by having to do so?
I mean sure it's a Ubuntu Wiki but there are many Multiverse, Universe, Risky and Unsupported links I've connected myself into.  Is this still OK security wise?
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories)

It's still ok, yes. All you've done is allowed your computer to 'see' these new repositories. It's not like you're connected all the time - just when you want to download something. It just means that those repositories aren't 'officially maintained', or that the software within them are 'risky' in the sense that they're still in development and so may be unstable. It's not like any old person can just wade in and start adding stuff, they're just maintained by a different group of people who aren't directly affiliated, OR there is some other reason why they're not enabled by default. The people who maintain those 'risky' repositories still check the packages to make sure there's nothing malicious going in. There are also packages in those repositories which may be considered illegal in your country, which is why, if they are official Ubuntu repositories, you have to manually enable them.

---

