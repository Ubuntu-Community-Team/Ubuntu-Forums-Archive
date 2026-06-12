---
title: "argggh! how do I get rid of Ubuntu?"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by weemikey on 2006-05-24
Well, I've tried and tried.
Ubuntu reads both my cd drives, but not dvds.  Will write .jpgs and .doc files, but not to the same disc with CD Creator.
Read my wife's digital camera images just fine and d/ls them to computer.
[COLOR="Red"]BUT[/COLOR] there is no way it will let me be /root.  It will NOT d/l any updates (even tho' it tells me there are e147 of them), no access to repositories (suppositories?) on the install cd or online.  If I d/l a programme, ie Mozilla Suite to replace Firefox, there is no way I can install it -'you do not have permissions'.
By the way I only have 640 permissions in my .dmrc file, checked that one.
I really can see that this is the way to go, but what a hard road to drive - worse than the Dempster Highway by far!
And for this I completely formatted my h/d (after saving my data to cd-rw, no red face there!).
So.... what do I do?  Can I uninstall Ubuntu and re-install Windows xp pro on a wiped h/d?  Should I take all the help I can get and persevere with Ubuntu? or return to the Stone Age, dump my computer altogether (a Dell Dimension 2400 with a replacement m/board by Via as the old one totalled), and renew my library card?
HELP< HELP.[http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)
wee mikey

---

### Post by an.echte.trilingue on 2006-05-24
Just put your windows XP disk in the drive and let 'er rip.  They should both wipe your HD and reinstall windows.

You would have had a more positive experience if you had read this:

[https://wiki.ubuntu.com/FindPage?action=fullsearch&titlesearch=1&value=help](https://wiki.ubuntu.com/FindPage?action=fullsearch&titlesearch=1&value=help)

---

### Post by bruce89 on 2006-05-24
You should **never** use root, you should always do things with sudo.

---

### Post by IYY on 2006-05-24
You're having several problems here, let's start with your problem with the root account:

The root user is restricted in Ubuntu. You can't login as root, or be root. All you can do is run commands or programs "as root". This is done using sudo (or gksudo for graphical programs). So, if you want to run the program synaptic as root from the terminal, you'd type **gksudo synaptic**, and then enter your password. You don't need to do this to launch synaptic though, because it's already configured to ask for the password when you select it from the menu.

Now for software installation:

What exactly is the problem that's reported when you try to install something from Synaptic? Or is there an error message when you launch synaptic?

About uninstalling Ubuntu:

I'd suggest trying to fix your problems first. I don't think they are severe. However, if it turns out that you have to re-install Windows, it's as simple as popping the Windows CD in the drive and installing. It will format the drive all by itself.

---

### Post by aysiu on 2006-05-24
Reinstall Windows and get a Ubuntu live CD.

Play with the live CD for two weeks--get to know it slowly without panicking. Ask questions here as they come up.

If, after two weeks, you think it's something worth exploring more, set up a dual-boot with Windows.

---

### Post by youthforlinux on 2006-05-26
[QUOTE=IYY]You're having several problems here, let's start with your problem with the root account:

The root user is restricted in Ubuntu. You can't login as root, or be root. All you can do is run commands or programs "as root". This is done using sudo (or gksudo for graphical programs). So, if you want to run the program synaptic as root from the terminal, you'd type **gksudo synaptic**, and then enter your password. You don't need to do this to launch synaptic though, because it's already configured to ask for the password when you select it from the menu.

Now for software installation:

What exactly is the problem that's reported when you try to install something from Synaptic? Or is there an error message when you launch synaptic?

About uninstalling Ubuntu:

I'd suggest trying to fix your problems first. I don't think they are severe. However, if it turns out that you have to re-install Windows, it's as simple as popping the Windows CD in the drive and installing. It will format the drive all by itself.[/QUOTE]

i thought u can log in as root though i dont do it cuz its bad and in there is no need to do this but if u enter this then u can log in as root i think
> sudo passwd root

---

### Post by bruce89 on 2006-05-26
That will make things even worse.

---

### Post by youthforlinux on 2006-05-26
[QUOTE=bruce89]That will make things even worse.[/QUOTE]

yea i know but i was just wondering if that was the way to be able to login as root
even though i dont do it and its bad and should never be done

---

### Post by bruce89 on 2006-05-26
It's how to set root's password, as Ubuntu makes it a random sequence.

---

### Post by youthforlinux on 2006-05-26
okay just wanted to make sure and to increase my knowledge

---

### Post by feardotcom on 2006-06-14
ok, i was used to suse 9.1, where are you type SU - and not sudo, so i set the root password in ubuntu, i dont see a problem here?

---

### Post by killernurd on 2006-06-20
Actually, SU and sudo are slightly different.

'sudo' is a command that allows you to do something as root. There is a file tucked away in /etc called sudoers - that files contains the parameters for using sudo. Usually, it'll indicate that only root and members of group wheel are allowed to sudo (though root need not sudo :)

As near as I can tell, 'su -' reproduces a root prompt, including environement variable settings, like PATH. I've found that it's usually more worth my time to use 'sudo bash' than 'su -'.

The way that Ubuntu handles the root account is highly intelligent, from my perspective. It allows for an admin-priviledged user to do everything, and puts a wall between the nasties outside and gaining root access. Too, it also prevents *you* from making stupid mistakes inadvertently - you have to deliberately invoke sudo to get stuff done (I will note that this does not stop lusers, who'll just sudo anything and damn the torpedoes).

---

### Post by AirRaven on 2006-06-20
As a side note, you can access a root terminal by either typing [FONT="Courier New"]sudo su[/FONT] or [FONT="Courier New"]sudo -i[/FONT].

---

### Post by jlbjlb on 2006-06-21
I found myself as root user when I booted into recovery mode.  I have just started with Ubuntu, but in the 1990s I looked after SCO Unix servers, so knew about VI !.  Fortunately, I have to hand O'Rileys Linux in a Nutshell -- saved the day.!  I had been messing around with /etc/X11/xorg.conf trying to increase my screen resolution.

Incidentally, I had no problems with installing from CD and now have dual boot with XP PRofessional.  Needless to say, I have been with Ubuntu 99% of the time.

---

### Post by anpan on 2006-06-22
Your solution to uninstall ubuntu seems simple with Windows XP, but I have Windows 98.  How can I uninstall ubuntu? 

Thanks.

---

