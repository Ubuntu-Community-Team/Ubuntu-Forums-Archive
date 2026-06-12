---
title: "Movies  with Feisty"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by RichPicker on 2007-05-08
Hi folds. I played movies with Edgy using gxine and kaffeine. I'm now running Feisty, and those players wont' work. 

I must install something else?  

Thanks

---

### Post by taurus on 2007-05-08
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by RichPicker on 2007-05-08
Thank you.

When I installed the Ubuntu-Restricted Formats I got the following errors:

E: /var/cache/apt/archives/sun-java6-bin_6-00-2ubuntu2_i386.deb: subprocess pre-installation script returned error exit status 1
E: /var/cache/apt/archives/sun-java6-jre_6-00-2ubuntu2_all.deb: subprocess pre-installation script returned error exit status 1

I moved on and installed feisty/free/libdvdcss_1.2.9.orig..   And now the following resides on my desktop:

libdvdcss_1.2.9.orig.tar.gz

I'm lost.

---

### Post by RichPicker on 2007-05-08
I'm getting this message:

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.


Sorry, but I'm too new for this.

---

### Post by taurus on 2007-05-08
applications -> Accessories -> Terminal
```
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by RichPicker on 2007-05-08
rich@rich-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  guile-1.6 guile-1.8 lilypond-data tetex-base liboggflac3 guile-1.8-libs
  tetex-bin blt libgmp3c2 libt1-5 freepats libxml1 libgdk-pixbuf2 libglade0
  tex-common texinfo
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
rich@rich-laptop:~$ sudo apt-get install update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package update
rich@rich-laptop:~$ sudo apt-get install upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package upgrade
rich@rich-laptop:~$

---

### Post by floke on 2007-05-08
sudo apt-get upgrade - NO INSTALL - not sudo apt-get install upgrade!!
Same with update

---

### Post by RichPicker on 2007-05-08
Got it. Thanks.

update looks good. but
upgrade looks like this:

rich@rich-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  xserver-xorg-video-intel
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
rich@rich-laptop:~$

---

### Post by RichPicker on 2007-05-08
In the instructions for installing  libdvdcss, I get to here, and then get lost. There  is no such option with the right mouse button

# Right click on the package you just downloaded.
# Select Ubuntu Package Menu.
# Choose Install Package.

This is on my desktop, how do I install it?

 /home/rich/Desktop/libdvdcss_1.2.9.orig.tar.gz

---

### Post by RichPicker on 2007-05-08
Still no luck. The Update Manager alerted me, and I accepted the updates, which were for kaffeine and the libdvdcss, but still NO movie plays with kaffeine or gxine. Movies played on both of these with Edgy. Is there a problem with Feisty?

---

### Post by dangerousnerd on 2007-05-08
Just putting this out there... Have you tried VLC?  It's light weight and plays [SIZE="1"](almost)[/SIZE] everything I've thrown at it (even those .flvs you get from youtube).  It works fine on Feisty. :)

---

### Post by H.E. Pennypacker on 2007-05-08
Whenever you get instructions to use the terminal, please avoid them.  Use Automatix to install codecs ([www.getautomatix.com)](www.getautomatix.com)).

Please see [www.getautomatix.com](www.getautomatix.com) for any questions specific to Automatix.

---

### Post by RichPicker on 2007-05-08
Thank you, both of you.

VLC works great. 

I installed Automatix, and then installed the Multimedia Codecs with Automatix. Now all the players work perfectly. Gxine, Kaffeine, VLC, and Totem.

Thank you very much.
Multumesc fuarte mult.

---

### Post by matthew on 2007-05-09
> **H.E. Pennypacker said:**
> Whenever you get instructions to use the terminal, please avoid them.Umm, no. That is actually bad advice if you want to learn and understand what you are doing.

Anyone who wants to learn to use something new will have to realize that the thing they are learning may already have established methods for doing things that work very well. These methods will seem foreign and difficult at first, but with just a little bit of time and practice, they will enable to user to be far more adept than enabling people to avoid adapting.

I understand your point of view, but I politely and wholeheartedly disagree. Teaching someone to overcome their fear of the terminal is a kind and useful thing to do. The CLI is often faster, and things learned in the CLI will continue to be valuable knowledge regardless of whether a user ends up keeping a default installation using GNOME or decides to switch to KDE or XFCE or IceWM or any of the numerous other GUIs available for Linux.

A person who understands what he is trying to accomplish behind the scenes will be able to figure out the graphic interface with a little time, even if they change which one they use. A person who is trained only in one GUI method will be crippled when (not if) that method ends up being changed in an update. CLI commands almost never change.

Oh, and you are free to discuss Automatix, and even recommend it if you like, although I think it will benefit users far more to learn better methods of accomplishing their goals. Here is the [official forums statement]("http://ubuntuforums.org/announcement.php?f=13") on this sort of thing.

---

### Post by hyper_ch on 2007-05-09
I'd also advice against using automatix... it may be more confortable at first but you don't know the effects it has on the system... in the past automatix used to break the system quite often...

---

### Post by RichPicker on 2007-05-09
I'm not afraid of the terminal. I'm afraid of Ubuntu. I followed the terminal instructions posted here, and from launchpad, and got ZERO results. If Automatix works, I will use it. I've been running Ububnt since January, and have never had so many problems with any operating system. And when such statements as this are made, we are scolded and warned not to criticized the sacred cow of volunteer Ubuntu. I don't want to learn ANYTHING. I just want to use my laptop to send email, record music, watch movies, burn CDs, etc. But that is seemingly impossible here. 

Is that your mission? To TEACH people? Maybe you could spend your time more wisely removing the bugs from Ubuntu. I've been patient, and offered to others what I've learned here whenever I could, and shown appropriate community behavior, but your statement about TEACHING me pisses me off. Why don't you focus on TEACHING yourself.

You don't need to blame Automatix for Ubuntu problems. Ubuntu has plenty of it's own.

Mathew, your comments were arrogant, NOT  helpful.

---

### Post by hyper_ch on 2007-05-09
What problems does Ubuntu have?
And what bugs are you referring to?

---

### Post by RichPicker on 2007-05-09
Just check the forum pages and see how many laptop users don't have use of their microphone. Watch and see them post again and again and again, day after day after day, all the while knowing it's a Feisty bug that's still being worked on. That's one. 

The web camera crashes. It has never worked correctly with Ubuntu. That's two. 

The CD burner doesn't work. That's three. 

All of these worked perfectly with XP. But not with Ubuntu. My mic worked with Edgy for about three weeks (grateful for those three weeks). But no more. It's a bug that's being worked on. It is a low priority. I understand that. I appreciate the efforts of the developers.

Being part of a community where the OS is maintained by volunteers is an incredible, viable alternative to the other operating systems available today. And a unique, positive environment for developing community and communication. But on this laptop, Ubuntu does NOT work. On other configurations of desktops, maybe. But for my laptop, Ubuntu simply does not work correctly. The BAD part about that, and the WRONG part about that is nowhere is that stated. We were not warned before switching to Ubuntu. We are told in the verbage how wonderful Ubuntu is.

You are probably wondering why I continue to hammer away at this to try to get it to work. Because I believe open system is a worthwhile effort. We should all help each other, not scold or condescend each other.

Sheesh. Take a pill dudes.

---

### Post by hyper_ch on 2007-05-09
Why didn't you test it out with the LiveCD? And Ubuntu has a hardware compatibility list... you could check there...

And I'm not experiencing any of your problems... webcam works... microphone (in the webcam) works, cd/dvd-burner works....

---

### Post by dangerousnerd on 2007-05-09
I agree with Matthew.  Good terminal skills are indespensible in the present state of the Linux desktop.  Unfortunately, this is one of the major reasons that Linux is not ready for widespread desktop use.  Using the terminal can allow you to surgically troubleshoot, repair and upgrade your linux box in a much more percise way than the gui allows.  Until the time comes when the hardware compatibility is as high as Microsoft's compatibility, Linux users will have to roll up their sleaves and get into the terminal.  Programs like Automatix are attempting to make things easier, but often they end up messing up the user's system.  All the things that Automatix does, one can do using the CLI (or even Synaptic for some) with much much better results.  

Just my 2 cents. :)

---

### Post by matthew on 2007-05-09
> **RichPicker said:**
> I don't want to learn ANYTHING.I believe you.

If you want to make your Ubuntu installation play dvds and play movies or other media files using non-free formats, you will have to learn something, though. Sorry.

Here's one way to do it. 
-In Feisty, using the default GNOME desktop, open the Applications->Add/Remove... menu. 
-At the bottom left, click Preferences. Enter your password when prompted.
-In the new "Software Sources" dialog box, select the "Ubuntu Software" tab. Then mark the box to enable "Software restricted by copyright or legal issues".  Click "Close"
-Then, back in the Add/Remove dialog, at the upper right of the window, select Show: All Available Applications.
-In the pane on the left, select All.
-In the pane on the right, scroll down and select "Ubuntu restricted extras" and click "OK" to install them.

Or, you could open a terminal at Applications->Accessories->Terminal and type
```
sudo gedit /etc/apt/sources.list
```and replace whatever is there with this```
deb http://archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse

# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse
```
Click "Save" and close gedit. Then, back in the terminal, type
```
sudo apt-get install ubuntu-restricted-extras
```I'll let you decide which is easier.

---

### Post by RichPicker on 2007-05-10
Thank you, sincerely. I followed the instructions about the Ubuntu-Restricted from this link
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
And got errors about this and that, which led me here and there. Then I entered the terminal commands, until I got them right. But still the players didn't work. Then Automatix was suggested. I tried it and it works. All the players work now.

I used Ubuntu in Europe on a few desktop systems, and it worked flawlessly on all of them. That's why I installed in on this laptop. Little did I know, I would have this many problems with it. I've been using since January, and have followed everyone's instructions, but have never had all the components working.

I admit my mistake, I made a mistake installing  Ubuntu. This little computer worked perfectly before installing Ubuntu. 

If the microphone bug isn't fixed, it does nothing for you or anyone else to 'teach'. And all this typing is wasted, because Ubuntu won't work on this laptop anyway.

---

### Post by RichPicker on 2007-05-11
I really feel stupid. I need to apologize to everyone for my inability.
The mic works perfectly now.

Instead of addiing this to the alsa-base file:  ". . . =ref"  (= character)

I added this:  ". . . -ref"  (- character)

How lame. Thank you everyone for your help.

---

### Post by matthew on 2007-05-11
I pleased to hear it all worked out in the end. Congratulations.

---

