---
title: "How to migrate from Ubuntu to Mint"
date: 2011-10-22
forum: Any Other OS
---

### Post by mpiter on 2011-10-22
According to many users that have recently gave up Ubuntu for Mint, switching from Ubuntu to Mint is not a very difficult task. Many are happy with the change. Since Mint 11 is based on Ubuntu 11.04, it might be easier to hop from Ubuntu 11.04 than from another version. I have just installed Mint from scratch on a test computer, and it seems promising. I however have not tested yet the process described below.  It is just a summary of hours of reading about that topic.  I will migrate myself on my main computer in a few days.

The principle of the migration would be:[LIST=1]
[*]Use [COLOR="Green"]etckeeper[/COLOR] tool to save [COLOR="green"]/etc[/COLOR] in a repository;
[*]Use [COLOR="green"]mintbackup[/COLOR] to save the list of packages that you have installed yourself after the first Ubuntu installation;
[*]Install Mint from the live DVD in a new partition or over Ubuntu;
[*]Reboot in Mint and restore the supplementary packages using the Mint Backup tool which is compatible with [COLOR="green"]mintbackup[/COLOR];
[*]Tune [COLOR="green"]/etc[/COLOR] with the help of your previously saved [COLOR="green"]/etc[/COLOR] repository.
[/LIST]

Rebuild [COLOR="green"]/usr/local[/COLOR].

Of course, user data needs to be backed up and restored too. When you have successfully restored user data on your new Mint system, it is advised to erase a few hidden directories from the user home directories [COLOR="Red"]BEFORE[/COLOR] they login. This includes [COLOR="Green"].gconf[/COLOR], [COLOR="green"].gconfd[/COLOR], [COLOR="green"].config[/COLOR], and a few others. I do not remember where I saw the complete list of directories to be erased. It was in one of the links that I provide in this post or in a thread related to Mint upgrade in this forum: [[COLOR="Blue"]http://forums.linuxmint.com/viewforum.php?f=46[/COLOR]]("http://forums.linuxmint.com/viewforum.php?f=46"). With a little search, you will find the list. The reason behind this is that an obsolete [COLOR="Green"].gconf[/COLOR] might be more difficult to handle than a new one if you do not have exactly the same versions of the softwares handled by [COLOR="Green"]gconf-editor[/COLOR]. Because there are a little bit more graphical tools to configure a desktop on Mint than on Ubuntu, recreating a known configuration might be easier than facing incompatibility problems due to an obsolete desktop configuration. I have never used Mint, so I cannot confirmed this.

Here are the main Web pages I have read [[COLOR="Blue"]http://community.linuxmint.com/tutorial/view/2[/COLOR]]("http://community.linuxmint.com/tutorial/view/2") to understand the general Mint upgrade model and to apply it to your Ubuntu-to-Mint migration. [[COLOR="blue"]http://aymanh.com/version-control-linux-configuration-files-etc-etckeeper[/COLOR]]("http://aymanh.com/version-control-linux-configuration-files-etc-etckeeper") to manage [COLOR="green"]/etc[/COLOR] in a repository. [[COLOR="blue"]http://forums.linuxmint.com/viewtopic.php?f=46&t=83347[/COLOR]]("http://forums.linuxmint.com/viewtopic.php?f=46&t=83347") to upgrade from Ubuntu 11.04 to Mint 11 with not too much effort, including how to install [COLOR="Green"]mintbackup[/COLOR] on Ubuntu. Of course the last link will give you access to the Mint forum where you can find a lot of help.

As I wrote above, I have already started to install and configured Mint 11 on a test computer.  It really feels like being on Ubuntu, but slightly different.  When I have finished my test I will try the process described above.  I may write in one or two weeks a tutorial actually based on a real experience.

---

### Post by gbrowne on 2012-07-02
Hi mpiter,

Did you ever successfully migrate from Ubuntu 11 to Mint 13 ?  I would be interested to read a followup to your original post ?

Cheers,
GB

---

### Post by mpiter on 2012-07-02
> **gbrowne said:**
> Did you ever successfully migrate from Ubuntu 11 to Mint 13 ?  I would be interested to read a followup to your original post ?

Yes, I firstly migrated from Ubuntu 11.04 to Linux Mint 11 (based on Linux Mint 11), then to Linux Mint 12 (based on Ubuntu 11.10), and then to Linux Mint 13 (the LTS version based on Ubuntu 12.04).  I also just finished this morning a direct Ubuntu 11.04 to Linux Mint 13 migration and carried out last week a Linux Mint 11 to 13 migration.

My analysis after 9 month of Linux Mint use is that this distro in fully desktop-oriented and more user-oriented that Ubuntu.  I think that Clem, the Mint guru, is always listening to users and is always trying to satisfy a maximum of them.  I think he wants us to benefit from the best classical desktop experience he can provide with stability, ease of use, and user-satisfaction in mind.  If you want a large-public oriented distro that can run on tablets as well as on desktops with fancy original features to play with, go to Ubuntu.  If you want a more serious distribution aimed at stable development on desktops and laptops, go to Mint.  For example, I do not think that Clem would dare to launch on the market a "stable" release which is actually a beta release as Marc Shuttleworth did with Ubuntu 11.04.  From time to time, Clem provides an RC release requesting adventurous users to test it during a month before sending the stable release.  But at least, you know it is an RC release.

Up to now, I have mainly seen advantages to use Linux Mint over Ubuntu when you want a trustworthy production tool.  The only con I have spotted in 9 months is that the forums are less crowded.  When you face a problem, you are more likely to receive a quick answer in Ubuntu forums.  It however evolves quickly over time as Mint becomes more popular.

Now, the migration.  My first experience was totally satisfying.  The step from Ubuntu 11.04 to Linux Mint 11 was easy.  I did it in the end of October.  I just did what I had written in the first post of this thread.  I did not find hidden problems and the full migration took me about a day.  Mint 11 seemed to me more stable and more user friendly.  It felt like eventually recovering a stable computer for production after several months of hassles with Ubuntu 11.04.  I could only praise Mint at that time for their seriousness and their user-oriented approach.  Their menu is particularly nice and well thought.

I felt Gnome 3 very appealing and I was impatient to try it.  I therefore migrated to Linux Mint 12 around November or December.  I again followed the process detailed in the first post of this thread (a full installation instead of an upgrade).  The migration was easy again.  The experience was however less pleasant after.  I tried the pure Gnome shell 3.2 with the tweaking tools provided by Mint.  To my needs, it was much better than Unity but still unsatisfying for heavy development in comparison to Gnome 2.32 with Compiz.  I was working on a 8-thread Genuine Intel i7 CPU Q 840 at 1.87GHz with 4 GB of RAM.  Even with that configuration, the Gnome Shell was too slow to be comfortable to use.  For example, when I typed a simple text in Emacs, I had to wait a split of a second before seeing the characters on the screen.  Usually, I see the letters as soon as I type them.  Some times the computer became deadly slow for a few seconds. What a pain!  It also lacked many features that I consider important for my use.  So too slow and lacking too many features.

Gnome 2.32 was not available anymore and its replacement called Mate was still in beta.  I did not want to test it because I knew that is was far from stable.  It was written on Linux Mint Web site.  They did not try to cheat people and it was not advise to use it for production purposes.  I had kept working with Gnome 3.2 for about 4 months when I discovered around April that Mint was working on their own Gnome shell called Cinnamon.  I tried it for a couple of months.  I think it corrects several shortcomings of Gnome 3.2 and is more pleasant to use.  I really like it but it is also too slow, maybe because it is also a Gnome shell.  I start to think that CSS interpretation for dynamic behavior is just too resource consuming for many today computers.  I therefore decided to come back to GTK 2 desktops. I will probably not try anything anymore based on GTK 3 with current technologies.

To me, Linux Mint 12 was eventually disappointing when it ran Gnome shells.  I am happy to have tested this, but I kept Linux Mint 11 on all other computers that I manage.

10 days ago, I installed Linux Mint 13 based on Ubuntu 12.04.  I choose the Mate version, i.e., the Gnome 2.32 clone based on GTK 2.  What a pleasure to work again with a responsive computer that does not lag for unknown reasons :p.  I have only used it for about 10 days but I have no complains so far.  I therefore decided to migrate other computers to Mint 13.

I finished this morning to migrate a Ubuntu 11.04 computer to Linux Mint 13, Mate version.  I also migrated last week a Linux Mint 11 to Linux Mint 13, Mate version.  Both computers originally used Gnome 2.32 with Compiz.  I left one with Mate, I installed Compiz on the other one.

Now the concrete pieces of advice if you want upgrade Ubuntu 11.04 to Mint 13.

In contrast to what I wrote in the first post of this thread, I advise you to keep the [COLOR="Magenta"].gconf[/COLOR] and other dot files.  They contained so many configuration values of so many pieces of software that getting rid of the old values requests a lot of work to rebuild them.  I lost a lot of time trying to remember everything from scratch.  For my last migrations, I kept all the dot files and I reached my goals much quicker.  I am going to edit my first post about that.

If your mail client is Evolution, be careful.  Evolution mail format was [COLOR="YellowGreen"]mbox[/COLOR] till version 2.32 and the format switched to [COLOR="YellowGreen"]maildir[/COLOR] with version 3.0.  When you migrate a computer based on Ubuntu 11.04 or older (same for Mint 11 or older) to a more recent version, Evolution suggests to migrate your [COLOR="YellowGreen"]mbox[/COLOR] format to a [COLOR="YellowGreen"]maildir[/COLOR] one.  Accept the suggestion because managing oneself the migration is a bit tedious.  When you click the button to accept, the dialog window disappears and nothing seems to happen for several minutes if you have a lot of emails.  The first time, I thought Evolution had crashed and I ran a second occurrence.  I ended up with all emails duplicated.  If you happen to make the mistake, get out of Evolution and type in a terminal:
```
cd ~/.local/share/evolution/mail
rm -rf local
mv local_mbox local

```
And run Evolution again.  Be patient, he will silently make the migration when you accept it, and a few minutes later it will open the client as usual.  As long as nothing happens on the screen, Evolution is working on the translation.  Once the client window appears, check that the migration was correctly done, then you can erase the [COLOR="YellowGreen"]mbox[/COLOR] backup.  If you prefer to do the email migration yourself (I strongly advise not to do that) you can read the tutorial I wrote about it: [[COLOR="RoyalBlue"]http://forums.linuxmint.com/viewtopic.php?f=42&t=88648[/COLOR]]("http://forums.linuxmint.com/viewtopic.php?f=42&t=88648")

The other trap I found was running Compiz in Linux Mint 13.  If you blindly run [COLOR="Magenta"]compiz --replace[/COLOR], Compiz and [COLOR="YellowGreen"]marco[/COLOR] (the Mate window manager) will compete in parallel eating a lot of resources.  Follow this tutorial if you want to run Compiz: [[COLOR="RoyalBlue"]http://community.linuxmint.com/tutorial/view/919[/COLOR]]("http://community.linuxmint.com/tutorial/view/919").  I did it, and it seemed to work well.  I have not used the computer for long after installing Compiz on Linux Mint 13, so I cannot judge its quality with that distribution.  It still seems powerful, full of features, but conflicting with the other window manager settings making the piece of software hard to manage.  I still love it though.

Finally, when I migrated a Ubuntu 11.04 computer to Linux Mint 13, I could not install [COLOR="Magenta"]mintbackup[/COLOR].  The PPA did not work, and I eventually downloaded a [COLOR="Magenta"].deb[/COLOR] file to install it.  I do not remember where I found it, but it might be from the Linux Mint repository: [[COLOR="RoyalBlue"]http://packages.linuxmint.com/[/COLOR]]("http://packages.linuxmint.com/")  Take the [[COLOR="RoyalBlue"]Linux Mint 11 Katya[/COLOR]]("http://packages.linuxmint.com/list.php?release=Katya") link to find the [COLOR="Magenta"]mintbackup[/COLOR] package.

Of course, I will never insist enough on making good backups.

In summary, if you are a developer or want a serious desktop that is stable, trustworthy, consuming few resources, without needs to run the same OS on traditional computers and tablets, but still easy to use and maintain, my pieces of advise are:
[LIST=1]
[*]Avoid Ubuntu too adventurous without respect for its user base (cf. the Ubuntu 11.04 release).
[*]Avoid any window manager based on GTK3 such as Gnome shells because they seem to eat a lot of resources.
[/LIST]

Now, I am testing a pure Mate desktop on Linux Mint 13.  In a couple of months, I will add Compiz to check it again (I used it during several years and I miss it).  Then I will try Linux Mint 13 XFCE version.  This version has just been released as an RC release.  We can expect the stable release in about a month.  It will probably be lighter than Mate, although it is based on Ubuntu instead of Xubuntu and although nobody has made benchmarks to compare the two versions.  As usual, when Clem takes something in hand, he adds marvelous things in comparison the standard.  In this particular case, all Mate applets (gnome applet clones) can be used on the XFCE panel, including the Linux Mint menu.

Of course, Ubuntu has also advantages over Linux Mint including an original way to handle the desktop, a bigger user base, the plan to run it on tablets and computer...  There are good arguments for that OS.  For professional uses, such as in my case, I prefer Clem to Marc Shuttleworth philosophy after experiencing both.

Take care.

---

### Post by kurt18947 on 2012-07-02
> **gbrowne said:**
> Hi mpiter,

Did you ever successfully migrate from Ubuntu 11 to Mint 13 ?  I would be interested to read a followup to your original post ?

Cheers,
GB

I kind of like Cinnamon's design.  I do have one complaint in Mint 13 though.  I did a fresh install and have twice had FireFox lock up TIGHT.  <SysRq>+alt+k didn't do anything.  I've actually had better luck installing Cinnamon on Ubuntu 12.04.  I didn't install muffin in that case and it seems to work fine.

---

### Post by gbrowne on 2012-07-03
> **mpiter said:**
> Yes, I firstly migrated from Ubuntu 11.04 to Linux Mint 11 (based on Linux Mint 11), then to Linux Mint 12 (based on Ubuntu 11.10), and then to Linux Mint 13 (the LTS version based on Ubuntu 12.04).  I also just finished this morning a direct Ubuntu 11.04 to Linux Mint 13 migration and carried out last week a Linux Mint 11 to 13 migration....

mpiter, thank you so much for your excellent analysis and helpful advice and suggestions.  I will certainly try a dual boot Mint13 next.  I was going to use Cinnamon, but may reconsider MATE after what you have said about being so resource hungry though.  As for Compiz, I'm not sure I'm so bothered?

Thanks again,
GB.

---

### Post by mpiter on 2012-07-03
> **kurt18947 said:**
> I kind of like Cinnamon's design.  I do have one complaint in Mint 13 though.  I did a fresh install and have twice had FireFox lock up TIGHT.  <SysRq>+alt+k didn't do anything.  I've actually had better luck installing Cinnamon on Ubuntu 12.04.  I didn't install muffin in that case and it seems to work fine.

I have recently used Cinnamon 1.4 for a couple of months with Linux Mint 12.  I had a freeze maybe once every 40 to 50 hours of computer use.  It was not pleasant but bearable for a very young desktop evolving very quickly.  I was impatient to see version 1.5, but I gave up that Gnome shell for Mate because it ate too much resource.  Finally, I prefer Mate (Gnome 2.32 clone) design and I do not plan to go back to Cinnamon.

---

### Post by mpiter on 2012-07-03
> **gbrowne said:**
> I was going to use Cinnamon, but may reconsider MATE after what you have said about being so resource hungry though.  As for Compiz, I'm not sure I'm so bothered?

It is claimed that Cinnamon performances, and more generally Gnome shells and GTK 3 performances, depend a lot on your hardware.  You might be very happy with Cinnamon on your computer configuration, but as a general rule of thumb I try to avoid systems requiring powerful up-to-date hardware.  The modest resource needs of Linux is something that I like.

---

### Post by gbrowne on 2012-07-03
> **mpiter said:**
> It is claimed that Cinnamon performances, and more generally Gnome shells and GTK 3 performances, depend a lot on your hardware.  You might be very happy with Cinnamon on your computer configuration, but as a general rule of thumb I try to avoid systems requiring powerful up-to-date hardware.  The modest resource needs of Linux is something that I like.

I quite agree mpiter.  Another consideration for me is I'm using an Nvidia Quadro FX3700M and I'm not sure how good the drivers are under Gnome3 code.
GB

---

### Post by mpiter on 2012-07-03
> **gbrowne said:**
> Another consideration for me is I'm using an Nvidia Quadro FX3700M and I'm not sure how good the drivers are under Gnome3 code.

If I remember well, this is an old Nvidia card.  Presently, the Nvidia driver 295.40 is provided with Linux Mint 13.  There is a known bug in this driver that randomly freezes your computer very frequently when composite is on with old graphic cards.  If you suffer from this bug, expect a freeze every 5 minutes needing you to reboot your computer.  So do not panic if your computer freezes soon after Linux Mint 13 installation, there are solutions.

Among the solutions, you can install a more recent version of the Nvidia driver (at least 295.49), it solves the problems for some cards.  Google to find out how to do it.  Another possibility that I used on a GEFORCE 8400M graphic card was to install a driver from the old 173 series.  The only problem is that the Xorg API has changed since then, and you have to downgrade Xorg to be able to install an old Nvidia driver 173.x.  Here is a tutorial to do that: [[COLOR="Blue"]http://forums.linuxmint.com/viewtopic.php?f=42&t=102602&p=581957&hilit=geforce+8400#p581957[/COLOR]]("http://forums.linuxmint.com/viewtopic.php?f=42&t=102602&p=581957&hilit=geforce+8400#p581957").  I hope that you will not be victim of that bug.  I read that Nvidia claimed to work to sort this bug out.

---

