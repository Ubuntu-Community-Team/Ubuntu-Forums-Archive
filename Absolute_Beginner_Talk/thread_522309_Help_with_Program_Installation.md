---
title: "Help with Program Installation"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-08-10
I want to completely switch and force myself to learn Ubuntu.
There are several programs that I have that are proprietary to
windows so I am going to try some native Linux alternatives.

I have a Police Scanner that I use often and it came with
some software that only runs in windows. Well I found a
replacement that someone has written to work in Linux.

Would someone take a look at this and tell me how easy this would be
to install. Also, could you show me how to install it. 

If it could be installed this may help some other users that use Scanners.  
From what I could find, this is the only one I know of that runs in Linux.

This is the Website:
[http://home.comcast.net/~kilowattradio/files/](http://home.comcast.net/~kilowattradio/files/)

Currently, I am using Virtual Box to run Ubuntu
and every time I start Wine, it bogs everything
down. I think running an emulator in an emulator
really taxes the machine. From what I have been
told, this program can't be installed in WINE so
I don't think that would be an option anyway.

I'd love to learn if my original windows Program
would run in WINE but I think it may be to much
for the machine.

---

### Post by Ek0nomik on 2007-08-10
You can always use Wine to see if it will install the program.  If it doesn't work (gives you errors or just won't run after installation), no harm done.  You can simply remove the files and be done with it.  So, it's worth a shot.

From the link you provided, the website provides you with the source, so all you need to do is compile it to install it.  They also state it has been tested on Ubuntu, so it will probably install just fine.

If you need help compiling, there are a lot of resources out there that explain how to do it, and the steps to take.  Otherwise you can post on the forum if you can't find your answer elsewhere.

---

### Post by SOULRiDER on 2007-08-10
Running that program is really easy, dont worry!

First you need to install the dependencies:
```
sudo aptitude install install tcl tk tcllib bwidget
```

Now that you have all necesary programs to run it, you need to actually run it :P
In a terminal, go tot he directory containing the program and type:
```
./startlinux.sh
```

If it gives you an error saying you dont ahhve permissions type:
```
sudo chmod +x startlinux.sh
``` and try again, it should work correctly.

If you want you can see if the windows program runs on wine by checking:
[http://appdb.winehq.org/](http://appdb.winehq.org/)
Good luck!

---

### Post by Hospadar on 2007-08-10
It looks like this program is super easy to run, just download the .tgz file ([http://home.comcast.net/~kilowattradio/files/bc246t-0.8d.tgz](http://home.comcast.net/~kilowattradio/files/bc246t-0.8d.tgz)), extract the folder in it, then cd to it in a terminal and run the start script (Applications->Accessories->Termina)

Lets say you extracted it to your desktop, in the terminal:
```
cd ~/Desktop/bc246t-0.8d
./startlinux.sh
```

Also, you could just go to that folder, double click on "startlinux.sh" and choose run.

---

### Post by Orbital75 on 2007-08-10
Thanks everyone.... Looks like it's pretty simple

I'm kinda new at linux so I'm learning as I go.
I like to keep a tight clean OS's is there a place
in Linux ( Ubuntu ) like Program Files where
all the applications are keep.  Would I create
a folder somewhere and throw all the files
in there then place that folder in a certain location
in linux?

Just want to have a place where I know where everything
is.

(Edit) Hummmmm just tried it and got this

Reading Package List.....Done
Building Dependency tree......
Reading State information...... Done
Package tcl is not available, but is referred to by another package
This may mean the package is missing, has been obsoleted, 
or is only available by another source. 
E: Package has no candidate source.

Any ideas?

---

### Post by Orbital75 on 2007-08-10
Got the program up and running.  What had happen is that the Package names
had been changed.

They are now:
tk8.4
tcl8.4
tcllib
bwidget

Thanks everyone for all the help and
If anyone has a Uniden bc246T Police Scanner, now you know how to install it.  :)
Now the trick will be finding out how to use it.

I ended up putting the bc246T-8.0d folder in /usr/lib
I'm thinking this is like Program Files in Windows.
Can someone tell me how I came set an Icon for
it and run it from Applications.  Thanks

[IMG]http://img528.imageshack.us/img528/4783/screenshotaf8.png[/IMG]

---

### Post by SOULRiDER on 2007-08-10
Im not sure about how GNOME behave sin ubuntu, but in my GNOME installation you can right click it and select Edit Menus. After that you just click new item and youre all set. For the command, youll have to add the full path to the launcher which is startlinux.sh. So if you copied it to /lib/usr/ the command should look like:

```
/usr/lib/bc246t-0.8d/startlinux.sh
```

I would suggest putting that directory in your Home folder though.

---

### Post by Orbital75 on 2007-08-10
I started a new post on the Launcher..... thanks for answering though.

---

### Post by kolinab on 2007-11-28
Did you get this software working to your satisfaction? Inquiring minds want to know. I'm thinking getting the scanner you describe and was excited to find there are Linux control options for it . . . if they work!

K

[edit] Nov 29. OK, got it installed and everything OK. I don't have a serial port on my laptop so I'll have to learn to use my USB to serial adapter I guess. I'll post back with problems in a couple of weeks! No time for all this now . . .

[edit again] Great, followed the instructions on the website, and it works great! Now if I could only figure out how to work it :)

---

### Post by hyper_ch on 2007-11-28
> **Orbital75 said:**
> so I'm learning as I go.

I guess that's how most of us learn... you want to do something... you encounter a problem... you try to solve it ;)

Regarding the menu entry, maybe you need to install "a la carte" first (or something like that).

---

