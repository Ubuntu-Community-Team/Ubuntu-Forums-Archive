---
title: "Slow OS upgraded to 12.04 Antec Model SU380"
date: 2012-06-04
forum: Asus Ubuntu Support (CLOSED)
---

### Post by ken78724 on 2012-06-04
losing patience,,, Slow OS on asustek PC; happened after Upgrade 11.10 to 12.04 LTS. Since upgrade I see a "crash report detected" which I transmitted. Can't see report. have a wragged login skin. Sys is up to date but the wragged skin won't correct. uninstalled and reinstalled all kde & kubuntu as I had kxstudio with high powered PPA in 10.04,10.10, 11.04, then upgraded to 11.10 then to 12.04. 

pc is painfully slow with a browser & libre writer open... ????

Did terminal network analysis as of 6-2-12 9:30 PM; is reported below.

ken@kenpc:~$ lspci -nnk | grep -iA2 net
00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
Subsystem: ASUSTeK Computer Inc. Device [1043:8234]
Kernel driver in use: forcedeth

am backing up to ubuntu one cloud & ASAP I plan a new 12.04 LTS install. recommendations welcome on 12.04 Antec Model SU380 asustek

---

### Post by Paddy Landau on 2012-06-05
If you're going to do a fresh installation, it's a good opportunity to decide which variant you should install.

If you have a modern computer with at least 2Gb RAM, I'd go for 64-bit Ubuntu. If your RAM is lower or if your computer is old, I'd try 64-bit [Lubuntu]("http://lubuntu.net/") instead.

---

### Post by ken78724 on 2012-08-01
Paddy Landou:
 
Went to 2nd PC; had set the Antec Mod SU 380 as it has too many files not backed up. Will do a re-install as you recommend as the PC has memory needed etc.

thanks again! Kenneth :)

---

### Post by Paddy Landau on 2012-08-01
Good luck. Let us know how it turns out.

---

### Post by ken78724 on 2012-08-11
Yesterday 8-10-12 amidst intended corrective action, a 601 file update gave us options, particularly a bunch of KDE & Libre office make overs, which did not produce a clean log in page or detected crash notice removal or a libre office that functions w/o going into "a forced to close panic mode." I let an auto-update work around kick in. 

Will report back if the fireworks lets this PC stay alive beyond go. 

Auto back up has not been an option since letting this PC sit idle from June 2nd to August 10th.

---

### Post by ken78724 on 2012-08-11
Paddy Landau: with limited and no sure back up,,,, am not sure on an install you recommended. Apologize I am not conversant with what a variant is. Recall you recommended > **Paddy Landau said:**
>  do fresh install, decide which variant [to] install. "http://lubuntu.net/"]Lubuntu[/URL]

As noted on another thread, when I used this PC the first hour since June 2nd on Aug 10th, the crash detected note was still auto posted and the OS tried to/failed to do updates and went to a forced quit involving a KDE and Libre Office war. Whe the internal fight let up, the PC auto-updated 601 files, ran fair then crashed and tumbled for a while and this morning has done it again then went into an auto repair when I elected not to power off. Will report what happens shortly if I can.

---

### Post by ken78724 on 2012-08-11
Paddy, is there a terminal work around that would let me carve out antagonist guts of the current install and build a so to speak blood and guts lubuntu ? 

I did +/- that on this 64 bit Antec Model SU380. I have maybe six or eight gigs of files not backed up and want every bit of a chance to save that. If I recall I beefed up the PPA anticipating I'd do some high powered video production. No productions got done and now a light OS would handle most of what I need to do. 

Hope you or any concerned other may venture a work around going from a some what over built OS to light weight Lubuntu.

---

### Post by Paddy Landau on 2012-08-11
Kenneth, I'm sorry, I do not entirely understand everything that you have written.

If you wish to back up your files but your computer won't boot, may I suggest that you boot from a Live CD and back up from there to a safe place, e.g. an external USB drive.

If you wish to do video work, take a look at [Ubuntu Studio]("http://ubuntustudio.org/"). I haven't used it, but it may suit your needs.

EDIT: By "variant", I just meant one of the alternative "flavours" of Ubuntu. Ubuntu has several flavours: its main offering (also known as Unity), Lubuntu (for low-spec machines), Xubuntu (uses LXDE desktop), Edubuntu (for educators), Ubuntu Studio, and Kubuntu (uses KDE desktop). There are also unofficial Ubuntu distributions, such as Bodhi (for very low-spec computers) and Mint. Then there are many other distributions that have nothing to do with Ubuntu, such as CentOS, Fedora, Arch, Debian, Red Hat, and a multitude of others.

---

### Post by ken78724 on 2012-08-11
Paddy: I've used Ubuntu Studio seven years and am finding out via backup that I am saving immense junk, caches, old/presumed to be deleted programs, crash reports, etc. Much of that is being backed up unnecessarily. I had tried to ask you whether I could essentially delete major parts or all of the old programs, discarded programs, etc. using a terminal delete. Why? I am paranoid regardless of how good back up may be that I'd lose the half million files, chapters, etc. that remain on my HD, to be edited and turned into manuscripts. Yes, I am slow to learn how to copy those jewels to thumb drives, DVDs or a cloud storage. 

My question is answered for deleting Lubuntu via terminal @ [http://ubuntuforums.org/showthread.php?t=2040433](http://ubuntuforums.org/showthread.php?t=2040433). 

I want a general terminal deletion to remove ubuntu studio, multiple builds of mozilla firefox, sea monkey, opera and so forth. I know if U do a new install it wipes a HD clean. But, amidst certain programs like opera, big caches of video and picture memories, you can lose valuable writing, calculations and other materials, which only a research scientist would want. Well, I have to face the hard work, and even buy Hard drives so I guarantee the files are not lost. apologies. 
'
back to the terminal deletion guidance I am asking for. Do you know where I may find the sudo apt-get remove ???? that I may use to do "the dumps" one by one... ?

yes, I'd be grateful to know...

---

### Post by ken78724 on 2012-08-11
Paddy: if you wonder what's Ken talking about stop in on housekeeping at [http://ubuntuforums.org/showthread.php?p=12165748#post12165748](http://ubuntuforums.org/showthread.php?p=12165748#post12165748)

Thanks for pointing me along the way. Looking back at getting my KX Studio humming and saving photos in Opera and removing it as incompatible with Open Weld and audio programs etc., ended up with worthless crash reports that are in my cloud, on thumb drives and DVDs, making it hard as a dickens to find highly valuable paragraphs or chapters I find hard to locate. 

I know, you too have the need. 

Thanks again!!!!!!:popcorn::popcorn:

---

### Post by Paddy Landau on 2012-08-12
Kenneth, I wonder if you are making things too complicated for yourself.  Also, please distinguish between "delete" and "uninstall". With  uninstalling, the package manager handles the process (including  deleting files). With deleting, the implication is that you are deleting  the files, which is a poor way to remove programs, because the package  manager does not know what is going on.

But I suspect that you already know that, as you use apt-get.

Now, to try to answer your questions, assuming that I have understood you correctly.

> **ken78724 said:**
> … I am saving immense junk, caches,  old/presumed to be deleted programs, crash reports, etc.
Linux has a lovely separation of areas (e.g. there is no Registry, as Windows has). *All* of your data is stored within your *home folder*, i.e. [FONT=Lucida Console]/home/ken[/FONT] (or whatever your user name is), a.k.a. [FONT=Lucida Console]~[/FONT], unless you have specifically placed your data elsewhere.

Furthermore, some of the folders that you mentioned are hidden folders — those beginning with a dot. In general, you will ignore those folders and back up only your normal, not-hidden folders, such as [FONT=Lucida Console]Documents[/FONT], [FONT=Lucida Console]Pictures[/FONT] and [FONT=Lucida Console]Videos[/FONT].

You may make exceptions for specific applications: for example, [FONT=Lucida Console]~/.mozilla[/FONT] for Firefox settings (but you can exclude [FONT=Lucida Console]~/.mozilla/firefox/*.default/Cache[/FONT]); [FONT=Lucida Console]~/.thunderbird[/FONT] (again, exclude [FONT=Lucida Console]~/.thunderbird/*.default/Cache[/FONT]).

> **ken78724 said:**
> .. could  [I] essentially delete major parts or all of the old programs, discarded  programs, etc. using a terminal delete.
Well, whether you use a terminal or a GUI to uninstall makes no difference. In Ubuntu, you can use apt-get, [Synaptic Package Manager]("apt:synaptic"), or Ubuntu Software Centre. Use whichever you prefer to install and uninstall; they work well together.

But bearing in mind what I mentioned about backing up your data, this should make *no difference whatsoever* to your backups! You should not be backing up anything outside your home folder, unless you had specific reason to place data elsewhere.

The Linux operating system is a small one, using little disk space compared to Windows, and on a modern computer you will not need to worry about uninstalling anything unless it causes a problem. However, if you are running short on space, you can use the following two commands, but they are unlikely to make much difference:
```
sudo apt-get autoremove
sudo apt-get clean
```Those two commands can also be achieved through the GUI, though I do not remember how.

> **ken78724 said:**
> I am paranoid regardless of  how good back up may be that I'd lose the half million files, chapters,  etc. that remain on my HD, to be edited and turned into manuscripts. … I am slow to learn how to copy those jewels to thumb drives, DVDs  or a cloud storage. 
Half a million? You have been busy! If you have not been backing up, you could lose *everything* at a stroke should your computer be stolen or the hard drive fail (hard drives do fail, sometimes suddenly without warning).

Sort out your backups *now*, before you do anything else!

Here is how I back up on a **daily** basis:

[LIST]
[*]Cloud storage. I use [SpiderOak]("https://spideroak.com/"), which is relatively cheap, highly reliable, totally secure, cross-platform, and easygoing with using it on multiple computers. Of course, you need broadband if you do this. I back up all essential data with this.
[/LIST]

[LIST]
[*]External USB hard drive. I use [rdiff-backup]("apt:rdiff-backup"), and save my entire home folder. This means that I have access to all hidden settings that I may later decide I wish I had kept.
[/LIST]
Additionally, when I reinstall Linux:

[LIST]
[*]I make a full backup of the entire Linux partitions onto the external USB hard drive using [CloneZilla]("http://www.clonezilla.org/") (you may prefer the more user-friendly [RedoBackup]("http://redobackup.org/")). This means that if I totally screw up the installation, I can restore the entire drive back to where it was, and I have lost nothing. (BTW, this works brilliantly with Windows — saves you the hassle of reinstalling when viruses or BSOD plague you.)
[/LIST]
  > **ken78724 said:**
> I want a general terminal deletion to remove ubuntu studio, multiple  builds of mozilla firefox, sea monkey, opera and so forth.
All right, I don't know how you have managed to collect multiple builds of various programs. Have you not been using the package manager? If not, this is going to be a laborious, time-consuming and error-prone process.

On the other hand, if you have been using the package manager, you should always have only the latest version — the package manager *replaces* older versions with updated versions. That way, there is no need to worry about multiple builds. As I already stated, you also don't need to worry about uninstalling unused programs unless, for some reason, they cause a problem on your system.

If your hard drive is in a mess, there is only one way to clean it up. Back up as I have instructed (using cloud storage if you have the bandwidth, an external hard drive, and CloneZilla); then reinstall from scratch.

> **ken78724 said:**
> … saving photos in Opera
I did not know that that was possible. I haven't used Opera except for browsing.

> **ken78724 said:**
> … ended up with  worthless crash reports that are in my cloud, on thumb drives and DVDs
My previous comments should have clarified things. I don't know where you have been saving your data, but your crash reports should not be anywhere that you would easily find them.

Ken, I hope that I have correctly understood what you have been asking. It sounds to me that, somehow, you made things terribly complicated for yourself. Linux should be easy; if you are struggling to do something, the chances are you should be doing it a different way.

---

