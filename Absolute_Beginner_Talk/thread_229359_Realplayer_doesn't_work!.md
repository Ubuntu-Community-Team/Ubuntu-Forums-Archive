---
title: "Realplayer doesn't work!"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by Mikawa Ossan on 2006-08-04
I don't know if this is the right place for this, but I have a feeling that this will turn  out to be a stupid question.

I am trying to get RealPlayer to work on my computer.  I first searched for a DEB build for it, but for some reason I couldn't find one.  So instead I downloaded a RedHat build and converted it using Alien.  I proceeded to install it, but I can't get it to work.

Ok, so next I saw a thread about using Automatix to install Realplayer, so I did that as written.  I didn't uninstall the redhat build, because I didn't know what to type at the command line; I basically just hoped that Automatix would install over my readhat build.

Well, I still can't get Realplayer to work, so I'm stuck.  Please help me!

---

### Post by Titus A Duxass on 2006-08-04
I would uninstall the RH RealPlayer and then run Automatix.
It may be having problems because the latest standard of Realplayer is already installed.

---

### Post by Mikawa Ossan on 2006-08-04
I tried this.  I typed the command:  sudo dpkg -r realplayer

It said it removed realplayer, so I tried to install it again using Automatix, but Automatix said that the newest version of Realplayer was already installed.

As it stands, I can not find any icons for realplayer, and I have no idea of what to type in the terminal to make it run.  I suppose if I could solve either of those issues, I would be happy.

---

### Post by Metacarpal on 2006-08-04
Try installing the Helix player from your add/remove programs.  The new RealPlayer for Linux is basically just the Helix player with a different GUI.

---

### Post by Mikawa Ossan on 2006-08-04
I also just tried the following:

1)  At the command prompt, I typed "re" and then hit TAB twice.  Nothing resembling a realplayer command showed up except for realvncpasswd and realvncpasswd.real

2)  Again at the command prompt I typed "sudo apt-get remove realplayer" and "sudo apt-get remove --purge realplayer"  Both times it said that realplayer wasn't installed so there was nothing to remove.

---

### Post by kadymae on 2006-08-04
Just to double check, are you using an Apple with a G series processor in it?

Because, if so, Real Player is X86 only.

---

### Post by cantormath on 2006-08-04
> **Titus A Duxass said:**
> I would uninstall the RH RealPlayer and then run Automatix.
It may be having problems because the latest standard of Realplayer is already installed.

I second that TITUS, use automatix.

remember that if you are on kubuntu, you use a different automatix
(X)ubuntu
[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)
kubuntu
[http://www.ubuntuforums.org/showthread.php?t=203294](http://www.ubuntuforums.org/showthread.php?t=203294)

---

### Post by Mikawa Ossan on 2006-08-04
No, I'm not using a Mac; it's a Pentium 4.

I tried installing Helix, but I got an error message, so that's no good either.  The error message is all in Japanese (I'm using the Japanese version of Ubuntu), so I can translate it if you want, but part of it says that it was trying to overwrite E: /var/cache/apt/archives/helix-player_1.0.6-3_i386.deb: `/usr/share/locale/de/LC_MESSAGES/libgtkhx.mo' which "is contained in Realplayer...

I tried uninstalling my other version of Realplayer, but for some reason, Automatix still thinks that it's installed.

EDIT:  I am using Ubuntu, and not Xubuntu or Kubuntu or Edubuntu or any of those.  But like I said it's the Japanese version.

---

### Post by Titus A Duxass on 2006-08-04
There is probably some command to force the remove and purge all the data.  But I have no idea how this is done, when faced with something like this as a newcomer I used to do a quick reinstall.

Edit: try running aptitude remove realplayer

---

### Post by Mikawa Ossan on 2006-08-04
> **Titus A Duxass said:**
> There is probably some command to force the remove and purge all the data.  But I have no idea how this is done, when faced with something like this as a newcomer I used to do a quick reinstall.

Edit: try running aptitude remove realplayer

1)  &#12497;&#12483;&#12465;&#12540;&#12472;&#12522;&#12473;&#12488;&#12434;&#35501;&#12415;&#36796;&#12435;&#12391;&#12356;&#12414;&#12377;... &#23436;&#20102;
2)  &#20381;&#23384;&#38306;&#20418;&#12484;&#12522;&#12540;&#12434;&#20316;&#25104;&#12375;&#12390;&#12356;&#12414;&#12377;... &#23436;&#20102;
3)  Initializing package states... &#23436;&#20102;
4)  Building tag database... &#23436;&#20102;
5)  E: &#12525;&#12483;&#12463;&#12501;&#12449;&#12452;&#12523; /var/lib/dpkg/lock &#12434;&#12458;&#12540;&#12503;&#12531;&#12391;&#12365;&#12414;&#12379;&#12435; - open (13 &#35377;&#21487;&#12364;&#12354;&#12426; &#12414;&#12379;&#12435;)
6)  E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I tried running aptitude remove realplayer, and I got the above message.  Translation follows:

1)  Reading the package list...  done
2)  Constructing dependency(?) tree ... done
3)  Initializing package states... done
4)  Building tag database... done
5)  Cannot open E: lockfile /var/lib/dpkg/lock (13 No permission)
6)  E:  Unable to lock the administration directory (/varlib/dpkg/).  are you root?

I'll try again using sudo this time.

---

### Post by Mikawa Ossan on 2006-08-04
Tried it again with sudo and got the following message:

The following packages are BROKEN:
  mozilla-helix-player
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  mozilla-helix-player: &#20381;&#23384;: helix-player (= 1.0.6-3) but it is not installableResolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
helix-player [1.0.6-3 (dapper)]

Score is -19

Accept this solution? [Y/n/q/?] y
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  helix-player

Do you want to ignore this warning and proceed anyway?


Shall I say yes?

---

### Post by Metacarpal on 2006-08-04
[Removal of softwares installed by automatix]("http://www.ubuntuforums.org/showthread.php?t=90797")

---

### Post by Metacarpal on 2006-08-04
> **Mikawa Ossan said:**
> Tried it again with sudo and got the following message:

The following packages are BROKEN:
  mozilla-helix-player
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  mozilla-helix-player: &#20381;&#23384;: helix-player (= 1.0.6-3) but it is not installableResolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
helix-player [1.0.6-3 (dapper)]

Score is -19

Accept this solution? [Y/n/q/?] y
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  helix-player

Do you want to ignore this warning and proceed anyway?


Shall I say yes?

Don't worry about that message.  It's okay to say yes.

---

### Post by cantormath on 2006-08-04
> **Mikawa Ossan said:**
> No, I'm not using a Mac; it's a Pentium 4.

I tried installing Helix, but I got an error message, so that's no good either.  The error message is all in Japanese (I'm using the Japanese version of Ubuntu), so I can translate it if you want, but part of it says that it was trying to overwrite E: /var/cache/apt/archives/helix-player_1.0.6-3_i386.deb: `/usr/share/locale/de/LC_MESSAGES/libgtkhx.mo' which "is contained in Realplayer...

I tried uninstalling my other version of Realplayer, but for some reason, Automatix still thinks that it's installed.

EDIT:  I am using Ubuntu, and not Xubuntu or Kubuntu or Edubuntu or any of those.  But like I said it's the Japanese version.

what happens when you type:
:~$ sudo apt-get remove realplay
?

---

### Post by Titus A Duxass on 2006-08-04
I would definately say yes and proceed with the removal.
If it is successful follow the removal process for automatix software (Metacarpal provided a link).

After that I would do an aptitude update and upgrade (probably followed with aptitude dist-upgrade) then you should be clear to run Automatix.

---

### Post by Mikawa Ossan on 2006-08-04
OK, starting in order from post #12.

#12
I looked at that thread but I didn't see specifically for realplayer.  However, I quickly noticed a pattern and typed "sudo apt-get remove realplayer".  It said that Realplayer is not installed.

#13
I did type yes.  There was an error, though, when reading dpkg: /var/cache/apt/archives/helix-player_1.0.6-3_i386.deb

In other words, it didn't install.

#14
I tried, and it said nothing whatsoever about realplayer.  It did give me an error message about helix.  An error message I ahve encountered on my own, too,k and I tried to fix it, but nothing happened.

#15
I'll try that.

---

### Post by Mikawa Ossan on 2006-08-04
> **Titus A Duxass said:**
> I would definately say yes and proceed with the removal.
If it is successful follow the removal process for automatix software (Metacarpal provided a link).

After that I would do an aptitude update and upgrade (probably followed with aptitude dist-upgrade) then you should be clear to run Automatix.

No dice.

I'm not adverse to reinstalling Ubuntu and trying all over again from scratch.  I kind of want to give Ubuntu a larger partition anyway.  Maybe I should try this?

---

### Post by Metacarpal on 2006-08-04
I recently did a reinstall so I could resize my partitions.  I gave the main Ubuntu partition (/) about 6GB, and am using the rest for /home and the swap file.

---

### Post by Mikawa Ossan on 2006-08-04
Thanks for the help.  I think I'll reinstall tomorrow.  It's getting pretty late here (2am).  Good night!

---

### Post by Metacarpal on 2006-08-04
Sleep well, and best of luck!

---

### Post by cantormath on 2006-08-04
> **Mikawa Ossan said:**
> No dice.

I'm not adverse to reinstalling Ubuntu and trying all over again from scratch.  I kind of want to give Ubuntu a larger partition anyway.  Maybe I should try this?

thats a little over kill.

---

### Post by Mikawa Ossan on 2006-08-04
Overkill?  Maybe, but I honestly was thinking of reinstalling anyway to make a larger partition for Ubuntu.  I whad it in my mind that I would learn how to do things with this installation so that I could do it perfectly the next time around.  I'll let you know if I continue to have problems.  Thanks again!

---

### Post by vladozan on 2006-08-07
I have installed RealPlayer using Automatix. I can run the applicaion but i  hear no sound. I have no problem with a sound card, because i can play music in e.g. Totem.

---

