---
title: "Ubuntu failing to compensate for my poor memory!"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by MysteryShopper on 2006-12-28
First post: be gentle!

I have Ubuntu 6.06 (Dapper Drake) installed as the only OS on a cute small-format factor PC which now needs to be redeployed so that it can be used for three things only: playing music, playing movies (in Mpeg2 or Mpeg 4) format, and browsing the web.  All the media resides on a shared Windows drive elsewhere on my home network.  The solution I adopt needs to be completely intuitive and graphical or my wife won't use it, and I am in two minds about whether to revert to the more familiar XP or not.  Either way, I have a couple of problems which are driving me absolutely crazy...

1.  I can't recall the user name and password I gave when I installed Ubuntu on this box.  I've just added a new user but this new user account does not have administrative privileges.  I can't therefore do any administration of my system or get at the Synaptic Package Manager, and I also can't seem to do anything to get Ubuntu to recognise my CD drive, which shows up as an icon but gives me a 'mount: special device /dev/hda does not exist' message.

2.  I'm guessing that perhaps because of this, I can't get my system to boot from a CD.  I've changed the boot sequence in the BIOS to try the CD-ROM first, but despite this neither Ubuntu nor Win XP boot disks are picked up.  I really don't mind re-installing either OS from zero.

3.  I can see my Windows shared folders across the network and the media files in them I'd like to play, but neither Media Player nor Rhythmbox will play these directly.  Forgive my ignorance, but is this because these shared folders need to be mounted on my local system (and is this the same as 'mapping' in Windows?)

4.  Once I get these issues resolved, I don't mind which OS I end up with on this box.  I know that must be offensive to Ubuntu fans, but all I need is for it to play media and let my wife browse the web.  I'd almost prefer not to have a desktop at all: anybody know of a good full-screen media-playing GUI which also provides an internet browser?

Thanks in advance for any advice you can send my way on any or all of these points.

---

### Post by sindrum_murdnis on 2006-12-28
The admin password is the same as the user you set up when setting up the system. To do stuff with admin you can use
```

 sudo -i

```
 to log in and work . or simply use 
```
sudo (command)

```
replacing command with what ever your doing. again it will prompt for a password and you use the user password you have set up when installing the system. Hope this helps

---

### Post by deadgobby on 2006-12-28
If you have low memory like less than 256k. I would move to Xubuntu. If you can boost your system ram to at least 256k. You'll be going. Please post your system specs and people will lead you right.

Gobby

---

### Post by agurk on 2006-12-28
1. Ouch. :( You *could* probably break into your system somehow and reset the password or something, but I strongly suspect reinstalling the OS from scratch is the route of least resistance.

2. No. Whatever you would do to mess up the OS, it would not prevent you from booting on a CD.

3. If you're able to see the files, you should be able to play them, **provided** you have installed the necessary codecs. Many of these codecs (such as the common mp3) are non-free and thus not included in the default installation. An alternative to installing a lot of codecs is using VLC as the media player (it has all the good stuff built-in).

4. There is a rumor about Google hacking on an OS like this. I do not know of any existing ones at present.


Hope that helps and good luck!

---

### Post by wpshooter on 2006-12-28
Dear MysteryShopper:

I know I may get hit in the head by a bunch of big rocks or something, but for doing the types of things that it sounds like to me that you are wanting to do, I think M/S Windows is still by far the most user friendly way of doing these things.  All of what you are wanting to do is pretty much pre-built into M/S whereas in Ubuntu/Linux, you still have to do a good bit of **Doctoring** to the system to get it to perform these same functions (and I certainly am not saying that this is necessarily Ubuntu's fault).  And I assure you that it gives me absolutely ZERO pleasure in saying this because I love the concept of Ubuntu but I just don't think it is quite there yet for most users.  I am crossing my fingers and still hoping that in about 2 to 3 years it is going to be there and even surpass M/S in easy of use.  If I were you I would stick with M/S for now to do what you are talking about but yet still keep a machine with Ubuntu on it so you can monitor it's progress much like I and I suspect many other users currently are.

Good luck.

---

### Post by MysteryShopper on 2006-12-28
Thanks for the replies, guys, although I must have expressed myself poorly since none of them gets to the real problem which is that I am unable to get that PC ro read the CD drive in order to re-install an OS from scratch.  I've changed the BIOS settings to boot from a CD first but it completely ignores this.  I am therefore stuck with the Ubuntu user account I've just created which had no admin privileges (although I'll try what sindrum_murdnis suggests).  So I haven't been able to either:
[LIST]
[*]re-install Ubuntu
[*]replace my Ubuntu install with Win XP
[*]download any additional Ubuntu packages
[/LIST]

and that's pretty frustrating since it means I can't do what I want, can't upgrade, uninstall or replace Ubuntu.  I've even considered pulling the HDD out of this system, installing it on another PC and reformatting, but would this make the necessary changes to the MBR or not?

Completely confused now!

By the way, Deadgobby, I have 1GB of RAM in that box: the inadequate memory is all in my own head!

I also tend to agree with you, wpshooter.

---

### Post by riven0 on 2006-12-28
MysteryShopper, are you sure there isn't something wrong with your cd drive? I've got a very old system where my drive just recently went dead and for the longest time I thought there was something wrong with the cd's I was burning.

When you log into Ubuntu, can you try another cd and see if Ubuntu mounts it?

---

### Post by doobit on 2006-12-28
If you don't know your password or your username, there still may be a solution if you have grub, and didn't also password the grub bootloader. Reboot the computer and hit  the Esc key when you see grub start. Then select the second choice in the list, which is recovery mode, and hit enter. This boots you as root. When you are root you are all-powerful to the OS. Navigate to the home directory and type ls which will list the visible files and directories in /home. One of those directories will have the name of your forgotten username. Next type ```
passwd thatforgottenusername newpassword
```
and reboot. Now you have changed the password for your username which you should now remember because you wrote it down, right?

---

### Post by richardward101 on 2006-12-28
Can't help with the CD, sounds like a hardware fault.

There are a few good media centre solutions for Linux. On ubuntu you can install mythtv, just google for it and theres plenty of how to guides (this gives an interface somewhat similar to Windows Media Centre edition.

If you get the drive working then there's a livecd called [Geexbox]("http://geexbox.org/en/index.html") that u may find useful

---

### Post by theoldgit on 2006-12-28
Sounds like your cd player is faulty. If you cant even boot from it then it is not due to the operating system.

as for media players,

 well for music I would use Amarok, you wont find aything in windows that comes anywhere near it. Probably the best music player I have seen. You can mount your windows drive and configur Amarok to play from it seemlessly.

Movie players - you're spoilt for choice

---

### Post by MysteryShopper on 2006-12-28
Thanks, doobit: that enabled me to retrieve my original user name and log in as root.  A step forward at last!

---

