---
title: "logitech mouse"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by mcnn on 2006-08-12
I am happily using ubuntu since yesterday, but I have two small issues:
1.I can't seem to download Flash Player.not automatically, nor manually.
what am I doing wrong?

2.I am using a logitech corded optical mouse, and it works fine except I can't set the scrool wheel ***button*** to anything( I usually have it set to "go back" for fast web browsing)

logitech has no drivers for linux...can you help..??
thanks

---

### Post by Herman on 2006-08-12
Hello, mcnn, I'll let someone else help you with your first problem, maybe do a search for 'automatix' and run it?
> I am using a logitech corded optical mouse, and it works fine except I can't set the scrool wheel ***button*** to anything( I usually have it set to "go back" for fast web browsing) Really, it is your second problem I'm more interested in. I haven't got a logitech mouse myself, but most of the drivers you need for almost any imaginable hardware are ususlly already included in Ubuntu. I have never heard of anyone needing to manually install any special mouse driver. (Not that I can recall anyway). I was wondering what protocol your mouse in running under in your Ubuntu system?
There are three main mouse protocols that I know of, and Ubuntu offers me two with my hardware. I don't know for sure what other people are able to use in Ubuntu.
These two mouse protocols available to me are,  
**ImPS/2 Protocol** If you have a Wheel Mouse, it usually uses the “ImPS/2&#8243; protocol. [COLOR=#000000][B]
ExplorerPS/2 Protocol [/B][/COLOR]for mice with a mouse wheel that you can use for scrolling up, scrolling down and also push in, so it functions as an extra button.  
My computers all use the [COLOR=#000000]**ExplorerPS/2 Protocol**[/COLOR]

By your symptoms, it sounds like your system is using the simpler **PS/2 Protocol ** for an old model of mouse with no mouse-wheel, just two buttons, but it is modern enough to use a *[PS/2 connector]("http://en.wikipedia.org/wiki/PS/2_connector"),  *(introduced back in 1987). Some laptop touchpads also have only two buttons.
   The PS/2 mouse communicates movements, and the state of each button, by means  of 3-byte packets.
Would your computer happen to be a laptop and you installed Ubuntu in it, and then plugged you mouse in later on maybe? 

In any case, to check what mouse protocol your system is running, use the following code, ```
cat /etc/X11/xorg.conf
``` If you look around on that file, you should see what mouse protocol your system has set up. If you want to change it, you can either edit the file manually, or run the sudo dpkg-reconfigure xserver-xorg command to have all your hardware re-detected and set up all over again.
Probably you can just edit the file if you only have one small change to make. be sure to make a backup of it first for safety.
If you need to know more details, please feel welcome to ask.
Regards, Herman :D

1st EDIT, I just re-read your post one more time and I think maybe you mean configuring you middle mouse button (sroll wheel) to automatically take you back one web-page. I don't know about that, all I do is right click and click 'back' at the top of the right-click menu. Try that for now, that's almost as quick. There's a 'forward' and even a 'reload' function very close by there as well.  You will probably be able to do your Web browsing even faster with Ubuntu when you get used to it. Best thing, no malware or adware or viruses! :D

2nd EDIT, [Automatix for Dapper and Breezy]("http://www.ubuntuforums.org/showthread.php?t=177646&highlight=automatix")
We don't just download 'installers' like in Windows. Ubuntu is much more advanced. You need to install stuff by special methods, always with a 'sudo' prefix to a command. 'Automatix makes installing most of the popular add-on software in Ubuntu simpler for most new users, and even experienced users. Probablt that will install all you want and more. You don't have to accept all of it though, I recommend installing only the programs what you recognize and understand. :D

---

