---
title: "Please Help"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by RichPicker on 2007-01-19
I am new to linux and ubuntu. I have posted the problems with my mic and my trackpad. I have received good, gratious help from several of you. (thank you) But I DO NOT understand the commands of linx in the terminal. I can type, yes. But I need, please. very simple step-by-step instructions on how to perform the fixes that some of you have already done.

I apologize for being so ignorant. I apologize if I vent my frustrations to any of you who are so helpful and kind. 

If you can help me with these problems, I will appreciate it.

Both these problems are described in the 'no mic' post. There are other posts that have solutions that other folks have used. I have read those solutions, but do not understand how to do them on this computer. 

Thanks,
R-

---

### Post by bodhi.zazen on 2007-01-19
Here is an overview of commands;

[http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

Where are you getting tripped up ?

---

### Post by smile_sunshine on 2007-01-19
Ok 
for the mic fix instructions:

1. open a terminal screen - see [here]("http://www.psychocats.net/ubuntu/terminal") if you need instructions how to do that 

> How do I "backup existing /etc/modprobe.d/alsa-base"  

type: > sudo cp /etc/modprobe.d/alsa-base.backup

since you used sudo, it will ask you for a password, this is the same one you use to log in with

this will make a copy of the file called alsa-base.backup  which you can easily copy back if something goes wrong with the changes you make

---

### Post by smile_sunshine on 2007-01-19
mic instructions (continued)

to > 2. append the following to the end of the file:

options snd-hda-intel model=ref 

you need to type (again in the terminal)
> gksudo gedit /etc/modprobe.d/alsa-base.backup

this will open the file for you in a text editor (sort of like notepad in windows) 

then add 
 >  options snd-hda-intel model=ref  to the end of the file , save it and close it, then you just have to reboot as it says in the instructions.

hope that helps :) feel free to post if its still confusing

---

### Post by smile_sunshine on 2007-01-19
i cant find the instructions you are following for fixing your mouse if you could post a link I'll try and explain them in more detail as well?
EDIT: found them :)

when you turn on your computer do you get a screen which gives you options like: 
 > 
Ubuntu, kernel 2.6.15-26-386
Ubuntu, kernel 2.6.15-26-386 (recovery mode)
Ubuntu, memtest86+
etc ? 

if so, thats grub. If not, i'm not sure what you should do then.

---

### Post by RichPicker on 2007-01-19
These are the results:

rich@rich-laptop:~$ sudo cp /etc/modprobe.d/alsa-base.backup
cp: missing destination file operand after `/etc/modprobe.d/alsa-base.backup'
Try `cp --help' for more information.
rich@rich-laptop:~$

---

### Post by RichPicker on 2007-01-19
Thanks for you help. I've been at this for four days, and still this piece of crap ubuntu work. It is neither stable NOR free. It has cost me toooo many hours wasted trying to get it to run. Good luck to all of you. I'm going to use Mandriva or another that is reliable. This is a rip-off.

---

### Post by jvc26 on 2007-01-19
What is a rip off? Its free???

I think there was a missing stanza in the command:
```

sudo cp /etc/modprobe.d/alsa-base /etc/modprobe.d/alsa-vase.backup

```

That will back up your file (I'm just correcting bits from the other's instructions above)

Then to append the bit go to:

```

gksudo gedit /etc/modprobe.d/alsa-base

```

Which will open a window with the alsa-base file in it ready for you to edit. Then append your line (copy it to the bottom of the file) and click the save button.
```

options snd-hda-intel model=ref

```

Apologies if thats not exactly it I'm not sure of the thing you were originally following, but the instructions above look very wrong to me:
1/ They were not making a backup, trying to copy a file that didnt exist.
2/ They were opening the backup file which didnt exist to make the new line rather than appending it to the real file
3/ I hope that helps, I've just tried correcting what I saw above.

Ubuntu is remarkably stable, as most people will say (unless you are doing things like using alpha software etc) which tends to ask for trouble ;) Is this your only problem? Can you detail it out as I'm not sure exactly what you're after - the above command is how to copy that file to a backup version.
Il

---

### Post by RichPicker on 2007-01-21
Yup. There was some text missing from those commands.

I did that fix, and now the mic works. But there are other sound problems. And I'm working with someone about the touchpad problems. I need to work with that one person. I dare not type anything into the terminal window unless I know it's correct. I don't know enough about linux to recognize if I've typed something wrong. 

It's not free, because it requires, not hours, but DAYS, of my time to get it to work. Maybe it's this type of Dell laptop? I don't  know. I have heard for years that linux is great. The people who told me that were telling the truth. But now that I have taken the plunge, WOW. It is EXTREMELY difficult and FULL of problems. That's not an opinion, it's a fact. 

The sound doesn't work, the touchpad doesn't work. the movie players won't play movies. much of the software doesn't work. I am soon in my  second week of trying to get these problems fixed. That does NOT fit ANY definition of stable or free.

I'm continuing to work on it, and hoping that by solving the problems with this laptop, others with similar problems will be helped.

Thanks to all of you for your help.

---

### Post by jvc26 on 2007-01-21
They wont play movies because it is free. Movies are protected by proprietary codecs which as Ubuntu is free, they wont distribute with the distro. Therefore you have to install them yourself - the same with .mp3 codecs and the like.
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs)
Much of the software doesnt work? Whats not working? It may well be that something is just missing perhaps? I'm sure by clarifying these problems you can be helped through this. Its a shame its taking you so much time to get everything sorted, once it is its definitely worth it. It may be due to your lappy that you're having such a hard time, they can be quite a bit of work from what I've heard.
Il

---

### Post by Shatrat on 2007-01-21
Whats with these CARS!
People keep telling me I can't live without one but I get into one and I have to have KEYS?
How do I make keys? Someone please give me simple instructions because I am too scared to experiment and too lazy to read.
Also I read somewhere that to drive it I have to go to the DMV?
This really isnt worth it, I don't see this whole 'automobile' thing catching on.

---

### Post by RichPicker on 2007-01-24
I was running 6.06 Dapper. I did all the recommendations from this group, and others from a helper at launchpad.net.

It got the mic to work. and the mouse to work 'better' but there were other problems. (Audacity still crashed, etc.) The launchpad.net person suggested I upgrade to 6.10 Edgy.

I did that, and am now running Edgy. The same problems exist. I repeated the previous fixes, but the mic still does not work. The mouse is not as bad as before, but still not right. 

Audacity crashes when I open it. Sometimes Sound Recorder locks up and I have to force quit. When Sound Recorder does work, and I try recording, I hear hiss or hum only.

Dependency problems? Driver problem? I don't know enough about linux or Edgy to proceed unaided.

Your suggestions?

---

### Post by RichPicker on 2007-01-24
Sorry. I keep saying mouse, but I mean touchpad.:guitar:

---

### Post by RichPicker on 2007-01-24
Additionally: With Dapper, Totem Movie player never worked on this machine, though I downloaded all the necessary codecs, etc. I used Kaffeine to play the movies. But now with Edgy, Totem still doesn' work, and Kaffeine doesn't work either.

---

### Post by RichPicker on 2007-01-24
Moer info:

I just installed GXINE and it works well. And, the audio adjustments and graphic equalizer work well. So, this means some part of the sound card is working well, but not the mcrophone?

---

