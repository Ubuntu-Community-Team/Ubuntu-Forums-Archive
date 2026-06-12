---
title: "first installation of Ubuntu and Linux please help me now."
date: 2005-11-23
forum: Absolute Beginner Talk
---

### Post by dayobu on 2005-11-23
Hi My name is Dayo, a nigerian.I got the ubuntu install CD from a friend and i installed it on my system and after the installation was complete, i started the system and for more than 1hr i was just seeing a lot of programming stuffs like loading some kinda files or settings and many things i cant remember now.i got so tired of reading them and i got up.Please how can i get this ubuntu to work?i hope u get me?I am just very curious and i want it to work now.please help if u r online now. thanks.

---

### Post by Axeface49 on 2005-11-23
Hi, Dayobu,

Well uhm it sounds like your using a Hoary Hedgehog CD and that screen that you sit infront of for hours is ubuntu finishing the installation.

Maybe some more details about what this screen looks like?

Signed,
Axeface

---

### Post by bluefrog on 2005-11-23
with a slow processor it will take time to finish the installation once you have taken out the cd and rebooted. Just wait and see..
The screen you'are looking at is deselecting, selecting, etc...It's normal.

---

### Post by dayobu on 2005-11-23
Okay, it started like every other linux that says loading kenerl, loading this and that and on the right side of the screen its says ok, ok , ok .Then, i started still on that interface it says reselecting .... and really i cant remember cos i did not pay attention i just though it would boot up fast like windows and i will be able to navigate thru it and know and see what linux is about.Later on it asked me to select the screen resolution i wanted and i selected something 1600x1200, i was given about 15options to choose from, i used the keyboard to select up/down movement.hope u get this now?I really hope so.thanks

---

### Post by aysiu on 2005-11-23
Everything you're describing is normal.
You see text.
You select options.
You get many options because Linux is about choice.

I don't understand what your question is.
If you don't like Ubuntu (which you may not), there are other Linux flavors that are entirely different (Mepis, Linspire, Blag, and SuSE are worth checking out, too).

And if you don't like Linux, you can use Windows.

If you want to try it, try it, but don't complain about it. If you have problems or questions, just ask, and people here will try to help.

---

### Post by dayobu on 2005-11-26
Hello  again all, is there anyway i can change the VGA mode/setting for me to be able to view the GUI in Ubuntu?Because i have just installed it and each time it starts booting my monitor keeps going off and i haveused two monitors.I think its as a result of the VGA settings i put on it.I chose 1600x1200.i guess thats quite much.Well, i hope i am asking some logical questions here.

---

### Post by Brunellus on 2005-11-26
1600x1200 seems rather too much.  can you tell us exactly what kind of hardware you have--be as specific as possible.

---

### Post by dayobu on 2005-11-27
Thanks for the prompt reply.The system i am using have this specs.Pentium MMX and 128MB memory and Hard disk size of 3GG.I guess this is enough to make the software work well.Is there anyway to change the VGA setting?if not, i guess i have to re install it then.

---

### Post by aysiu on 2005-11-27
[QUOTE=dayobu]The system i am using have this specs.Pentium MMX and 128MB memory and Hard disk size of 3GG.I guess this is enough to make the software work well.[/QUOTE] Well? I don't know. My Ubuntu install uses 2.9 GB of its partition. That's a full install with minimal additional applications. 3 GB is really pushing it in terms of hard drive space. And to run Gnome or KDE, 128 MB of memory is going to hurt you. You're probably better off doing a minimal (server) installation with [the xubuntu-desktop package.](https://wiki.ubuntu.com/Xubuntu)

Of course, everything I've talked about has nothing to do with your monitor or screen resolution.

---

### Post by dayobu on 2005-11-28
I am yet to finish with my ubuntu installation.I re-installed the software again, this time following the installation instruction from [https://wiki.ubuntu.com/InstallingXubuntu](https://wiki.ubuntu.com/InstallingXubuntu). I wanted to install it as a server.This time i beleieve i installed it well but i got stuck again when i did not know how to interprete the word "uncomment".i guess its a programming term.The installation went well and so was the system booting up process.i just did not know how to "Uncomment the universe repository line (search for universe and uncomment that line". I got the lines but i could not go further.later on i ignored the instruction after re-booting again i just wanted to see the beautiful ubuntu desktop and start browsing through its features so i ran the command "sudo apt-get update" and then also "sudo apt-get install xubuntu-desktop".But i got the reply that the "couldnt find package xbuntu desktop".I was able to get all this from this link -https://wiki.ubuntu.com/InstallingXubuntu.Hope my explainations are clear enough.please assist me.

---

### Post by aysiu on 2005-11-28
I'm assuming you know where the terminal is, since you were able to *sudo apt-get update*.

If so, follow the instructions in the first link in my signature to get the most up-to-date repositories. Then, ```
sudo apt-get update
sudo apt-get install xubuntu-desktop
```

---

