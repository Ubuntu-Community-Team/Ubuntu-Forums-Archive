---
title: "Realtek audio drivers idk how to install them, =("
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by jake16424 on 2007-08-13
ok, i download them, then i unpack them, then they sit there,, what do i click on , or ask to run?

these are the drivers.
Linux(kernel version 2.2.14 or 2.4)

this is the web page, (scroll to the bottom)

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=23&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false#AC]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=23&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false#AC")

i just don't know what todo with them after i unpack them, =(](*,)

---

### Post by iver2435 on 2007-08-13
I just downloaded and extracted the drivers you were talking about and there is a readme.txt file with extensive installation instructions.

According to the readme file, you can set the execute bit on the "install" file and then run that, like so:

```
chmod +x install
sudo ./install
```

That should get you going.

---

### Post by jake16424 on 2007-08-13
> **iver2435 said:**
> I just downloaded and extracted the drivers you were talking about and there is a readme.txt file with extensive installation instructions.

According to the readme file, you can set the execute bit on the "install" file and then run that, like so:

```
chmod +x install
sudo ./install
```

That should get you going.

tyou know,, i read that to,, haha,, :D... but, i entered the command, and nothing happened exect, it said file or directory invalid.. =-\

---

### Post by schorsch on 2007-08-13
> **jake16424 said:**
> 
Linux(kernel version 2.2.14 or 2.4)


.... I guess you are running kernel 2.6.x, so I doubt these drivers will work anyway ...

---

### Post by iver2435 on 2007-08-13
You have to run those commands from inside the directory where the "install" file is, just so you know.

Did you attempt the manual installation at all?

---

### Post by iver2435 on 2007-08-13
> **schorsch said:**
> .... I guess you are running kernel 2.6.x, so I doubt these drivers will work anyway ...

Wow, I totally missed that.....good eyes....

---

### Post by RomeReactor on 2007-08-13
Hi jake. Still no luck with the drivers?

---

### Post by dreadlord_chris on 2007-08-13
> **jake16424 said:**
> tyou know,, i read that to,, haha,, :D... but, i entered the command, and nothing happened exect, it said file or directory invalid.. =-\
if it said that then you entered the command wrong:
it should be **./** not **.\**

---

### Post by jake16424 on 2007-08-13
nope, i dont know how to manually install, i clicked the file that said Install.something, and nothing happened, a splash screen said, something about warning its a exicutable, and then, run or run in terminal, i tried both, nothing happened

---

### Post by RomeReactor on 2007-08-13
I'm surprised no-one with the same soundchip as you has offered you a solution, though from what I could find, it seems a tricky card to get going. Have you tried posting in the [Multimedia & Video]("http://ubuntuforums.org/forumdisplay.php?f=138") section also?
You could also try asking in the #ubuntu IRC channel.

---

### Post by jake16424 on 2007-08-13
will do , thank you :)

---

### Post by jephrandall on 2007-08-13
I'm not sure if Jake is still reading this thread, but the Realtek onboard audio chip works with Feisty out of the box (I have it, works great.  Even the front panel connectors work).  Have you upgraded to Feisty?  If not, why not try that?

---

### Post by jake16424 on 2007-08-13
> **jephrandall said:**
> I'm not sure if Jake is still reading this thread, but the Realtek onboard audio chip works with Feisty out of the box (I have it, works great.  Even the front panel connectors work).  Have you upgraded to Feisty?  If not, why not try that?

i did upgrade to feisty, still no audio, =(

---

### Post by jake16424 on 2007-08-13
might have something todo with my Green audio port doesn't work, even in XP my mobo came with it all staticy, and that was that.. i had to use the drivers to reconfigure the output .

---

### Post by diatribe on 2007-08-13
n/m

---

