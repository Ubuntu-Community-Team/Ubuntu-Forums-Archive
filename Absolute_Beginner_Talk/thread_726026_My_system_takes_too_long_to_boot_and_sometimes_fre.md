---
title: "My system takes too long to boot and sometimes freezes"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by endtheembargo on 2008-03-16
I've installed ubuntu v. 7.1 on my Toshiba Satellite A135, and for some reason it takes 3 whole minutes to boot (I timed it)!

It gets past the part that says GRUB loading stage 1.5, and then, it sits at a black screen for three minutes before the Ubuntu loading graphic comes up.

Once Ubuntu loads for the most part everything runs fine but every once in a while the computer will freeze and and need to be restarted. (I think this mostly happens while I'm in firefox.)

I'm wondering if this is a software or hardware issue. The computer came to me used with windows vista on it, and at that time I don't remember it having any problem booting up.

I'm sorry if this is a little vague, I' still learning about computers. Let me know if I need to get more specific about anything.
__________________

---

### Post by Diabolis on 2008-03-16
First we need to know in which stage of the booting process is hanging. When grubs appears, select your operating system and press **e** then select the line that say kernel and press **e** at the end erase **splash** and then press esc so you can boot up. Doing that will disable the ubuntu splash screen and you'll be able to see what is taking so long to get done while booting.

---

### Post by endtheembargo on 2008-03-16
I followed your instructions exactly, I erased splash, an then escaped out. But when I selected my operating system, it booted up the same as before, taking three minutes.

---

### Post by Diabolis on 2008-03-16
Oh! I'm really sorry, my bad. If you press esc, changes aren't saved so after you edit the kernel line press _**enter**_ and then in order to reboot press _**b**_. Then you'll see what the pc is doing while booting.

---

### Post by jakupl on 2008-03-16
here is what I did.

```
$ sudo gedit /etc/usplash.conf
```

Change from 1280 x 1024 to 1024x768

```
$ sudo update-usplash-theme usplash-theme-ubuntu
```

---

### Post by Diabolis on 2008-03-16
The problem doesn't have to deal with the splash screen, we are just removing it temporarily so we can see which process are consuming so much time.

---

### Post by jakupl on 2008-03-16
ok. but nevertheless, try it :popcorn:

---

### Post by ugm6hr on 2008-03-16
> **jakupl said:**
> here is what I did.

```
$ sudo gedit /etc/usplash.conf
```

Change from 1280 x 1024 to 1024x768

```
$ sudo update-usplash-theme usplash-theme-ubuntu
```

Indeed.  This is the most likely issue with the 3 minute boot:
[http://ubuntuforums.org/showthread.php?t=581075](http://ubuntuforums.org/showthread.php?t=581075)

Just pick the correct resolution.

As for the Firefox freezing problem, is it when you are viewing Flash video?

---

### Post by Diabolis on 2008-03-16
ah! good to know.

---

### Post by endtheembargo on 2008-03-16
Success Success!!!!!!! I changed the usplash settings and it booted up like MAGIC!! Thanks everyone for the patience and quick responses.

Now for the freezing problem. I can't remember whether it was while using flash or not. What might be a couple of scenarios?

---

### Post by jakupl on 2008-03-16
dont forget the "thank" button ;)

---

### Post by ugm6hr on 2008-03-16
> **endtheembargo said:**
> Now for the freezing problem. I can't remember whether it was while using flash or not. What might be a couple of scenarios?

Honestly, I don't know for certain.

But Flash did cause a few freezes on Firefox in Gutsy.

Mine seems to have fixed itself with the latest updates.

Try this:
```
sudo apt-get purge flashplugin-nonfree && sudo apt-get install flashplugin-nonfree
```

Ref: [http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

---

### Post by endtheembargo on 2008-03-16
Ok, I put the code in, and it asked if I wanted to install the updates/plug-ins, I said yes, and it looked like it was going to do it.

Then, at the end it says:
[I]Resolving fpdownload.macromedia.com... failed: Name or service not known.
download failed
The Flash plugin is NOT installed.
[/I]

---

### Post by ugm6hr on 2008-03-16
> **endtheembargo said:**
> Ok, I put the code in, and it asked if I wanted to install the updates/plug-ins, I said yes, and it looked like it was going to do it.

Then, at the end it says:
[I]Resolving fpdownload.macromedia.com... failed: Name or service not known.
download failed
The Flash plugin is NOT installed.
[/I]

Have you got all the necessary repositories enabled?  Can't think of any other reason that wouldn't work.  Unless the Flash download was temporarily off-line.  Maybe try again tomorrow.

---

### Post by imperius69 on 2008-03-18
for flash this page resolved my problem

[http://tombuntu.com/index.php/2007/12/31/why-cant-ubuntu-install-adobe-flash-player-anymore/](http://tombuntu.com/index.php/2007/12/31/why-cant-ubuntu-install-adobe-flash-player-anymore/)

installed like a charmed and is working

for the long boot time, i have the same problem, editing the file usplash did not resolved my problem, only way i could resolve was removing totally the quiet splash from menu.lst

if i remove only splash, still toooo long, if i remove both, ugly start up but a loooooot faster

any more ideas? :confused:

btw, im totally newb on linux, this is my first attempt on it, been reading the forums only.

My machine, acer aspire 1604LC P4 2.8GHz, 1GHz Ram, Ati Mobility Radeon 9000

---

### Post by imperius69 on 2008-03-18
did what was said in earlier page again, and now starts fine, go figure :D

thanks a lot for the fix :)

---

