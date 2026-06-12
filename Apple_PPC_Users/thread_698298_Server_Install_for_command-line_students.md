---
title: "Server Install for command-line students"
date: 2008-02-16
forum: Apple PPC Users
---

### Post by stream303 on 2008-02-16
Want to really learn the command line at your own pace?

I just performed a painless server install on an external firewire drive since I found myself getting too distracted by the gui on my main drive.

Despite your best efforts to get ubuntu/kubuntu/xubuntu/fluxbuntu whatever installed on your G3, and maybe found it just too slow for today's graphical world, think about making it a cli-only box.  Nothing can make you learn faster than by not having any gui options whatsoever.

Ok, so I'm not going to use it for mail, spreadsheets, etc and leave that to my G5.  However, I hate seeing good hardware go to waste.

**How to install the server in a few minutes:**

I chose the FEISTY 7.04 server, which can be found here:

[http://cdimage.ubuntu.com/ports/releases/7.04/release/](http://cdimage.ubuntu.com/ports/releases/7.04/release/)

It is similar to doing the "alternate" install, and all I did was UNselect the option to make any servers like DNS or LAMP when that prompt came up.

Upon reboot, I wanted to make sure it was updated:
```
[B]
sudo apt-get update[/B]
```

then

```
**sudo apt-get upgrade**
```

Doesn't get much easier than that.  Repeat these two commands every so often when you feel like being updated with the latest.

If you are a newcomer to the command-line, it can be a bit frightening to be rewarded with nothing but a shell prompt.  Let's install a small utility called HTOP that I like that is in color and makes a nice addition to the "top" command:
```
[B]
sudo apt-get install htop[/B]
```

Want to see a listing of the files in your present directory with trailing slashes so that you can quickly discern directories (if you aren't into the color thing):  (uppercase -F)
```
**ls -F**
```

Want to keep a bit organized as you study/play around?  Use the virtual terminals!  CTRL-ALT-F2 for another login.  CTRL-ALT-F3 if you need another. and so on.

Anyway, I could keep going forever, but just wanted to point out that a CLI-only box can be a lot of fun if you aren't distracted by a gui (leave that on your other box), and take the right attitude and not try to learn it all in a day.  I suppose this thread could go into another forum, but just wanted to make sure that no good Mac hardware ends up being junked prematurely.

If you want to reboot:
```
[B]
sudo shutdown -r now[/B]
```

If you want to shutdown completely:
```
**sudo shutdown -h now**
```

---

### Post by bodycoach2 on 2008-02-16
This is an excellent idea for people studying for Linux+ or LPI exams.

---

### Post by stream303 on 2008-02-16
I was in such a rush to get to the desktop that I just blindly banged out commands and once there realized that I didn't have any solid background at the command prompt.

My most expensive mistake was when I thought that going commercial would make things easier, so when the farthest I could get graphically with Yggdrasil Linux was showing ls in color, I bought a two-license seat of SCO OpenServer for my 386.  For $500.  No compilers, no tcp/ip, barely anything.  That hurt, and not just financially.  I went running back to Linux with open arms. :)

I just started by learning how to cd around the filesystem, pwd to see where I am in this Linux filesystem cave, (learning that cd with no parameters will take you home), used less, more, cat to look at files, and eventually learned a little vi.  Sure wish I had nano back then - even though I dig vi today.

I crashed the system a lot before I learned the shutdown command!  Nothing was journaled, so I did a lot of reinstalls. :)

After awhile, instead of just typing commands, it becomes natural like a language.  It just flows from your fingers without thinking like riding a bike.

---

