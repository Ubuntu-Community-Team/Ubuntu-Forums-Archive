---
title: "MintPPC 11 vs 9.3 for 12 inch G4 Aluminum Powerbook?"
date: 2011-12-28
forum: Apple Hardware Users
---

### Post by haziz on 2011-12-28
I am currently backing up my Powerbook's data  (using terminal from a Tiger 10.4 Install disc) since the OS X install  is corrupted and will try to resurrect this machine which had been  retired for 6 years. Machine is a G4 867 MHz Powerbook with 512 Megs RAM  and a 100 gig HD.

I wish to install MintPPC.

Which version would you advise and why?

Will use it mainly for programming practice from the command line. This will not be my main machine.

Thanks.

---

### Post by rsavage on 2011-12-29
> **haziz said:**
> 
I wish to install MintPPC.
 
Which version would you advise and why?
 
None.  Because I like ubuntu.  Questions about other distributions should be made on their forums.
 
My question to you: why don't you want to install lubuntu and why?

---

### Post by 2F4U on 2011-12-29
> **haziz said:**
> I am currently backing up my Powerbook's data  (using terminal from a Tiger 10.4 Install disc) since the OS X install  is corrupted and will try to resurrect this machine which had been  retired for 6 years. Machine is a G4 867 MHz Powerbook with 512 Megs RAM  and a 100 gig HD.

I wish to install MintPPC.

Which version would you advise and why?

Will use it mainly for programming practice from the command line. This will not be my main machine.

Thanks.

You do realize that you are on the Ubuntu forums, do you? So we will, of course :D recommend Ubuntu to you. Here are the Ubuntu options available to you:

[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

Depending on what you intend to do with this machine and if you prefer current software, you should use the latest version, which is 11.10.
If you are more interested in stability you should look at 10.04, which has long term support.

---

### Post by theos911 on 2011-12-29
MintPPC versions:
9.3 for stability
11 for newer software


Most of my PPC machines are too weak for *buntu and their variants. That is why I use MintPPC 11. Haziz, your Powerbook G4 has enough strength to run MintPPC 9.3/11 and Lubuntu.

MintPPC is specifically engineered for PPC. *buntu is not and was not, and ppc isn't an official port anymore. However, *buntu is easier for someone new to Linux. MintPPC has been a steep learning curb for me.

The breakdown:

MintPPC:
Pros: Engineered for PPC, specific help for problems as we only work with Macintoshes, tighter community
Cons: More CL involved, not source compatible with *buntu packages

*buntu:
Pros: Easier to use, likely less CL
Cons: Possibly a bit slower - a good bit slower


I hope this clarifies,
Ted

---

### Post by rsavage on 2011-12-29
theos911/Ted, it's nice to see you posting on the ubuntu forums. I have read many of your posts over on the MintPPC forum. However, I would like to pull you up on one or two things you've said there.....
 
There is a lot of bile written over on MintPPC (and by it's members on other forums) directed at Ubuntu and other PPC distributions. I have never bothered correcting it before, but since you have entered the lions den so to speak you are going to get my opinion!
 
> MintPPC is specifically engineered for PPC. *buntu is not and was not, and ppc isn't an official port anymore.
Okay, lets be clear what MintPPC is. It is debian plus a few Mint packages. There is nothing specifically engineered for PPC about that. What is does do, however, is run a very short script when you install that mops up a few installation issues. For example, it adds a line to a file to make the battery work. Honestly, that's about it on the PPC specifics.
 
Ubuntu is not specifically designed for PPC, but like I say nor is Debian. PPC is in the ports directory of ubuntu. It is still compiled by canonical as far as I am aware. The PPC packages are still all on launchpad. You can look up all the source code. You can look up all the build logs. You can look up all the bugs. You certainly cannot do these things with MintPPC. Canonical staff still fix PPC bugs when they are reported and when they find them. The only difference from 'official' architectures really, is that PPC lacks the numbers for testing. This means things like the live cds do not work so well in recent versions. That is why you won't find a 11.04 and 11.10 live cd. 
 
> 
However, *buntu is easier for someone new to Linux.

The idea behind MintPPC is that it does everything for you and you shouldn't have to tweak/install anything to make it work. So, actually, with regard to recent Ubuntus then MintPPC should be easier. If it is not then MintPPC has failed and is essentially pointless IMHO. PPC ubuntu has excellent documentation (because I wrote it) so there are instructions to do all the necessary PPC tweaks. It is possible to do them all in less than 30 seconds.
 
> 
MintPPC has been a steep learning curb for me.

I think it is debian causing that. I just find sometimes debian likes to make life hard. All linux has a steepish learning curve though.
 
> 
MintPPC:
Pros: Engineered for PPC, specific help for problems as we only work with Macintoshes, tighter community
Cons: More CL involved, not source compatible with *buntu packages

Forum is friendly. Not always great/correct advice in my opinion. If your query is not PPC specific then Ubuntu offers far superior forums/guides/web sites. Hopefully, with the good PPC ubuntu documentation, you won't have to ask a question on the forum and can solve it yourself with ubuntu.
 
Not sure what you mean by source compatible. You could certainly compile the source code for MintPPC. In fact, I'm sure most binary packages would work. 
 
> 
*buntu:
Pros: Easier to use, likely less CL
Cons: Possibly a bit slower - a good bit slower

Using ubuntu I find is easier than debian. But, if you are talking setting up/installing then like I've said before MintPPC should be easier and have less command line.
Yes standard 11.04/11.10 ubuntu is slower. **However, lubuntu is faster and lighter than MintPPC**. 
 
I nearly got taken in myself with the whole debian is faster than ubuntu malarky. So I trialled the two and did extensive testing. I had no preference at the time, I was merely interested in using the fastest distribution. Since straight debian was a hassle, I installed MintPPC 9.2. I was fully expecting it to be the quickest after everything I had read. However, it was significantly slower to boot than every version of Lubuntu I tried. It was even slower than xubuntu 11.04.
 
I haven't tried MintPPC 11, but I'm guessing it will be the same. The trouble is it installs loads of stuff I don't want/need. Somebody else will have to trial it (I do not believe what linuxopjemac writes anymore - sorry JD).
 
Hopefully, I've cleared up a few of the myths that I keep reading. There should be more sharing of information between the two distributions and less bashing each other. The best thing to do - and it is what I keep writing - is install a few different distributions and stay with the one you like the best. Don't believe what others tell you.

---

### Post by rsavage on 2011-12-29
theos911, I thought you might like to look at the MintPPC 11 preseed file. I'm sure linuxopjemac won't mind since he says MintPPC is committed to open source. I have highlighted the PowerPC specific bit, just in case you thought I was exaggerating. It looks like 11 installs far fewer packages than 9.2 did.
 
```
### Apt setup
# You can choose to install non-free and contrib software.
d-i apt-setup/non-free boolean true
d-i apt-setup/contrib boolean true
# Uncomment this if you don't want to use a network mirror.
#d-i apt-setup/use_mirror boolean false
# Select which update services to use; define the mirrors to be used.
# Values shown below are the normal defaults.
d-i apt-setup/services-select multiselect security, volatile
d-i apt-setup/security_host string security.debian.org
d-i apt-setup/volatile_host string volatile.debian.org
 
# Additional repositories, local[0-9] available
d-i apt-setup/local0/repository string http://mintppc.org/repository katya main
d-i apt-setup/local0/comment string MintPPC repository
# Enable deb-src lines
#d-i apt-setup/local0/source boolean true
d-i apt-setup/local0/key string http://mintppc.org/files/mintppc11/mintppc-keyring.gpg
# URL to the public key of the local repository; you must provide a key or
# apt will complain about the unauthenticated repository and so the
# sources.list line will be left commented out
#d-i apt-setup/local0/key string http://local.server/key
 
# By default the installer requires that repositories be authenticated
# using a known gpg key. This setting can be used to disable that
# authentication. Warning: Insecure, not recommended.
#d-i debian-installer/allow_unauthenticated string true
 
### Package selection
tasksel tasksel/first multiselect standard
# If the desktop task is selected, install the kde and xfce desktops
# instead of the default gnome desktop.
#tasksel tasksel/desktop multiselect lxde
 
# Individual additional packages to install
d-i pkgsel/include string abiword apturl b43-fwcutter catfish cowsay cups exaile firestarter firmware-b43-installer firmware-linux-nonfree fortunes-husse fortune-mod galculator gedit gftp gimp gnome-alsamixer gnome-disk-utility gnome-alsamixer gnome-mplayer gnome-nettool gnome-run-dialog gimp gnome-screenshot gnome-system-tools gnome-wise-icon-theme gnumeric gparted gufw hardinfo icedove iceweasel icedtea6-plugin lxappearance lxde lxkeymap lxtask openjdk-6-jre midori minitube mmouseemu network-manager-gnome ntp obconf pidgin seahorse simple-scan system-config-printer transmission update-manager-gnome update-notifier vlc xchat xfburn mint-artwork-common mint-artwork-lxde mint-backgrounds-helena mint-backgrounds-isadora mint-backgrounds-julia mint-backgrounds-katya mint-backgrounds-katya-extra mint-common mint-elementary-icons mint-info-lxde mint-lxde-default-settings mint-translations mint-x-icons mint-x-theme mintbackup mintdesktop mintinstall mintmenu mintnanny mintppc11-backgrounds mintppc-gdm-themes mintsystem mintwelcome **[SIZE=2][COLOR=red]powerprefs[/COLOR][/SIZE]** python-webkit python-vte
 
# Whether to upgrade packages after debootstrap.
# Allowed values: none, safe-upgrade, full-upgrade
#d-i pkgsel/upgrade select none
 
# Some versions of the installer can report back on what software you have
# installed, and what software you use. The default is not to report back,
# but sending reports helps the project determine what software is most
# popular and include it on CDs.
popularity-contest popularity-contest/participate boolean false
 
# This command is run just before the install finishes, but when there is
# still a usable /target directory. You can chroot to /target and use it
# directly, or use the apt-install and in-target commands to easily install
# packages and run commands in the target system.
#d-i preseed/late_command string apt-install zsh; in-target chsh -s /bin/zsh
d-i preseed/late_command string \
**[SIZE=2][COLOR=red]echo 'pmu_battery' >> /target/etc/modules; \[/COLOR][/SIZE]**
**[SIZE=2][COLOR=red]echo 'i2c-dev' >> /target/etc/modules; \[/COLOR][/SIZE]**
echo '' > /target/etc/motd.tail; \
echo '' >> /target/etc/motd.tail; \
echo 'The programs included with this build of MintPPC GNU/Linux are free software;' >> /target/etc/motd.tail; \
echo 'the exact distribution terms for each program are described in the' >> /target/etc/motd.tail; \
echo 'individual files in /usr/share/doc/*/copyright.' >> /target/etc/motd.tail; \
echo '' >> /target/etc/motd.tail; \
echo 'This build of MintPPC GNU/Linux comes with ABSOLUTELY NO WARRANTY,' >> /target/etc/motd.tail; \
echo 'to the extent permitted by applicable law.' >> /target/etc/motd.tail; \
echo '' >> /target/etc/motd.tail; \
echo 'More information about MintPPC GNU/Linux can be found at:' >> /target/etc/motd.tail; \
echo 'http://mintppc.org/' >> /target/etc/motd.tail; \
echo '' >> /target/etc/motd.tail; \
in-target wget http://mintppc.org/files/mintppc201107/repository/pool/gtk2-engines-candido_0.9.1-1_powerpc.deb; \
in-target dpkg -i gtk2-engines-candido_0.9.1-1_powerpc.deb; \
in-target rm gtk2-engines-candido_0.9.1-1_powerpc.deb; \
in-target apt-get install -y mint-artwork-gnome; \
in-target wget http://debian-multimedia.org/pool/main/libd/libdvdcss/libdvdcss2_1.2.11-0.0_powerpc.deb; \
in-target dpkg -i libdvdcss2_1.2.11-0.0_powerpc.deb; \
in-target rm libdvdcss2_1.2.11-0.0_powerpc.deb;

```

---

### Post by theos911 on 2011-12-29
> However, I would like to pull you up on one or two things you've said there.....Like what? You can search my posts over there for "ubuntu". I've not said a negative word about it. Some others, Yes, have not had the nicest time with it, but do not attribute that to me.

> There is nothing specifically engineered for PPC about that.I've spoken to JD about this issue. He told me that modifications to the mint packages used in MintPPC go a good bit beyond simply rebuilding for a different arch. I won't actually be building packages for MintPPC until a few weeks from now. Thus, I do not know how significant the changes are. I'll take him at his word on this. Whether you do or not, is up to you.

> The idea behind MintPPC is that it does everything for you and you shouldn't have to tweak/install anything to make it work.I just installed MintPPC 11 yesterday. There was no tweaking needed. Everything went fine. There was a minor issue with my Xorg.conf due to a new "dri" in debian wheezy. However, JD and I patched the file and it is now the default for that machine.

> If it is not then MintPPC has failed and is essentially pointless IMHO.Most of the people using MintPPC and PPC Lubuntu are former mac users. Most mac users are accustomed to easy installation. They are often not familiar with the CLI. MintPPC's install doesn't require any CLI tweaks. You are saying that *buntu has good documentation for the tweaks they need to do post install. That is excellent. With that documentation, PPC *buntu users can now easily do the things that are done automatically for MintPPC users.

> I think it is debian causing that. I just find sometimes debian likes to  make life hard. All linux has a steepish learning curve though.Yes, yes it does. That might be one of the few things we'll agree on.

> Not always great/correct advice in my opinion. If your query is not PPC  specific then Ubuntu offers far superior forums/guides/web sites.Again, given the audience, our forums are more about giving the easiest to implement answer to fix the issue. Sometimes this means it isn't the most correct answer and it may be a bit kludgey, but it is intended to be easy for someone not familiar with linux to implement.

> Not sure what you mean by source compatible. You could certainly compile  the source code for MintPPC. In fact, I'm sure most binary packages  would work. Sorry, meant binary compatible. We don't have an equivalent to the software center. *buntu is easier to install software on in that regard.

> Using ubuntu I find is easier than debian.I use Ubuntu on my x86 box. I agree with that. I prefer Ubuntu to plain Debian. However, MintPPC is a lot closer to Linux Mint than to plain Debian.

> But, if you are talking setting up/installing then like I've said before MintPPC should be easier and have less command line.I'm not sure what you mean. Almost all of our installs involve no CLI. I'm not sure how it can get less than 0 CLI. As for ease, on a new world, you pop in the cd and go. The only commands you need are:
```
install url=mintppc.org
```That is it. It usually goes on without an issue. I'm not going to go into Old World, because PPC Lubuntu & MintPPC have the exact same issues that must be solved the exact same way, so no use beating that horse.

> Yes standard 11.04/11.10 ubuntu is slower.We agree on that then.

> **However, lubuntu is faster and lighter than MintPPC**.  Please provide your benchmarks. I will be testing this as soon as I can and will post my benchmarks as well.

>  less bashing each other.Pardon me, but I don't think I've done any bashing.

---

### Post by rsavage on 2011-12-29
> **theos911 said:**
> Like what? You can search my posts over there for "ubuntu". I've not said a negative word about it. Some others, Yes, have not had the nicest time with it, but do not attribute that to me.
 
I think you have misunderstood my post as attacking you. That was not my intention and probably my fault for poor wording. When I wrote "*However, I would like to pull you up on one or two things you've said there.....*" it was referring to your original post in this thread. Since I then went on to explain what I thought was incorrect I thought this was apparent.
 
However, since you do bring up your mintppc posts, the classic that has always stuck in my mind was "*PPC Ubuntu is basically PPC Debian and PPC GNOME with no glue between them.*". Posted Wed 9th Nov.
 
> 
I've spoken to JD about this issue. He told me that modifications to the mint packages used in MintPPC go a good bit beyond simply rebuilding for a different arch. I won't actually be building packages for MintPPC until a few weeks from now. Thus, I do not know how significant the changes are. I'll take him at his word on this. Whether you do or not, is up to you.
That is not the impression he has given here when the lack of source code was queried. 
 
> 
I just installed MintPPC 11 yesterday. There was no tweaking needed. Everything went fine. There was a minor issue with my Xorg.conf due to a new "dri" in debian wheezy. However, JD and I patched the file and it is now the default in the script to prevent anyone else from needing to fix it.

Not sure what you are on about there. There is no reference to dri in the script. However, you do bring up one of my main problems with MintPPC. The secrecy. Any solutions you do find are not open for others to benefit. I hope you have fed your solution back to debian developers.  MintPPC is the only distribution I know where the documentation is password protected.
 
>  
I'm not sure what you mean. Almost all of our installs involve no CLI. I'm not sure how it can get less than 0 CLI. 
I don't think that is really true. The MintPPC forums are much busier than the Apple Ubuntu forum. Installing those awful xorg.conf files in 9.3 spring to mind. But, like I say, since a lot of stuff is automated for you then you have less or zero cli involvement in an install. I think we are agreed. It was a compliment btw so not sure why you are arguing. 
 
> 
Please provide your benchmarks. I will be testing this as soon as I can and will post my benchmarks as well.

Some of them I printed on the forum at the time. I cannot give you them since I've probably chucked the bit of paper they were scribbled on.  If you look now at the MintPPC 11 packages and the lubuntu packages they are very similar now.  MintPPC has slimmed down and is now benefiting (like ubuntu 11.04 and 11.10) from a faster kernel.
 
> 
Pardon me, but I don't think I've done any bashing.
Don't think I accused you of any. I was writing in general.  I have a major problem with threads like this [http://www.mintppc.org/forums/viewtopic.php?f=18&t=558](http://www.mintppc.org/forums/viewtopic.php?f=18&t=558) .

---

### Post by linuxopjemac on 2011-12-29
For the sake of clarification, I will highlight what is specific for MintPPC and PPC users in general in that preseed file.

### Apt setup
# You can choose to install non-free and contrib software.
d-i apt-setup/non-free boolean true
d-i apt-setup/contrib boolean true
# Uncomment this if you don't want to use a network mirror.
#d-i apt-setup/use_mirror boolean false
# Select which update services to use; define the mirrors to be used.
# Values shown below are the normal defaults.
d-i apt-setup/services-select multiselect security, volatile
d-i apt-setup/security_host string security.debian.org
d-i apt-setup/volatile_host string volatile.debian.org
 
# Additional repositories, local[0-9] available
[B]d-i apt-setup/local0/repository string [http://mintppc.org/repository](http://mintppc.org/repository) katya main
d-i apt-setup/local0/comment string MintPPC repository[/B]
# Enable deb-src lines
#d-i apt-setup/local0/source boolean true
```
d-i apt-setup/local0/key string http://mintppc.org/files/mintppc11/mintppc-keyring.gpg
```
# URL to the public key of the local repository; you must provide a key or
# apt will complain about the unauthenticated repository and so the
# sources.list line will be left commented out
#d-i apt-setup/local0/key string [http://local.server/key](http://local.server/key)
 
# By default the installer requires that repositories be authenticated
# using a known gpg key. This setting can be used to disable that
# authentication. Warning: Insecure, not recommended.
#d-i debian-installer/allow_unauthenticated string true
 
### Package selection
tasksel tasksel/first multiselect standard
# If the desktop task is selected, install the kde and xfce desktops
# instead of the default gnome desktop.
#tasksel tasksel/desktop multiselect lxde
 
# Individual additional packages to install
d-i pkgsel/include string abiword apturl **b43-fwcutter** catfish cowsay cups exaile firestarter **firmware-b43-installer firmware-linux-nonfree fortunes-husse fortune-mod** galculator gedit gftp gimp gnome-alsamixer gnome-disk-utility gnome-alsamixer gnome-mplayer gnome-nettool gnome-run-dialog gimp gnome-screenshot gnome-system-tools gnome-wise-icon-theme gnumeric gparted gufw hardinfo icedove iceweasel icedtea6-plugin lxappearance lxde lxkeymap lxtask openjdk-6-jre midori minitube mmouseemu network-manager-gnome ntp obconf pidgin seahorse simple-scan system-config-printer transmission update-manager-gnome update-notifier vlc xchat xfburn **mint-artwork-common mint-artwork-lxde mint-backgrounds-helena mint-backgrounds-isadora mint-backgrounds-julia mint-backgrounds-katya mint-backgrounds-katya-extra mint-common mint-elementary-icons mint-info-lxde mint-lxde-default-settings mint-translations mint-x-icons mint-x-theme mintbackup mintdesktop mintinstall mintmenu mintnanny mintppc11-backgrounds mintppc-gdm-themes mintsystem mintwelcome powerprefs python-webkit python-vte**
 
# Whether to upgrade packages after debootstrap.
# Allowed values: none, safe-upgrade, full-upgrade
#d-i pkgsel/upgrade select none
 
# Some versions of the installer can report back on what software you have
# installed, and what software you use. The default is not to report back,
# but sending reports helps the project determine what software is most
# popular and include it on CDs.
popularity-contest popularity-contest/participate boolean false
 
# This command is run just before the install finishes, but when there is
# still a usable /target directory. You can chroot to /target and use it
# directly, or use the apt-install and in-target commands to easily install
# packages and run commands in the target system.
#d-i preseed/late_command string apt-install zsh; in-target chsh -s /bin/zsh
d-i preseed/late_command string \
[B]echo 'pmu_battery' >> /target/etc/modules; \
echo 'i2c-dev' >> /target/etc/modules; \
echo '' > /target/etc/motd.tail; \
echo '' >> /target/etc/motd.tail; \
echo 'The programs included with this build of MintPPC GNU/Linux are free software;' >> /target/etc/motd.tail; \
echo 'the exact distribution terms for each program are described in the' >> /target/etc/motd.tail; \
echo 'individual files in /usr/share/doc/*/copyright.' >> /target/etc/motd.tail; \
echo '' >> /target/etc/motd.tail; \
echo 'This build of MintPPC GNU/Linux comes with ABSOLUTELY NO WARRANTY,' >> /target/etc/motd.tail; \
echo 'to the extent permitted by applicable law.' >> /target/etc/motd.tail; \
echo '' >> /target/etc/motd.tail; \
echo 'More information about MintPPC GNU/Linux can be found at:' >> /target/etc/motd.tail; \
echo 'http://mintppc.org/' >> /target/etc/motd.tail; \
echo '' >> /target/etc/motd.tail; \
in-target wget [http://mintppc.org/files/mintppc201107/repository/pool/gtk2-engines-candido_0.9.1-1_powerpc.deb;](http://mintppc.org/files/mintppc201107/repository/pool/gtk2-engines-candido_0.9.1-1_powerpc.deb;) \
in-target dpkg -i gtk2-engines-candido_0.9.1-1_powerpc.deb; \
in-target rm gtk2-engines-candido_0.9.1-1_powerpc.deb; \
in-target apt-get install -y mint-artwork-gnome; \
in-target wget [http://debian-multimedia.org/pool/main/libd/libdvdcss/libdvdcss2_1.2.11-0.0_powerpc.deb;](http://debian-multimedia.org/pool/main/libd/libdvdcss/libdvdcss2_1.2.11-0.0_powerpc.deb;) \
in-target dpkg -i libdvdcss2_1.2.11-0.0_powerpc.deb; \
in-target rm libdvdcss2_1.2.11-0.0_powerpc.deb;[/B]

I have to also point out, that many of these 'mint' packages are not just rebuilt from mint source but actually adapted for ppc. The source code was adapted. I had to also introduce new mintppc specific packages to make it all work and to set more configurations under the hood.

I hope this clears things up rsavage.

---

### Post by theos911 on 2011-12-29
> "*PPC Ubuntu is basically PPC Debian and PPC GNOME with no glue between them.*"I'm not sure what you mean by quoting that here...
Are you saying that PPC Ubuntu **does** have that? Or that you feel it is negative in some way?

> That is not the impression he has given here when the lack of source code was queried. I have not started building yet. When I do so, I imagine things will be clear.

> Not sure what you are on about there. There is no reference to dri in  the script. However, you do bring up one of my main problems with  MintPPC. The secrecy. Any solutions you do find are not open for others  to benefit. I hope you have fed your solution back to debian developers.   MintPPC is the only distribution I know where the documentation is  password protected.A. That was a miswording on my part. My brain had already skipped forward to the script. I edited the post to reflect this, but it looks as though you had already hit quote.

B. The solution to the exact problem I was speaking about is completely available at [http://mac.linux.be/files/xorg/g3_450.txt](http://mac.linux.be/files/xorg/g3_450.txt) . Anyone can download this and benefit, no secrecy.

C. You make a good point. I do not like password locked docs either. JD and I are discussing options about unlocking them.

D. The Debian devs have been aware since at least spring of this year. Unfortunately, it hasn't been addressed.

> I don't think that is really true.That is your opinion. Do your own install and see. Unless you still haven't talked to JD about a password, [I]ojordan.

[/I]>  Installing those awful xorg.conf files in 9.3 spring to mind.In 11, most configs work fine with no xorg file. However, those suffering from the r128 error I ran into yesterday will need a specific file disabling the now broken features.

> not sure why you are arguing. I was arguing because you seemed to insinuate that PPC Lubuntu was easier to install than MintPPC, thus by your own words "making MintPPC pointless".

>  I have a major problem with threads like this [http://www.mintppc.org/forums/viewtopic.php?f=18&t=558](http://www.mintppc.org/forums/viewtopic.php?f=18&t=558) .While, agreeably, not in the best taste, he was expressing that he feels the distro to be very slow. Is that an issue?

On the topic of your distro. I went to lubuntu.net and couldn't find any ppc iso or instructions anywhere. How is that user friendly?


Thank you, JD, for clarifying on the script.

---

### Post by theos911 on 2011-12-31
JD and I discussed the matter for a good while. The documentation on [www.mintppc.org]("http://www.mintppc.org") is now fully public. No more need for a password. Anyone is free to come and try it out now.

---

