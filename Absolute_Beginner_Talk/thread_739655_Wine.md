---
title: "Wine"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by Dedaw on 2008-03-29
What is it? How does it work? How do I use it?

Any help appreciated :D

---

### Post by scragar on 2008-03-29
install, then just right click any .exe file, and select properties, then set "open with" to wine. from then on just double click any exe to run it in wine, no further problems.

---

### Post by Dedaw on 2008-03-29
Where do I install it from? Is it in Linux?

Sorry for being such a noob :( I just installed Ubuntu maybe 20 minutes ago...

---

### Post by scragar on 2008-03-29
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) <-- make sure you have universe enabled

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware) <-- install wine

not hard, with the universe option enabled from a terminal you can just run:
```
sudo apt-get update && sudpo apt-get install wine
```if you don't feel like using synaptic.

---

### Post by iSplicer on 2008-03-29
Scragar, you made a mistake mate =)

Run this from Accessories -> Terminal

```
sudo apt-get update && sudo apt-get install wine
```

---

### Post by alexforcefive on 2008-03-29
wine is not an emulator ;) but it is fairly comparable to one. It allows you to run windows applications from inside linux. You can install it from Applications > Add/Remove, but first check if the program you want to run will actually work with wine at: [http://appdb.winehq.org/](http://appdb.winehq.org/)

Also, remember that (apart from games), almost any windows program you could want already has a free native linux counterpart

---

### Post by chewearn on 2008-03-29
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by linuxbeatswin on 2008-03-29
I've used Ubuntu for a while, and just installed Wine. I am trying to get my wife's windoze based cd-rom to work, and was able to install it, but when I right-clicked the exe file to run the program, I got this error message: 

EAccessViolation in module CompRev4.exe at 00000000
AccessViolation at address 00000000 in module 'CompRev4.exe'.
Read of address 00000000

What does this mean, and how do I fix it? My wife really needs this to work, and I have been looking at forums for the past two hours trying to figure this thing out before I bothered you nice folks about it,. Any help you can give is greatly appreciated.

Thank you!

---

### Post by iSplicer on 2008-03-29
Oh and before I forget, welcome to Ubuntu Dedaw! If you have any concerns or questions whatsoever, we are there to help you! Never forget that I too was once using Ubuntu 20 minutes after first touching linux

I agree with alex, you should use wine as an absolute last resort. It is extremely buggy and doesnt work most of the time. There has to be a program that is native to linux, what is it that you are trying to run?

Good Luck!

---

### Post by Dedaw on 2008-03-29
Ok... I feel really retarded. This still makes no sense, and I have no clue what a terminal is. Is it like command prompt?

---

### Post by iSplicer on 2008-03-29
> **linuxbeatswin said:**
> I've used Ubuntu for a while, and just installed Wine. I am trying to get my wife's windoze based cd-rom to work, and was able to install it, but when I right-clicked the exe file to run the program, I got this error message: 

EAccessViolation in module CompRev4.exe at 00000000
AccessViolation at address 00000000 in module 'CompRev4.exe'.
Read of address 00000000

What does this mean, and how do I fix it? My wife really needs this to work, and I have been looking at forums for the past two hours trying to figure this thing out before I bothered you nice folks about it,. Any help you can give is greatly appreciated.

Thank you!

Please do not hijack this thread, make your own one with all the details you can provide, including what you are trying to run, and we can help you =)

---

### Post by scragar on 2008-03-29
it is the command propt, Applications > accessories > terminal


@ iSplicer - sorry, thanks for noticing that, caught p by mistake :P

---

### Post by Laser Dude on 2008-03-29
Wine is, to quote their website "an Open Source implementation of the Windows API".  In simpler terms, it lets you run Windows programs without actually having Windows.  Their homepage is here: [http://www.winehq.org/](http://www.winehq.org/)

To install Wine, open your package manager, usually under System > Administration > Synaptic Package Manager and searching for "wine".  Click the checkbox next to it, and click apply at the top.  This should cause any .exe files you click to be run with Wine, however if they don't, then you can right-click and "run with Wine".

However, don't depend on Wine.  Don't expect it to run your programs perfectly, or even at all.  Wine is still in beta, and it is recomended that you don't use it unless you absolutely have to (like for a game).  If you're not sure whether something will run under Wine, check their AppDB: [http://appdb.winehq.org/](http://appdb.winehq.org/)

I know you're excited to find that you can run Windows programs under Wine, although like the rest of us, you'll probably realise that it's not as important as you thought.  As you start using Linux/Ubuntu more and more, you'll realise that there are many alternatives to the Windows programs you're used to, most of which are actually better than the Windows program that performs a similar function.

---

### Post by Dedaw on 2008-03-29
> **iSplicer said:**
> Oh and before I forget, welcome to Ubuntu Dedaw! If you have any concerns or questions whatsoever, we are there to help you! Never forget that I too was once using Ubuntu 20 minutes after first touching linux

I agree with alex, you should use wine as an absolute last resort. It is extremely buggy and doesnt work most of the time. There has to be a program that is native to linux, what is it that you are trying to run?

Good Luck!
Thank you :)
I've already made up my mind to ditch Windows altogether :)

And I'm looking to us Photoshop. And yes, I do know that there is GIMP, but it isn't nearly the same as Photoshop.

---

### Post by iSplicer on 2008-03-29
> **Dedaw said:**
> Ok... I feel really retarded. This still makes no sense, and I have no clue what a terminal is. Is it like command prompt?

Dont feel retarded, I too was once asking what a terminal was. 

A terminal is the linux version of command prompt, albeit much more powerful. We use it to execute a lot of commands and run programs

The command I gave you is to install wine. So open the terminal by going to 

Applications -> Accessories -> Terminal and type in the command I gave you.

If you need any further help, please ask!

---

### Post by linuxbeatswin on 2008-03-29
> **iSplicer said:**
> Please do not hijack this thread, make your own one with all the details you can provide, including what you are trying to run, and we can help you =)

My sincerest apologies. I've been up for quite a while, and my manners "flew the coop", so to say. Again, please forgive the momentary lapse of coolness.

---

### Post by iSplicer on 2008-03-29
> **Dedaw said:**
> Thank you :)
I've already made up my mind to ditch Windows altogether :)

And I'm looking to us Photoshop. And yes, I do know that there is GIMP, but it isn't nearly the same as Photoshop.

Well, it is my sad duty to advise you that if you plan on using photoshop past version 7.0, you will be disappointed. It doesnt run in wine, unfortunately.

The only thing you can do (what I am doing) is to install virtualbox, and install XP inside the virtual machine which is running in linux. You can then run PS as normal

PS is basically the only program that doesnt have a good alternative and cant be wined. I cant think of anything else ATM

---

### Post by Dedaw on 2008-03-29
So... before CS2?

And thank you guys so much for the help :)
It's really cool to have such a helpful community. :D

EDIT: Just saw that it works up to CS2, which is perfect :D

---

### Post by iSplicer on 2008-03-29
> **Dedaw said:**
> So... before CS2?

And thank you guys so much for the help :)
It's really cool to have such a helpful community. :D

CS2 does not work, I've heard. As I said, virtualbox/vmware/dualboot is the only way to include PS in your computer.

Are you familiar with Virtual Machines, dedaw?

---

### Post by Dedaw on 2008-03-29
> **iSplicer said:**
> CS2 does not work, I've heard. As I said, virtualbox/vmware/dualboot is the only way to include PS in your computer.

Are you familiar with Virtual Machines, dedaw?
Not at all sadly :(

---

### Post by Dedaw on 2008-03-29
Hmmm... One thing I don't like. The differences between the two resolutions. It's either really small or big,bigger,and biggest. No in between?

---

### Post by iSplicer on 2008-03-29
> **Dedaw said:**
> Not at all sadly :(

It isnt hard at all to understand; a virtual machine is a program that runs under linux, which simulates another computer, so you are able to run a windows INSIDE a program in linux. This screenshot should explain everything:
[IMG]http://www.llaumgui.com/public/images/linux/virtualbox/virtualbox_vista.png[/IMG]

Notice how that guy is running Vista INSIDE ubuntu! You can do the same thing,  by installing virtualbox and installing windows inside it. Then you can use PS as normal!

---

### Post by Laser Dude on 2008-03-29
According to the app DB, the last test of Photoshop CS2 received a platinum rating.  According to the page, you need to install the times32 font, and there's apparantly a few random bugs.  Otherwise it seems OK.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2631](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2631)

---

### Post by iSplicer on 2008-03-29
Also, dedaw, have a read of this:

[http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux](http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux)

---

### Post by Dedaw on 2008-03-29
So, do I have to have XP installed on my system? Because I'm looking to toss that P.O.S ;)

---

### Post by alexforcefive on 2008-03-30
You could try GIMPshop, which is a version of gimp which is layed out to work the same as photoshop. I don't use it so I can't personally recommend it, but it seems ok: [http://www.gimpshop.com/](http://www.gimpshop.com/)

---

### Post by bbharatsony on 2008-03-30
Terminal is like Command Promt. Terminal is avalible in Applications>Accessories>Terminal

---

### Post by linuxbeatswin on 2008-03-30
> **alexforcefive said:**
> You could try GIMPshop, which is a version of gimp which is layed out to work the same as photoshop. I don't use it so I can't personally recommend it, but it seems ok: [http://www.gimpshop.com/](http://www.gimpshop.com/)

A fellow employee uses GIMPshop as well as photoshop, and he uses GIMP more often, saying that its layout is nicer, it's faster, and is more user friendly. I don't use it personally, but he really likes it. 

Just my two cents... :)

---

### Post by Laser Dude on 2008-03-30
> **Dedaw said:**
> So, do I have to have XP installed on my system? Because I'm looking to toss that P.O.S ;)

If you use Wine, no.  It's essentially a free version of Windows.  Windows is not required.

A virtual machine is basically a computer simulator which runs within your OS.  Using a virtual machine, you would install Windows on that virtual machine, and whenever you turn on the virtual machine, Windows starts up.  It looks like the screenshot posted above.  The advantages to using a virtual machine are that your applications are garunteed to work exactly as they would in Windows (because they are running in Windows).  Disadvantages are that running an entire operating system can take up a lot of system resources, and you need to specify a separate partition and some memory to work with your OS.  It will not integrate with your Linux.

The AppDB has given Photoshop in Wine some good reviews, and it is one of the apps which is targetted to be working perfectly by the 1.0 release (sometime in the summer).  I'd suggest that you try it in Wine, if it does satisfy you, excellent!  If not, then you can either dual boot or run a virtual machine to use photoshop.  Or, you could try this Gimpshop which people have mentioned.  In any of the last two cases, I'd suggest that every month or so you give Photoshop a shot in Wine (after updating of course).  That way if it ever does work, then you can ditch either your Windows or Gimpshop, and start using photoshop within Linux.

---

### Post by Michl on 2008-03-30
> **Dedaw said:**
> So, do I have to have XP installed on my system? Because I'm looking to toss that P.O.S ;)

No.  One nice thing is that you can configure wine so that in Applications -> Wine ->
Configure Wine you can set it so that Applications run under different Windows
OS emulations.  For example, AUtocad 2000 runs under W2k but not under XP
while other programs dont run under W2k.  So you can configure that.

Also, you can install updates, drivers, service packs and so on simply by
downloading the .exe (typically) and running them with the Wine emulator.
Just right click, choose to run with the emulator and your program is updated.

I have only tried Autocad 2000 and Fritz7, and both run smoothly under Wine.

Autocad, tax prohrams and music productoin (Reason)
are to my mind the only programs that you need to use windoze applications.

---

