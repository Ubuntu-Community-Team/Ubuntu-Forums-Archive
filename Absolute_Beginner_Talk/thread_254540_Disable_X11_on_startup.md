---
title: "Disable X11 on startup"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by Abstract on 2006-09-10
Hey, I was wondering if it is possible to make it so on startup XWindows is disabled, but I can login and start it using:
```
xstart
```

Any ideas?

---

### Post by steve.horsley on 2006-09-10
There are two easy-ish ways to do this. The command-line way is to use the command:
**sudo rm /etc/rc2.d/S13gdm**
and to make it work at startup again is:
**sudo ln -s /etc/rc2.d/S13gdm /etc/init.d/gdm**

The graphical way is to install the package **bum** and then use it (System->Administration->Boot Up Manager)to disable the service **gdm**. Ironically, you cannot use the normal services dialog (System->Administration->Services) to disable gdm, because as you click to stop gdm, it stops and the GUI dies before it gets a chance to save its settings.

P.S.
it's **startx** and not **xstart**.

---

### Post by bodhi.zazen on 2006-09-10
I suggest you disable start scripts rather then deleting them.

Since Linux is case sensitive this is easy:

To disable:
```
sudo mv /etc/rc2.d/S13gdm /etc/rc2.d/s13gdm
```
To Enable:
```
sudo mv /etc/rc2.d/s13gdm /etc/rc2.d/S13gdm
```
This way I do not need to remember
[list]
[*]What start scripts I disabled
[*]Start order of said scripts
[*]Where was that link to ?.
[/list]
After booting to cli:
[list]
[*]To start gdm: sudo gdm
[*]You know startx
[/list]

---

### Post by steve.horsley on 2006-09-10
Yup. Good plan. I'll go along with thtat.

---

### Post by LadyDoor on 2006-09-10
Actually, there's an elegant way to do this with the **update-rc.d** command. To remove:

```
sudo update-rc.d -f gdm remove
```

And if for some weird reason you ever want it back...

```
sudo update-rc.d -f gdm defaults
```

And here's a link to a thread that will give you a nice ASCII art issue before you log in. [http://www.ubuntuforums.org/showthread.php?t=39572&highlight=spice+boot+text](http://www.ubuntuforums.org/showthread.php?t=39572&highlight=spice+boot+text)

Enjoy!

--Door

---

### Post by LadyDoor on 2006-09-10
Actually, there's an elegant way to do this with the **update-rc.d** command. To remove:

```
sudo update-rc.d -f gdm remove
```

And if for some weird reason you ever want it back...

```
sudo update-rc.d -f gdm defaults
```

And here's a link to a thread that will give you a nice ASCII art issue before you log in. [http://www.ubuntuforums.org/showthread.php?t=39572&highlight=spice+boot+text](http://www.ubuntuforums.org/showthread.php?t=39572&highlight=spice+boot+text)

Enjoy!

--Door

P.S.:  Please search before posting. These instructions already exist on the forums--that's how I found them originally a while back--by searching.

P.P.S.:  If you plan to use a CLI or even a terminal, you might be interested in checking out GNU screen! If you already know of it, this part isn't for you but for some person who hasn't who might be reading this post.

---

### Post by LadyDoor on 2006-09-10
Sorry to double-post. I thought hitting stop in my browser would stop it from posting the first time--but I was deceived.

---

### Post by mugabemkomo on 2007-12-13
Hi, I was trying the same thing, but run into some problems:

First of all, the font is really crappy i cant really see anything at all, i have to type "blind". Is there a way to install another font on the shell login for example?

and the next problem is, when I log on and use startx i cant really run any administrive programs, like set services for example. I always end up with an error message and no "enter password window" like usual!

Thx for advice

---

