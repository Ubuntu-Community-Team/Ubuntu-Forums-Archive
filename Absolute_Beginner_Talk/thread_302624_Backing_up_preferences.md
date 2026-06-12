---
title: "Backing up preferences"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by redbluemangle on 2006-11-18
ok, hypothetical situation...

You've screwed up your ubuntu install so badly you can't even log into failsafe. All you can do it mount your filesystem and a 2nd HDD from the liveCD to backup files. If you wanted to backup my Gnome layout where would you look?

---

### Post by turbojugend_gr on 2006-11-18
ACtually just keeping your home unformated, and re-install should do all the tricks (all prefs kept, wanted or not...)

If you only wish to keep some of them, safer way is to keep your home, after deleting all the hidden folders for prefs you wish to spare.  (.strating_ones in your home)

---

### Post by redbluemangle on 2006-11-18
wait, I can do a repair type installation?

---

### Post by turbojugend_gr on 2006-11-18
If what you mean is you loose all stuff installed via synatpic, apt-get etc, but keep all your prefs, yup you can, anytime, just install again ubuntu leaving /home untouched, like I suggested, is this still hypothetical, cause if it's not then I should post some how to's for better following.

You will just need to install the apps, (codecs maybe) again, but the prefs will remain there, so it is not like you missed anything (just some time w8ing).

---

### Post by Papa-san on 2006-11-18
:D I think I'd like to see a how to... LOL

This sounds like something I will need before too long!

---

### Post by aysiu on 2006-11-18
> **Papa-san said:**
> :D I think I'd like to see a how to... LOL

This sounds like something I will need before too long!
Here's one:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by redbluemangle on 2006-11-18
yea, its not hypothetical :P I was trying to save face. Here's my dillema:

I set my desktop to /home/user instead of /home/user/desktop
and I mounted my fat32 partition(my big file storage one) to /home/user BUT I messed up and mounted it to /home

Everything stopped working, i couldn't even launch a terminal.](*,) 
So i boot from the live CD and I mounted my installed filesystem and fixed my fstab so the fat32 drive was mounted to /home/user which didn't help at all. I boot up and I couldn't even log in I was prompted with this :

User's $HOME/.dmrc file is being ignored, this prevents default session and language from being saved, File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by any other users. 

Then I would get another message i forgot to write down about how the session lasted less than 10 seconds and listed a few erros from /etc

I guess reinstalling is the way to go :-k

---

### Post by aysiu on 2006-11-18
I would back up these folders (/home/user = ~/):

~/.gnome
~/.gnome2
~/.gconf
~/.gconfd
~/.nautilus
~/.metacity
~/.icons
~/.themes

And if you're using Firefox and Evolution, these too:
~/.mozilla
~/.thunderbird

Those are all hidden directories, by the way.

---

### Post by jordanmthomas on 2006-11-18
You can probably fix your problem!
Press Ctrl-Alt-F2

If you can log in as your user, then try this:
```
sudo chmod 644 ~/.dmrc 
```
Then, hit Ctrl-Alt-F7 and try logging in again.

---

### Post by turbojugend_gr on 2006-11-18
LOL, here's the deal, Corfu is an Island in Greece, if you can explain how on earth it's in new york too, then I will.... ;)

The real deal, I will make it short, you will do all things I say:

1. Decide which app's prefs you don't wish to keep, you go in your home folder and delete that apps config folder (usually it is like ~/.APP_NAME).

2. You insert the ubuntu disk, you follow installing procedures, as you normally should, you just make sure /home is **not** to be formatted, all others should be (exept those you wouldn't format anyway ofcourse, like multimedia partitions, winxp partitions, backup partitions etc)

3. You are done, your system looks like it did, all the apps you wanted to be as they should are, you have one that still messes you up maybe, you do not blame me for that, I told you to get rid if it ;).

4. You install codecs, apps (yup those that are missing now, but when you install them they are just like they never left the building (or tower maybe ;))

5. You call your windoz pall, and make fun of his 200 DVDs of backupping every time his favorite app crack, made him to reformat.

I hope you understand it's too simple, so I needed to make it look like a tought hack, so I look great... hehe 8).

---

### Post by redbluemangle on 2006-11-18
> **aysiu said:**
> I would back up these folders (/home/user = ~/):

~/.gnome
~/.gnome2
~/.gconf
~/.gconfd
~/.nautilus
~/.metacity
~/.icons
~/.themes

And if you're using Firefox and Evolution, these too:
~/.mozilla
~/.thunderbird

Those are all hidden directories, by the way.

coooool I have those backed up :D

---

### Post by aysiu on 2006-11-18
Sorry. I was on crack. Evolution is in ~/.evolution

I use Thunderbird, so I put ~/.thunderbird

By the way, you may want to try some of those tricks to change the permissions and ownership on ~/.dmrc

---

### Post by redbluemangle on 2006-11-18
ok I just tried the trick with ~/.dmrc and it said no such file existed. So I think I've basically deleted my home directory altogether. There is an error log. i've attached it.

---

### Post by jordanmthomas on 2006-11-18
You may lose some settings but you could just delete ~/.gnome2_private
```
sudo rm -r ~/.gnome2_private
```
Chances are, though, that a lot more than that is wrong.

What I would do instead of a reinstall, personally, is make a new user
```
sudo adduser newuser
sudo adduser newuser admin # so you can use sudo with newuser

```
Then, I would log on as them and recover whatever files from the old user I wanted.  Probably not the best thing, but better than a reinstall.

---

### Post by turbojugend_gr on 2006-11-19
> **jordanmthomas said:**
> You may lose some settings but you could just delete ~/.gnome2_private
```
sudo rm ~/.gnome2_private
```
Chances are, though, that a lot more than that is wrong.

What I would do instead of a reinstall, personally, is make a new user
```
sudo adduser newuser
sudo adduser newuser admin # so you can use sudo with newuser

```
Then, I would log on as them and recover whatever files from the old user I wanted.  Probably not the best thing, but better than a reinstall.

I totally agree, keeping your home is mostly useful, when upgrading or messed up with the system itself (root stuff in other words), when adding a new user is no good, I posted while the situation was still "hypothetical" and non-issue-specific (--> see what shyness ca do... ;) - post your issues, no one will judge you here).

Best Regards, TJ.

---

