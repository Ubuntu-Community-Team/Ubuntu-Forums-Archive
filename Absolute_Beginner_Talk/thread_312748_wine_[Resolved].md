---
title: "wine [Resolved]"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by TheOtherLinuxFreak on 2006-12-04
i installed xubuntu edgy 6.10 on my computer and i downloaded wine. i opened the pakage and it says "Error: Dependency is not satisfiable:libartsc0" can any one help?:confused: :confused: 

Thanks!!

---

### Post by nickburns on 2006-12-04
go to a terminal (Applications >> Accessories) and type:

sudo apt-get install wine

and it will install it for you with the dependencies...

---

### Post by aysiu on 2006-12-04
Yeah, use the package manager instead:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by aysiu on 2006-12-04
> **nickburns said:**
> go to a terminal (Applications >> Accessories) and type:

sudo apt-get install wine

and it will install it for you with the dependencies...
You have to enable extra repositories before you can do that:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by TheOtherLinuxFreak on 2006-12-04
it said package wine not available. i have the pakage manager but when i went file -> add download packages when i browsed for the file, installation file showed up but it was grayed out and it didnt let me open it!!

thanksfor the quick reply!

---

### Post by aysiu on 2006-12-04
> **TheOtherLinuxFreak said:**
> it said package wine not available. i have the pakage manager but when i went file -> add download packages when i browsed for the file, installation file showed up but it was grayed out and it didnt let me open it!!

thanksfor the quick reply!
As I pointed out in the last post, you need to enable extra repositories before you can install Wine with the package manager.

---

### Post by TheOtherLinuxFreak on 2006-12-04
> **aysiu said:**
> As I pointed out in the last post, you need to enable extra repositories before you can install Wine with the package manager.
i did that adn it didnt work.. ill try again though

---

### Post by aysiu on 2006-12-04
> **TheOtherLinuxFreak said:**
> i did that adn it didnt work.. ill try again though
Can you post the output of these terminal commands? ```
cat /etc/apt/sources.list
sudo aptitude update
sudo aptitude install wine
```

---

### Post by TheOtherLinuxFreak on 2006-12-04
im not connected to the internet on my pc. im using my aunt's laptop right now. my pc is connecting to the internet when i type in the middle command.

---

### Post by aysiu on 2006-12-04
> **TheOtherLinuxFreak said:**
> im not connected to the internet on my pc. im using my aunt's laptop right now. my pc is connecting to the internet when i type in the middle command.
Ah. That makes things a little more complicated.

Not having an internet connection makes software installation complicated. Do you have another computer that *is* connected to the internet and that's not using wireless or dial-up?

---

### Post by TheOtherLinuxFreak on 2006-12-04
> **aysiu said:**
> Ah. That makes things a little more complicated.

Not having an internet connection makes software installation complicated. Do you have another computer that *is* connected to the internet and that's not using wireless or dial-up?
yes that s how i downloaded wine in the first place. it windows xp

---

### Post by aysiu on 2006-12-04
> **TheOtherLinuxFreak said:**
> yes that s how i downloaded wine in the first place. it windows xp
Okay. Well, this is going to be a bit convoluted, but--as I said before--not having an internet connection make software installation complicated.

Download [this file](http://archive.ubuntu.com/ubuntu/pool/universe/w/wine/wine_0.9.9-0ubuntu2_i386.deb) on your networked computer. Then move it to the desktop folder of your non-networked Xubuntu and paste these commands into the terminal: ```
cd Desktop
sudo dpkg -i *.deb
```

---

### Post by Linux Lover on 2006-12-05
The thing is not more complicated. You are not connected with the wine cvs repository. Open the /etc/apt/sources.list file with your favourite text editor,

Then add the following line at the end of the file,
```
deb http://wine.sourceforge.net/apt/ binary/

```
Be sure to hit a carriage return at the end of the file.

Then give the following command,
```
sudo aptitude update
sudo aptitude install wine
```

I think you can now become successful to install wine.

---

### Post by aysiu on 2006-12-05
I think you're missing somehow that TheOtherLinuxFreak doesn't have an internet connection on the Xubuntu computer. Adding an online repository won't help.

---

### Post by TheOtherLinuxFreak on 2006-12-05
ill try that then! if this doesent work then mabe i could connect it 2 the internet geyt the file

---

### Post by TheOtherLinuxFreak on 2006-12-05
ok now i got it innstallled! i installed a very small game and it works except that the graphics r very slow. is this normal? i installed the same game when the pc had windows and it worked fine. also installing office 2000 didnt work. thats all i tried. it workes good but its ultra slow! does anyone no whats wrong or is it normal.:-k 

thanks for all your help!!

---

### Post by aysiu on 2006-12-05
Please understand that Wine is a hack.

You're trying to run a Windows-native program on a non-Windows operating system. If it functions normally, that's a miracle. That said, in theory, Wine shouldn't run the program any more slowly than normal, since Wine isn't an emulator.

Maybe the game requires some kind of hardware acceleration in your video card? I don't know much about games, so I can't tell you what's up. Maybe post a new thread about your game?

---

