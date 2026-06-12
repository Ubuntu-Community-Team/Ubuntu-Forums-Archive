---
title: "Azureus Updating itself"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by jtomoso on 2007-01-30
I installed azureus last night and the first time it ran it needed to updated itself.  After the updates were downloaded, though, they couldn't be run because the updater needed root access to overwrite some files.  How do I give the updater root privileges so that it can run correctly?

---

### Post by taurus on 2007-01-30
Where did you install azureus?  You just need to change that partition to your **username** so you can write to it.  That's all you need to do.

---

### Post by jtomoso on 2007-01-30
I'm not sure.  I installed it from the add/remove programs dialog.  I also didn't partition my drive at all, is that a problem?

---

### Post by taurus on 2007-01-30
```
locate azureus
```

---

### Post by jtomoso on 2007-01-30
I'll do that when I get home today and see what it tells me.

---

### Post by jtomoso on 2007-01-31
Azureus is installed in
[LIST]
[*]/opt/azureus
[*]"/usr/share/applications" for the azureus.desktop file
[/LIST]

---

### Post by jordanmthomas on 2007-01-31
```
sudo chown $USER /opt/azureus
```

---

### Post by jtomoso on 2007-01-31
That did it.  Thanks!

---

### Post by Phosphoric on 2007-02-01
> **jordanmthomas said:**
> ```
sudo chown $USER /opt/azureus
```

Hi, same problem.

is USER my username? or typed in just as it is?

Thanks. :)

---

### Post by Soarer on 2007-02-01
Just type it as it is. $USER is an environment variable which always contains... the current user.

Simple, but effective :)

---

### Post by Phosphoric on 2007-02-01
Thanks, I'll try it later. :D

---

### Post by navneeth on 2007-02-03
Okay one more person with the same problem.  I installed Azureus via Automatix, and this is what 'locate azureus' says:

```
/usr/share/app-install/desktop/azureus.desktop
/usr/share/automatix2/conf/azureus.desktop

```

Do I need to change sudo chown $USER /opt/azureus in any way?

Thanks.

---

### Post by jackrobinson on 2007-02-03
> **navneeth said:**
> Okay one more person with the same problem.  I installed Azureus via Automatix, and this is what 'locate azureus' says:

```
/usr/share/app-install/desktop/azureus.desktop
/usr/share/automatix2/conf/azureus.desktop

```

Do I need to change sudo chown $USER /opt/azureus in any way?

Thanks.

all you need to do is this:
```
sudo azureus
```
let azureus download and install the updates.
close it.
you are all set.

---

### Post by navneeth on 2007-02-03
> **jackrobinson said:**
> all you need to do is this:
```
sudo azureus
```
let azureus download and install the updates.
close it.
you are all set.

That's what it doesn't do. I installed it the app. yesterday, and as soon as I opened it for the first time, I got an alert that said there was an update available. I let it download, but it would not install. Here's the exact warning message:

> The location '/opt/azureus' isn't writable, this update will probably fail. Check permissions and rety[sic] the update

---

### Post by Perfect Storm on 2007-02-03
As it says you don't have permission to write there (security reasons). There is numerous way to handle this. One way is as described above (use that methode to only updating azureus, don't run azureus normally this way), the other way is to change permission of Azureus folder and then change it back when it have updated.

sudo chown -R username:username /opt/azureus/
sudo chown -R root:root /opt/azureus/

Another option is to download the binary for their homepage and run it all from your "home".

---

### Post by navneeth on 2007-02-03
sudo azureus doesn't work. I get a command not found. 

AI, I tried the code you provided, and that doesn't work, too! :(

I'll use your suggestion to download it from their site. 

Thanks for the help, guys.

---

### Post by Perfect Storm on 2007-02-03
Try this howto I wrote: [http://ubuntuforums.org/showthread.php?t=144546](http://ubuntuforums.org/showthread.php?t=144546)

---

### Post by navneeth on 2007-02-03
Edit: Never mind.

---

### Post by navneeth on 2007-02-03
AI, thank you. No probs while installing. I think just to test whether it works, an update for a plugin popped up while I opened it. :D The update was installed successfully after I opened it as root.

---

### Post by xhabitat4humanityx on 2007-02-03
I also had the problem of 2.5...not being able to work. 
This worked well: sudo chown $USER /opt/azureus

THANKS!

---

### Post by dedeaux on 2007-05-13
I know this is a dated thread.  However, I used this command:

```
sudo chown $USER /opt/azureus -R

```

Whether this solution is safe or not, it was necessary in order to get the plugins dir accessible.  I know, I could have JUST chown'd the plugins dir, but now its all chown'd to the specific user.

---

