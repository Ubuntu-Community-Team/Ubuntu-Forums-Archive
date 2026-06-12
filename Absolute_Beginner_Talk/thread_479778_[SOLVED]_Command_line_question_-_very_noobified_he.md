---
title: "[SOLVED] Command line question - very noobified help needed"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by crjackson on 2007-06-20
I have ubuntu A64 installed, I purchased Acronis True Image Server - Linux - I've looked over the directions and don't understand them at all.

My install is setup.sfx - I click it and of course it does nothing.

The quick start guide looks like this.

1) login as root (or su)
2) ensure that setup.sfx has wxecutable flag (chmod +x)
3) ./setup.sfx
4) follow program instructions when prompted

NOTE: If an error occurs due to kernelmod: dkms build -m snapapi26 -v 0.7.0 --arch i686 --kernelsourcedir <sourcedir>

[SIZE="4"]**Obviously I don't have a clue as to what I'm doing here.  Could someone be kind enough to walk me through this.**[/SIZE]

---

### Post by Happy_Man on 2007-06-20
Right, open up a terminal. Then, do this:
```
sudo -i
cd <directory this setup file is in>
chmod +x setup.sfx
./setup.sfx
```

And you should be OK from there.

---

### Post by Golyadkin on 2007-06-20
Okay, this is going to be quite simple. Put the file you downloaded (setup.sfx) in your home directory.
Then click "Applications" in the top left of the screen, then point to Accessories and chose "Terminal". That should open up the commandline for you in a new window.

Type these commands, and finish each line by pressing [Enter].

> 
sudo chmod +x setup.sfx

sudo ./setup.sfx


---

### Post by crjackson on 2007-06-20
> **Happy_Man said:**
> Right, open up a terminal. Then, do this:
```
sudo -i
cd <directory this setup file is in>
chmod +x setup.sfx
./setup.sfx
```

And you should be OK from there.

You guys are great - I'm at work right now but I can't wait to get home and try this.  Thanks a bunch...:D

---

### Post by Golyadkin on 2007-06-20
You are welcome :) good luck, I am sure it will work out fine. Let us know if you need any more help.

---

### Post by crjackson on 2007-06-22
> **Golyadkin said:**
> You are welcome :) good luck, I am sure it will work out fine. Let us know if you need any more help.

That launched me into the graphical installer perfectly, I input my serial number, it's accepted, then I get an error that it can't install and I forget the error code (I'm at work tonight).

I guess I'll have to go through the SLOW process of getting Acronis help (turst me, I've owned every version of Acronis TI now, and THEY ARE SLOW TO HELP).

I hate to say it, but I CAN boot into XP and make quick backups of my ubuntu drive.  I just hate HAVING to boot into XP for this.

**Does anyone know of a good reference book I can pick up that will explain what the basic Linux commans are?  For instance what does "./" mean?  Run perhaps?**

I know that su means SuperUser but what is the DO in sudo?  Just basic stuff like that.

---

### Post by Happy_Man on 2007-06-22
> **crjackson said:**
> That launched me into the graphical installer perfectly, I input my serial number, it's accepted, then I get an error that it can't install and I forget the error code (I'm at work tonight).

I guess I'll have to go through the SLOW process of getting Acronis help (turst me, I've owned every version of Acronis TI now, and THEY ARE SLOW TO HELP).

I hate to say it, but I CAN boot into XP and make quick backups of my ubuntu drive.  I just hate HAVING to boot into XP for this.

**Does anyone know of a good reference book I can pick up that will explain what the basic Linux commans are?  For instance what does "./" mean?  Run perhaps?**

I know that su means SuperUser but what is the DO in sudo?  Just basic stuff like that.
I believe [http://linuxcommand.org](http://linuxcommand.org) will help you immensely.

---

### Post by crjackson on 2007-06-22
> **Happy_Man said:**
> I believe [http://linuxcommand.org](http://linuxcommand.org) will help you immensely.

Great Thanks! Reading it now...

---

### Post by crjackson on 2007-06-22
I still can't find the difference between su sudo...

---

### Post by Seisen on 2007-06-22
Su makes you as the root user and sudo just gives the user superuser priveleges for a certain amount of time or for a certain application.

---

### Post by Scheater5 on 2007-06-22
"sudo" and "su" are different ways of doing administrative tasks.  The "root" user is the linux equivalent to windows "administrator."  
Sudo is somewhat uniquely "Ubuntu."  It temporarily gives any user (well, any user in in the proper group - but that's another story) administrative privileges.  ie:
```
sudo aptitude update
```
will update your list of available programs (packages).  
"super user" is the somewhat more traditional method.  It's essentially doing commands as the root user.  in most distributions you merely enter "su -" (- is short for root) however in ubuntu use "sudo su -"

Only telling you this because it's likely not to be in linuxcommand.org.  It's somewhat confusing, I know.

---

### Post by crjackson on 2007-06-23
got it, thanks...

---

