---
title: "wireless help"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by Greenbean209 on 2008-04-19
I finaly after a long series of waits, failed cd burning, and fruitless instalation attempts i finaly got through and installed ubuntu gutsy. so far the only thing ive changed is the screen resolution so i have a blank slate right now. my problem is that i have a wirless usb adapter that wont connect. model is a netgear WG111v2. it uses a 64 bit WEP code.
ive clicked the icon on the top of the screen to connect but when i put in the code it is still not connected. let me say again that i havent change any internet settings so is there something i have to do first?

---

### Post by natirips on 2008-04-19
Try restarting your wireless driver several times```
sudo modprobe -r drivername
sudo modprobe drivername
```I'm not sure if the second line is even necessary at all. You can find out what your drivername is by right clicking on your network icon and clicking the most obvious option (I have no idea how to translate the text from my localized version to english, sorry, but I believe you'll find it right away).

Edit: It won't necessarily fix your problem, although it fixed my problem whenever my card won't connect to my WLAN network (acctually, these are exceptional situations when it does on it's own XD)

---

### Post by Greenbean209 on 2008-04-19
Well let me explain a little more.. what happens is when i try to connect to my net work is it tries to connect but in the end all that happens is the little network icon just turns back to having the little _/!\_ symbol and it doesnt give me a message that it failed or anything. o yah and also i need a little help with command lines, ive used MS-DOS before but im not familiar with linux commands =( so im not sure exactly sure how to use that code

---

### Post by Vadi on 2008-04-19
I don't know what is the driver name that the OP has, nor I doubt the OP knows it even. So telling them to restart it is a bit useless :/

@ Greenbean209: the default network manager in 7.10 does have issue with certain networks. Here's what you can do - either upgrade to 8.04, which is already a "release canditate" and will be out in a week. The network manager there sports better connectivity, and a guide on upgrading can be found here ([click]("https://help.ubuntu.com/community/HardyUpgrades?highlight=(hardy)")).

Or, you can try WICD - it's a different network manager that works in a lot of cases where the default one doesn't: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by natirips on 2008-04-19
> **Vadi said:**
> I don't know what is the driver name that the OP has, nor I doubt the OP knows it even. So telling them to restart it is a bit useless :/
I had EXACTLY the same symptoms on my network,> it tries to connect but in the end all that happens is the little network icon just turns back to having the little /!\ symbol and it doesnt give me a message that it failed or anything And as weird as it sounds, but restarting my driver (ndiswrapper in my case) acctually works for reason I can not explain myself, it just works.:) I found the cure accidentally after desperately trying to set up my network for weeks...

Edit: "It works" for _me_.

---

### Post by Greenbean209 on 2008-04-19
i am just gonna say that the /!\ symbol is acualy a symptom of not being connected so that doesn't mean it's the same prob. Also are u talking about a card because im using usb.

---

### Post by natirips on 2008-04-19
Sorry, but that's all I have. Like I said in my original post, it wasn't a sure kill for the problem ("It won't necessarily fix your problem..."). I would tell you better if I knew better... (why do I have this feeling I did something wrong to you? I'm 100% sure that those two sudo lines were apsolutely harmless.)

---

### Post by Greenbean209 on 2008-04-19
no no no... i havent used the lines anyways because i wasnt sure how to any way like i said in my first reply I've used MS-DOS but im not familiar with linux commands so i could use some help with that

---

### Post by Vadi on 2008-04-19
What he meant is that you should go to Applications - Accessories - Terminal, and paste this in there:

> sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper

If that doesn't work though (doubt it will), look at my post.

---

### Post by Greenbean209 on 2008-04-19
> **Vadi said:**
>  upgrade to 8.04, which is already a "release canditate" and will be out in a week. The network manager there sports better connectivity, and a guide on upgrading can be found here ([click]("https://help.ubuntu.com/community/HardyUpgrades?highlight=(hardy)")).

Or, you can try WICD - it's a different network manager that works in a lot of cases where the default one doesn't: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Seriously Hardy Heron is gonna be released as a stable distro next week?!

oh and i looked a the WICD link but i wasn't sure how to get the files it said i needed download.

---

### Post by natirips on 2008-04-19
I'd like to be of any use to you so (now that you know how to open your terminal/console) here's a little MS-DOS : Unix/Linux comparison:
MS-DOS      Unix-Linux
dir           ls
cd            cd
mkdir       mkdir
rmdir      rmdir     or   rm -r
del        rm
copy     cp
renmove (I think it was)    mv
attrib        chmod
type        cat
edit        nano  /    pico


Also try typing "help" in your console. Try "man command_name" for more info on a specific command. Press Q key to quit the MANual.
Also, ~ (tilde) is abbreviation for your HOME directory (it has both the role of My Documents and Documents And Settings/username folders from Windows.
"sudo" before a command lets you use that command as a root (administrator).
You can also run a command by adding a little & sign after it (ie. "gedit &") to run a program in background and be able to use console while the program is runnig. Notice that such program might close together with the console itself.


On ubuntu, you can also see all the connected media (cdroms, etc) in your "/media" dir. (on some Linux distros it's "/mnt").
Your "/" directory (root) is what "C:\" would be on MS-DOS.
"/usr" if like Program files.
"/etc" is like c:\windows or c:\dos dir (I think, I'n not 100% sure).
Your boot loader is likely installed into "/boot" dir.
"/home" is like C:\documents and settings.

If you used windows, you might like these shortcuts as well:
ALT+F2 is "Run..."
ALT+F1 is like the Windows logo key in windows.
For more shortcuts and their customisation see System -> Settings -> Keyboard Shortcuts (I think, because my Ubuntu is not in english, at least the GUI).

Edit: Also notice the diffrence between slash "/" (unix/linux) and backslash "\" (dos).
And offcourse, there is a much better version of autocomplete than that in dos/windows, (use tabulator key once or twice while typing some long filenames or commands to see what I'm talking about).

---

### Post by Vadi on 2008-04-19
Installing Wicd in Ubuntu

Installing Wicd in Ubuntu is very simple. You just have to add the Wicd repository to the Ubuntu package manager. To open the package manager in Gnome, go to Administration > Synaptic Package Manager. When it appears, go to Settings > Repositories > Third Party Software > Add..., and enter the following line:

    deb [http://apt.wicd.net](http://apt.wicd.net) gutsy extras 

where gutsy is your version of Ubuntu in lowercase (dapper, edgy, feisty, gutsy, hardy). Then, click Reload, and wait while the package lists are downloaded. Now, search for "Wicd", and right click on it. Select Install, then press Apply, and Wicd will automatically be downloaded and installed for you. This will also keep you automatically up to date with the latest and greatest version of Wicd. Please note that this will remove network-manager, which is the default GNOME network manager and may cause loss of network connection temporarily.

In GNOME, to get the tray icon to automatically appear at boot, go to System > Preferences > Sessions. In the "Startup Programs" tab, click the "New" button. Give it a name ("Wicd" works fine). For the command, enter "/opt/wicd/tray.py".

---

### Post by Greenbean209 on 2008-04-19
oh wait so that means im gonna have to be online to do that right? because thats kinda like "a hole in the bucket" if you know what i mean:-k

---

### Post by sennep on 2008-04-20
> **Greenbean209 said:**
> oh wait so that means im gonna have to be online to do that right? because thats kinda like "a hole in the bucket" if you know what i mean:-k

lol, "a whole in the bucket" indeed:)

There are probably .deb files (they're like setup files) of wicd you can download on a different computer and just use a cd or floppy or something to get it to the ubuntu box. Once they are on the ubuntu computer, simply doubleclick on them to install. have a look at wicd's sourceforge site, they migh have some there:
[http://sourceforge.net/project/showfiles.php?group_id=194573](http://sourceforge.net/project/showfiles.php?group_id=194573)

As for this particular adapter, the wg111v2, well it's a bit tricky, I have one myself and I have been able to make it work with ndiswrapper (a program that makes you able to use windows drivers in ubuntu). I wrote a guide on how I did it, and it seems to work for some people, but not for everybody, you can give it a try if you want, it's a link to it in my signature.

---

