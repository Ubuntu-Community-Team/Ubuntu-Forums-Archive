---
title: "[SOLVED] looking for a paid coach to help me"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by 888mafia on 2008-03-16
is there 7.1 server is there a screen shot to show me if im looking at the right thing ?

Because after i in stalled and ran it it loads with text and ends with asking me to log in i do that and it gives me my new login info :example (mynetwork@mynetwork1:~$ ) this is where im stuck i thought there would be some sort of template to follow . 

if there is a walk through this would you point me in the right direction? 
I hate to say it but please KEEP it simple because i have no clue of what im doing im willing to pay a coach to coach me through this

So if you have the knowledge and patience  i will pay for your time

---

### Post by handydan918 on 2008-03-16
Tell ya what, I bet you could use the regular Ubu version. It is capable of all the server functionality of the server version. That's the nature of linux in general. You can install any package you may need to provide the server functionality required, and you can have a gui, too. 
For that matter, you might just try installing a gui on your server rig.

---

### Post by 888mafia on 2008-03-16
> **handydan918 said:**
> Tell ya what, I bet you could use the regular Ubu version. It is capable of all the server functionality of the server version. That's the nature of linux in general. You can install any package you may need to provide the server functionality required, and you can have a gui, too. 
For that matter, you might just try installing a gui on your server rig.
i dont know what a gui is this is y I need a coach
i will search around to see if i can figure out what your talking about

---

### Post by ghost_ryder35 on 2008-03-16
something along the lines of
sudo apt-get install gnome

---

### Post by 888mafia on 2008-03-16
ill try anything because i have a clean computer sitting here that i dont know how to use

---

### Post by durand on 2008-03-16
try sudo apt-get install ubuntu-desktop

---

### Post by ghost_ryder35 on 2008-03-16
you could also install KDE, which is probally 
sudo apt-get install kde

---

### Post by handydan918 on 2008-03-16
> **888mafia said:**
> i dont know what a gui is this is y I need a coach
i will search around to see if i can figure out what your talking about

Sorry, gui = Graphical User Interface
As noted, Gnome is on option. Probably the best one.

---

### Post by 888mafia on 2008-03-16
> **ghost_ryder35 said:**
> something along the lines of
sudo apt-get install gnome

command not found

---

### Post by MasterJS on 2008-03-16
Or since your trying to make a server, it probably be ideal to have a GUI (Graphical User Interface) that would take up less resources, would be to install the Xubuntu desktop. ```
sudo apt-get install xubuntu-desktop
```

---

### Post by rug77 on 2008-03-16
> **888mafia said:**
> i dont know what a gui is 

Simple.  GUI - Graphical User Interface.  It's the pretty windows way of working instead of the CLI (Command Line Interface) way that the server edition works.

The sudo apt-get install gnome that was suggested simply installs a graphical system on top of the command line interface that you have at the moment.

Basically, the system is controlled by a load of configuration files, and these can be changed by editing the text files directly, or by using a pretty graphical representation, which is just upating the files behind the scenes.

Don't panic.

Any questions, post here and you'll be helped for free...

It's like all things computer related - you don't know the way things work until you do !

Once you've done something once or twice you'll wonder why you were fazed by it in the first place.

So take it easy, and welcome to a world where people will help you, just because they can.

Rug

EDIT :  Wow, you try to help someone and dozens of replies get there first.  If anything it proves my point about people trying to help you ...

---

### Post by 888mafia on 2008-03-16
i spelt wrong so i tried again and something is going on ill let you all know if it works beer is on me

---

### Post by 888mafia on 2008-03-16
its flying a mile a min and i excited about whats happening it says rebuilding data base you guy rock it has taken me 3 weeks to get this close was about to give up today i thought i would give it one more try
thank you

---

### Post by ghost_ryder35 on 2008-03-16
when it is done issue
```
startx
```

---

### Post by 888mafia on 2008-03-16
> **ghost_ryder35 said:**
> when it is done issue
```
startx
```
errno 3 no such prosess

---

### Post by rug77 on 2008-03-16
Ctl + Alt + Backspace will restart the Gui Too.

---

### Post by ghost_ryder35 on 2008-03-16
> **rug77 said:**
> Ctl + Alt + Backspace will restart the Gui Too.

and or resart the computer 
it might be
```
start x
```
but I am pretty sure it is
```
startx
```

---

### Post by tgalati4 on 2008-03-16
I think the problem is that the OP (original poster) has installed the server edition of Ubuntu and he is presented with a command line.

A better option would be to install the Ubuntu desktop edition.  That provides almost everything you need.  You can either download it and burn a new CD or request one for free online.  It will arrive in a few weeks.

You can add stuff to your server addition, but you will constantly be missing pieces.  It's actually a good way to learn Linux, but it can be frustrating for new users.

Oh, keep your greenbacks.  You will be asked to help others in due time.

In the meantime, we could use some info.  Post the output of:

>lspci -v

Since you are probably accessing the forums from another machine, use:

>lspci -v > mymachine.txt

Then copy that file to a USB flash drive:

cp mymachine.txt /media/sdc

To find out what your USB device is actually called:

>df -h

---

### Post by 888mafia on 2008-03-16
```
Faild to start the x server (your graphical interface.) it is likelyit is not ste up correctley would you like to view the x server  
```
i chose yes and i got 

```
/etc/gdm/failsafexserver: line 47: [:too many arguments
Warning: could not retrive EDID because grt-edid is not installed 
Warning: could not retrive: PCI IDs discover not installed
dose not know how to config 10
shared/default-x-server dosent exisit xserver could not generate /etc/x11/xorg.conf.failsafe for vesa driver

```
????????????? lol
now im realy lost:lolflag:

---

### Post by ugm6hr on 2008-03-16
I would recommend you start again.

What are you trying to do with your computer?

Who installed Ubuntu 7.10 Server for you (and why the Server edition?)

It seems to me if it has taken you 3 weeks to get this far, then you have not been asking the right questions.

---

### Post by 888mafia on 2008-03-16
I believe your right it is hard to ask the right questions when i dont know how to ask it  ill try to start from the beginning.
i own a a poker forum  i wanted to start a radio station for my site to do a talk show 3 times a week i dont remember who told me but it was said that i should have my own server to do this. My host dose not support it and the hosts i checked were too expensive so i asked  can i take one of my other computers and make it a server to stream audio and was lead here 
and here we are lol

---

### Post by ugm6hr on 2008-03-16
OK.

I'm afraid I can't help you.

And you might have more luck if you post a specific question here:
[http://ubuntuforums.org/forumdisplay.php?f=7](http://ubuntuforums.org/forumdisplay.php?f=7)

Make sure you include lots of detail about your hardware.

---

### Post by 888mafia on 2008-03-16
> **ugm6hr said:**
> I would recommend you start again.

What are you trying to do with your computer?

Who installed Ubuntu 7.10 Server for you (and why the Server edition?)

It seems to me if it has taken you 3 weeks to get this far, then you have not been asking the right questions.
Did i or should i install a different software ?  and if so which one ? and can i use it as a audio server?

---

### Post by 888mafia on 2008-03-16
> **ugm6hr said:**
> OK.

I'm afraid I can't help you.

And you might have more luck if you post a specific question here:
[http://ubuntuforums.org/forumdisplay.php?f=7](http://ubuntuforums.org/forumdisplay.php?f=7)

Make sure you include lots of detail about your hardware.
This is y i am willing to pay for someone who knows what they are doing to spend the time to help me get it right 
This is something that i think will be so beneficial to me once i got it up and running  if i could learn the basics .
so the offer still stands

---

### Post by handydan918 on 2008-03-18
OK, I know a guy who administers Debian systems remotely nationwide. Try to contact him at [http://www.actusa.net/]("http://www.actusa.net/")

---

### Post by Arthur Archnix on 2008-03-18
[http://www.ubuntu.com/support/paid](http://www.ubuntu.com/support/paid)

---

### Post by steveneddy on 2008-03-18
To start the** G**raphical **U**ser** I**nterface, use this command

(I assume you installed Gnome Desktop)

```

sudo /etc/init.d/gdm start

```

and to stop the **GUI**, do this

```

sudo /etc/init.d/gdm stop

```

to get to a command line, if you hit the Ctrl + Alt + F1 keys, it will get you to what is called the tty screen.

**Servers don't usually use a GUI because it takes up valuable resources from the PC.**

This is why you need to learn to run in the text/terminal mode, or get used to turning yout GUI on and off, which is what I do.

Three links for you to study:

[http://www.oreillynet.com/linux/cmd/](http://www.oreillynet.com/linux/cmd/)

[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

[http://www.computerhope.com/unix.htm](http://www.computerhope.com/unix.htm)

---

