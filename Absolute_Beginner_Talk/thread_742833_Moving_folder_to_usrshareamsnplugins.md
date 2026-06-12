---
title: "Moving folder to /usr/share/amsn/plugins"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by Snitz on 2008-04-02
I just downloaded a plugin for Amsn and it's on my desktop, I'm trying to move it in the above directory but it's saying I don't have permissions.

Is there any specific way?

---

### Post by kellemes on 2008-04-02
Run nautilus with the correct privileges..
From terminal..

```
gksudo nautilus
```

---

### Post by Snitz on 2008-04-02
I launched it in the terminal but it opened the desktop folder with no permissions of whatsoever :\

---

### Post by kellemes on 2008-04-02
> **Snitz said:**
> I launched it in the terminal but it opened the desktop folder with no permissions of whatsoever :\

don't forget the "gksudo"
It should ask for your password..

---

### Post by Snitz on 2008-04-02
It's not asking for a password, it's loading the desktop folder automatically.

---

### Post by kellemes on 2008-04-02
> **Snitz said:**
> It's not asking for a password, it's loading the desktop folder automatically.

probably because you've used sudo recently?
Meaning you still have privileges..

Are you sure nautilus isn't started with root privileges?
Have you tried moving the folder to it's destination?

---

### Post by Snitz on 2008-04-02
I've tried moving the folder but the same error over and over again.
Now when I launch nautilus in the terminal it's loading: /home/slevin/

---

### Post by kellemes on 2008-04-02
> **Snitz said:**
> I've tried moving the folder but the same error over and over again.
Now when I launch nautilus in the terminal it's loading: /home/slevin/

Strange..
Can you try the following please?

```
gksu nautilus
```

---

### Post by Snitz on 2008-04-02
How can I not be the owner of my desktop?
I right clicked the plugins folder and this is what it says

[[IMG]http://img176.imageshack.us/img176/9620/screenshotun2.th.png[/IMG]](http://img176.imageshack.us/my.php?image=screenshotun2.png)

---

### Post by Snitz on 2008-04-02
> **kellemes said:**
> Strange..
Can you try the following please?

```
gksu nautilus
```

Still the same, here have a look

[[IMG]http://img526.imageshack.us/img526/2691/screenshot1pb2.th.png[/IMG]](http://img526.imageshack.us/my.php?image=screenshot1pb2.png)

---

### Post by kellemes on 2008-04-02
I guess Nautilus is opened with root-privileges since you're in the root folder.

---

### Post by Snitz on 2008-04-02
Ok, how do I proceed? :S

---

### Post by taavikko on 2008-04-02
You can always use command line to move the folder.

```
sudo mv -r amsnplugin/ /usr/share/amsn/plugins/
``` 
where amsnplugin is name of the folder

And if im not mistaken, amsn has hidden folder in home directory, which also includes plugin folder.

You only need to move it to /usr/share folder if you have multiple users in your computer and everybody wants access to those plugins.

---

### Post by Snitz on 2008-04-02
I'm getting the following error

> slevin@slevin-laptop:~$ sudo mv -r music/ /usr/share/amsn/plugins/
[sudo] password for slevin:
mv: invalid option -- r
Try `mv --help' for more information.


---

### Post by sayakb on 2008-04-02
Try changing the write permissions:
```
sudo chmod 777 /usr/share/amsn/plugins
```
And then copy it..

---

### Post by kellemes on 2008-04-02
From terminal..
```
sudo mv FROMFOLDER TOFOLDER
```
(-r not needed)

From nautilus it's just a matter of browsing to your Desktop, this is /home/slevin/Desktop and copy/move the folder or files to the destination..

---

### Post by Snitz on 2008-04-02
> **LinuxIsInnovation said:**
> Try changing the write permissions:
```
sudo chmod 777 /usr/share/amsn/plugins
```
And then copy it..
That worked, can I CHMOD the whole filesystem?

---

### Post by sayakb on 2008-04-02
No, you shouldn't. That maybe because you might harm your system by providing write permissions to root files. Your system may become vulnerable to all sort of security threats.

---

### Post by Snitz on 2008-04-02
Thanks alot guys, I appreciarte the help!

---

### Post by Snitz on 2008-04-02
Oh ****, I don't know what I have done.

I made the following command in the terminal

```
sudo CHMOD 666 /
```

And now I can't enter the desktop environment, how can I fix this?

---

### Post by sayakb on 2008-04-02
If  you typed CHMOD in uppercase, don't worry, nothing has happened :)  
For information on chmod, read here: [http://www.ss64.com/bash/chmod.html](http://www.ss64.com/bash/chmod.html)  
EDIT: Did you add the last line just now?? Anyway, try this via recovery mode 
```
sudo chmod 0755 /
```Other UF members please re-check what I posted.

---

### Post by Snitz on 2008-04-02
Then what the hell happened? Why can't I enter Ubuntu anymore?

---

### Post by sayakb on 2008-04-02
> **Snitz said:**
> Then what the hell happened? Why can't I enter Ubuntu anymore?

chmod 666 would give read and write permissions to root folders to all users/groups.

---

### Post by kellemes on 2008-04-02
> **Snitz said:**
> Then what the hell happened? Why can't I enter Ubuntu anymore?

Well, you know what you did..

Unless you don't mind the occasional reinstall or struggle to get things going, never use command lines when you don't know what they're doing.

Anyway, I'd go for a reinstall.

---

