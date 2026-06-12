---
title: "Installing a file"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by Stuperfied on 2006-04-14
I just downloaded the armyops250linux.run file from filefront but I dont know how to install it. I tried clicking on it but it tried to open it in text editor. I tried openning it in shell but it said it was a bad command. Can anyone tell me how to install it please?

---

### Post by Ensnared on 2006-04-14
Chances are it's not executable by default, which means you can run it by doing either this:
```
sh ./armyops250linux.run
```
Or this:
```
chmod +x armyops250linux.run
./armyops250linux.run
```

The first one will simply execute a shell which will then execute the file, which in turn makes it run.
The second will first make the file executable, then run it.

Both of these needs to be executed from the command-line in the same directory as the file is located. Otherwise you need to supply the full path to the filename rather than just putting "./" in front of it, which is simply a way of pointing to the current directory.

If you're the pure GUI-kind you could probably also right-click the file and open it's properties, then set the "execute" permissions on it, then double-click it afterwards.

---

### Post by Stuperfied on 2006-04-15
Thanks, I finally got it to install but it kept coming up with these errors because it couldnt change file permissions of the files it was creating so maybe I need to sudo it.

---

### Post by Stuperfied on 2006-04-15
I was thinking, instead of openning bash in addition to Gnome, is it possible to boot directly into bash without loading Gnome? I dont know if this game would run soely in bash but it does require a lot of resources, freeing up the resources taken by the windowning system would probably help a lot. Is there any way to do it in Ubuntu?

---

### Post by Ensnared on 2006-04-15
Games usually require an X-session to run, but it's possible to launch them in their own X-session without needing to have Gnome or any other desktop or Window Manager running. I doubt you'll notice any significant performance increase if you run it this way though, but yes, it is possible.

What you can do is simply turn off gdm (Gnome Display Manager - this is what provides a graphical login. Unless you use KDE, in which case you might be using KDM instead). This is done like so:
```
sudo /etc/init.d/gdm stop
```
Or if you're using KDM:
```
sudo /etc/init.d/kdm stop
```

Doing this will end your current X-session, so you will have to log in on the console. Then, create a script to launch your games. You can put this in a directory in your path, for instance /usr/local/bin. Name it anything you want - let's say we call it "rungame". Just create it with this command:
```
sudo nano -w /usr/local/bin/rungame
```
This will open the file in nano, which is a straight forward simple to use text-editor. In this file, you put the following:
```
#!/bin/sh
X :0 -ac -br &
export DISPLAY="localhost:0"
sleep 1
su <your_username_here> -c $*
sleep 1
kill `cat /tmp/.X0-lock`
```

Obviously you have to replace <your_username_here> with the username you normally log in with. Save and exit by hitting ctrl-x, then y, and then enter. Next, make the script executable by doing the following:
```
sudo chmod +x /usr/local/bin/rungame
```

Now, you can run your game by issuing the following command:
```
sudo rungame /path/to/game/mygame
```

The script needs to be run with sudo since it requires root privileges to start the X-server, but the "su <your_username_here>" line makes the game itself run as the user you usually log in with.

Now, I haven't actually tested this, but it should work. But as I said, I doubt you'll notice any significant performance increase by doing it this way.

---

### Post by Stuperfied on 2006-04-15
384
It worked but you were right, not much of a performance increase. I am using Gnome and once I closed it I couldnt find out how to open it again so I had to use the shutdown command (could have used restart but wanted to free any memory frag's).

I have an AMD Duron 995Mhz running at 1000Mhz with 384MB SD Ram, onboard 64MB Graphics (*variable and I did try 64MB but set at 8MB shared currently) and a 7200 RPM Drive. The game I mentioned (Americas Army 2.5.0) runs but I get heaps of mouse lag because of how slow its running, is there any way I can tweak Ubuntu into letting it run at normal speed or is it a hardware problem?

---

### Post by trent dillman on 2006-04-15
I'd say hardware, onboard gfx suck for gaming...

---

### Post by Stuperfied on 2006-04-16
The mouse lags in the menu and the menu is not graphics intensive at all so I do not believe it to be a graphics problem, maybe a ram problem, any ideas for freeing up more ram for it or possibly for getting the game to use actual ram and let other programs use page file?

---

### Post by Virtuous on 2006-04-16
If your mouse lags a little in the menu sections, then you might want to look at your hardware. I have that same problem with some pc games I run on a different OS. I'm kind of iffy with trying games on linux since I keep hearing about Cedega and don't want to pay a fee. But for starters you might want to look at your video graphics card. Maybe the driver needs to be updated. Sometimes that works. Good luck.:)

---

